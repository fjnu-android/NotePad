# NotePad

期中作业操作记录
1--添加显示时间
![image](https://github.com/fjnu-android/NotePad/blob/master/demo/1.png)
```
       String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE ,NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE} ;

       // The view IDs that will display the cursor columns, initialized to the TextView in
       // noteslist_item.xml
       int[] viewIDs = { android.R.id.text1 ,android.R.id.text2};
```     

在代码中，从数据库多读取一列时间COLUMN_NAME_MODIFICATION_DATE。从而显示文件处理时间。


2--按标题关键字查询
![image](https://github.com/fjnu-android/NotePad/blob/master/demo/2.png)
```  
  String where = "title LIKE '%"+keyWord.getText().toString()+"%'";
```  
通过添加where语句对数据库进行查询操作，使用LIKE进行模糊匹配。
  
3--更换背景颜色
![image](https://github.com/fjnu-android/NotePad/blob/master/demo/3.png)
```  
   mainBg.setBackgroundColor(Color.parseColor("#4169E1"));
```  
通过setBackgroundColor方法改变应用的背景颜色
    
4--笔记导出
![image](https://github.com/fjnu-android/NotePad/blob/master/demo/4.png)
![image](https://github.com/fjnu-android/NotePad/blob/master/demo/5.png)
```  
//设置文件路径
String filePath = Environment.getExternalStorageDirectory().getPath() + "/NotePad/ExportTxt/";
//保存文件
ToFile.writeTxtToFile(cursor.getString(colNoteIndex),filePath,cursor.getString(colTitleIndex));
```  
通过writeTxtToFile可以预先创建文件夹并且创建文件时将笔记中的标题以及文本信息写入txt格式的文件当中。
 注意： 
 ```        <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
 ```  
 需要在AndroidManifest.xml添加上述代码，应用才具有文件写入权限。
