
/*************************************************
 * AFW EXTERNAL API CONNECTOR
 *
 * Student Email -> Workspace Studio -> Gemini
 * -> NotebookLM policy answer -> Google Sheet queue
 * -> Apps Script -> Supabase student lookup
 * -> Telegram escalation -> Student email reply
 *************************************************/

/*************************************************
 * SUPABASE
 *************************************************/

function testSupabaseLookup() {
  const props = PropertiesService.getScriptProperties();
  const url = props.getProperty("SUPABASE_URL") +
    "/rest/v1/rpc/get_afw_student_record";
  const key = props.getProperty("SUPABASE_KEY");

  const response = UrlFetchApp.fetch(url, {
    method: "post",
    contentType: "application/json",
    headers: {
      apikey: key,
      Authorization: "Bearer " + key
    },
   
    payload: JSON.stringify({
      p_email: "programoffice@fiib.edu.in"
    }),
    muteHttpExceptions: true

  });

  Logger.log(response.getResponseCode());
  Logger.log(response.getContentText());
}

function lookupStudentByEmail(email) {
  const props = PropertiesService.getScriptProperties();
  const url = props.getProperty("SUPABASE_URL") +
    "/rest/v1/rpc/get_afw_student_record";
  const key = props.getProperty("SUPABASE_KEY");

  const response = UrlFetchApp.fetch(url, {
    method: "post",
    contentType: "application/json",
    headers: {
      apikey: key,
      Authorization: "Bearer " + key
    },
    payload: JSON.stringify({ p_email: email }),
    muteHttpExceptions: true
  });

  if (response.getResponseCode() !== 200) {
    throw new Error(
      "Supabase lookup failed: " +
      response.getResponseCode() + " " +
      response.getContentText()
    );
  }

  return JSON.parse(response.getContentText());
}

/*************************************************
 * GOOGLE SHEET QUEUE
 *************************************************/

function testReadPendingRows() {
  const props = PropertiesService.getScriptProperties();
  const sheetId = props.getProperty("SHEET_ID");
  const sheet = SpreadsheetApp.openById(sheetId)
    .getSheetByName("Sheet1");
  const rows = sheet.getDataRange().getValues();

  const pendingRows = rows.filter((row, index) =>
    index > 0 && row[6] === "PENDING"
  );

  Logger.log("Pending rows found: " + pendingRows.length);
}

/*************************************************
 * TELEGRAM
 *************************************************/

function getTelegramChatId() {
  const props = PropertiesService.getScriptProperties();
  const token = props.getProperty("TELEGRAM_BOT_TOKEN").trim();
  const url = "https://api.telegram.org/bot" +
    token + "/getUpdates";

  const response = UrlFetchApp.fetch(url, {
    muteHttpExceptions: true
  });

  Logger.log(response.getContentText());
}

function sendTelegramTest() {
  const props = PropertiesService.getScriptProperties();
  const token = props.getProperty("TELEGRAM_BOT_TOKEN").trim();
  const chatId = props.getProperty("TELEGRAM_CHAT_ID").trim();
  const url = "https://api.telegram.org/bot" +
    token + "/sendMessage";

  const payload = {
    chat_id: chatId,
    text: "AFW escalation bot is connected successfully."
  };

  const response = UrlFetchApp.fetch(url, {
    method: "post",
    contentType: "application/json",
    payload: JSON.stringify(payload),
    muteHttpExceptions: true
  });

  Logger.log(response.getResponseCode());
  Logger.log(response.getContentText());
}

function sendTelegramAlert(message) {
  const props = PropertiesService.getScriptProperties();
  const token = props.getProperty("TELEGRAM_BOT_TOKEN").trim();
  const chatId = props.getProperty("TELEGRAM_CHAT_ID").trim();
  const url = "https://api.telegram.org/bot" +
    token + "/sendMessage";

  const payload = {
    chat_id: chatId,
    text: message
  };

  const response = UrlFetchApp.fetch(url, {
    method: "post",
    contentType: "application/json",
    payload: JSON.stringify(payload),
    muteHttpExceptions: true
  });

  if (response.getResponseCode() !== 200) {
    throw new Error(
      "Telegram send failed: " +
      response.getResponseCode() + " " +
      response.getContentText()
    );
  }

  return JSON.parse(response.getContentText());
}

/*************************************************
 * STUDENT REPLY
 *************************************************/

function extractPolicyAnswer(policyText) {
  let text = String(policyText || "").trim();

  const match = text.match(
    /POLICY_ANSWER:\s*([\s\S]*?)(?=\n\s*STUDENT_RECORD_NEEDED:|\n\s*HUMAN_REVIEW_NEEDED:|\n\s*REASON:|$)/
  );

  if (match) text = match[1].trim();

  // Remove NotebookLM citation markers such as [1] or [1, 3].
  text = text.replace(/\s*\[\d+(?:\s*,\s*\d+)*\]/g, "");

  return text.trim();
}

function buildStudentReply(policyText, studentRecord, needsHumanReview) {
  const policyAnswer = extractPolicyAnswer(policyText);
  let recordText = "";

  if (studentRecord && studentRecord.found) {
    recordText =
      "\n\nYour available AFW record currently shows:\n" +
      "- Sessions attended: " +
      studentRecord.afw_sessions_attended + "\n" +
      "- Sessions missed: " +
      studentRecord.afw_sessions_missed + "\n" +
      "- Pending assessments: " +
      studentRecord.pending_assessments + "\n" +
      "- Evidence folder status: " +
      studentRecord.evidence_folder_status;
  }

  if (needsHumanReview) {
    return "Dear Student,\n\n" +
      policyAnswer + recordText +
      "\n\nYour request requires faculty review and has been escalated. " +
      "No exception, waiver, approval, reassessment, deadline extension, " +
      "or other special permission has been granted automatically. " +
      "You will receive a decision after faculty review.\n\n" +
      "Regards,\nAFW Course Team";
  }

  return "Dear Student,\n\n" +
    policyAnswer + recordText +
    "\n\nThis response is based on the AFW policy knowledge base " +
    "and the course record currently available to the system.\n\n" +
    "Regards,\nAFW Course Team";
}

function sendStudentReply(emailId, replyText) {
  if (!emailId) {
    throw new Error("No Gmail Email ID was provided.");
  }

  const message = GmailApp.getMessageById(String(emailId).trim());

  if (!message) {
    throw new Error("Could not find Gmail message: " + emailId);
  }

  message.reply(replyText);
}

/*************************************************
 * MAIN QUEUE PROCESSOR
 *
 * Sheet columns:
 * A - Received At
 * B - Student Email
 * C - Subject
 * D - Email Body
 * E - Gemini Analysis
 * F - Processing Status
 * G - Supabase Record
 * H - Telegram Status
 * I - Policy Answer
 * J - Email ID
 * K - Reply Status
 *************************************************/

function processLatestPendingRow() {
  const props = PropertiesService.getScriptProperties();
  const sheetId = props.getProperty("SHEET_ID");
  const sheet = SpreadsheetApp.openById(sheetId)
    .getSheetByName("Sheet1");
  const lastRow = sheet.getLastRow();

  // Start with the newest row and process one pending query per run.
  for (let row = lastRow; row >= 2; row--) {
    const status = sheet.getRange(row, 6).getValue();

    if (status !== "PENDING") continue;

    const email = sheet.getRange(row, 2).getValue();
    const subject = sheet.getRange(row, 3).getValue();
    const analysis = sheet.getRange(row, 5).getValue();
    const policyAnswer = sheet.getRange(row, 9).getValue();
    
    // Supabase lookup; write result to column G.
    const studentRecord = lookupStudentByEmail(email);
    sheet.getRange(row, 7).setValue(JSON.stringify(studentRecord));

    const needsHumanReview = String(analysis)
      .includes("NEEDS_HUMAN_REVIEW: YES");

    // Telegram escalation only when human review is required.
    if (needsHumanReview) {
      const existingTelegramStatus = sheet.getRange(row, 8).getValue();

      // Avoid duplicate alerts when retrying the row.
      if (existingTelegramStatus !== "ALERT SENT") {
        const telegramMessage =
          "🚨 AFW HUMAN REVIEW REQUIRED\n\n" +
          "Student: " + email + "\n" +
          "Subject: " + subject + "\n\n" +
          "Gemini Analysis:\n" + analysis + "\n\n" +
          "Student Record:\n" +
          JSON.stringify(studentRecord, null, 2);

        sendTelegramAlert(telegramMessage);
        sheet.getRange(row, 8).setValue("ALERT SENT");
      }
    } else {
      sheet.getRange(row, 8).setValue("NOT REQUIRED");
    }

    const replyText = buildStudentReply(
      policyAnswer,
      studentRecord,
      needsHumanReview
    );

    try {
      sendStudentReply(emailId, replyText);
      sheet.getRange(row, 11).setValue("REPLY SENT");
      sheet.getRange(row, 6).setValue("PROCESSED");
      Logger.log("Processed row " + row + " - reply sent.");
    } catch (error) {
      sheet.getRange(row, 11)
        .setValue("REPLY FAILED: " + error.message);
      sheet.getRange(row, 6).setValue("REPLY FAILED");
      Logger.log("Reply failed for row " + row + ": " + error.message);
      throw error;
    }

    return;
  }

  Logger.log("No pending rows found.");
}
