# Project BEVELON

Stack: HTML, CSS, JS

Made by Kihyeon KIM

// 구글 스크립트 API 수정 코드
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = e.parameter;
  
  // 현재 날짜 및 시간
  var now = new Date();
  var date = Utilities.formatDate(now, "GMT+9", "yyyy-MM-dd HH:mm:ss");
  
  // 시트에 데이터 추가 (HTML의 name 속성 순서와 맞추면 좋습니다)
  // 시트 1행에 순서대로 날짜, 회사명, 대표자, 연락처, 지역, 업종, 매출, 자금, 상황, 문의내용 을 적어두세요.
  sheet.appendRow([
    date, 
    data.company, 
    data.owner, 
    data.phone, 
    data.region, 
    data.biz_type, 
    data.sales, 
    data.fund, 
    data.status, 
    data.message
  ]);
  
  return ContentService.createTextOutput(JSON.stringify({"result":"success"}))
    .setMimeType(ContentService.MimeType.JSON);
}