before you can accsess this you need to first creat a google app script url of yours:
-Go to script.google.com
-Click New project
-clear all the code thats already in there and past this code;

function doPost(e) {
  const data = JSON.parse(e.postData.contents);
  
  const to = data.to;
  const subject = data.subject;
  const body = data.body;
  
  try {
    GmailApp.sendEmail(to, subject, body);
    return ContentService
      .createTextOutput(JSON.stringify({success: true}))
      .setMimeType(ContentService.MimeType.JSON);
  } catch(err) {
    return ContentService
      .createTextOutput(JSON.stringify({success: false, error: err.message}))
      .setMimeType(ContentService.MimeType.JSON);
  }
}


-------------------------------------------

-Click Save (Ctrl+S), give the project any name like "Email Sender"
-Click Deploy (top right) → New deployment
-Click the gear icon ⚙ next to "Select type" → choose Web app
-Set Execute as → Me
-Set Who has access → Anyone
-Click Deploy
-It'll ask you to authorize — click through and allow it
-Copy the Web app URL it gives you at the end




THAT IS YOUR Google Apps Script URL 
