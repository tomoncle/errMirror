##org.apache.poi.openxml4j.exceptions.InvalidOperationException: Can't open the specified file: 'C:\Users\Administrator\Desktop\1234.xlsx'
原因：new XSSFWorkbook(file) 不能读取2007以前版本的Excel，需要使用new HSSFWorkbook(new FileInputStream(file));

#

##java.io.IOException: Unable to read entire header; 0 bytes read; expected 512 bytes
原因：Excel文件创建有问题，需要打开*.xls 另存为*.xls 
