# GSheetsGoJiraf
sistema para validación de url´s

CODIGO FUENTE (script)
Hay un video del cual saque varias cosas donde explica paso a paso, se encuentra en el final la URL

  //constantes globales
  const ss=SpreadsheetApp.getActiveSpreadsheet()
  const formWS=ss.getSheetByName("Form")
  const settingsWS=ss.getSheetByName("Settings")
  const dataWS=ss.getSheetByName("Data")
  const idCell=formWS.getRange("A14:G14")
  const fieldRange=["B6:D6","F6","B9","D9","F9"]

  var desc=formWS.getRange("F9")
  var porc=formWS.getRange("D9")
  var precio=formWS.getRange("B9")
  var ext=formWS.getRange("F6")
  var url=formWS.getRange("B6:D6")

//funcion para guardar datos, se ejecuta con el boton del formulario
function gojirafSave() {
  const fieldValues=fieldRange.map(f=>formWS.getRange(f).getValue())
  const nextIdCell=settingsWS.getRange("A2")
  const nextId=nextIdCell.getValue()
  fieldValues.unshift(nextId)
  dataWS.appendRow(fieldValues)
  idCell.setValue(nextId)
  nextIdCell.setValue(nextId+1)
  clear()
}

//funcion para borrar las celdas de Form
function clear(){
  //fieldRange.forEach(f=>formWS.getRange(f).clear())
  
}

//Utilidades
//https://www.youtube.com/watch?v=ZKYvrD-3Ksc
