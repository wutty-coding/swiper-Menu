# swiper-Menu
load templat***************************
https://github.com/devmode-on/Card-Slider


**************รหัส GS************************
function setIMG() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('menu')
  var folder = DriveApp.getFolderById('xxxxx')
  var allFiles = folder.getFiles()
  var file
  while (allFiles.hasNext()) {
    file = allFiles.next()
    data = [
      file.getName(),
      "https://lh3.googleusercontent.com/d/" + file.getId(),
    ]
    sheet.appendRow(data)
  }
}
 
function doGet(){
  var template = HtmlService.createTemplateFromFile('index');
  template.data = getSheetData();
  var output = template.evaluate()
  .addMetaTag('viewport', 'width=device-width, initial-scale=1')
  .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL)
  return output;
 
}
 
 
function getSheetData(){
 return ss = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('menu').getDataRange().getDisplayValues().slice(1);
 
}
 


***************index.html****************

  <section class="swiper mySwiper">
<center><h4></h4></center>
    <div class="swiper-wrapper">
 <? data.forEach( row =>{ ?>
      <div class="card swiper-slide">
        <div class="card__image">
          <img src="<?!= row[1] ?>" alt="card image">
        </div>
        <div class="card__content">
          <span class="card__title" id="list1"><?!= row[0] ?></span>
          <a class="card__btn" href="<?!= row[2] ?>" target="_blank">คลิกเลือก</a>
        </div>
      </div>
   <? });?>
    </div>
  </section>

