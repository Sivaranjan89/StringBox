# StringBox

# Welcome to StringBox

###  You can manage all your database operations with this library. 
### Every information will be saved as Strings only. 
### This library can convert your images also to strings. 
### You can use the encryption options in StringBoxUtils to encrypt your data. 
### Check the below methods and enjoy using StringBox

# How to Install Plugin
Add the below in your root build.gradle(project) at the end of repositories:<br />
<b>allprojects { </b><br />
<b>repositories { </b><br />
<b>... </b><br />
<b>maven { url 'https://jitpack.io' } </b><br />
<b>} </b><br />
<b>} </b><br />
            
Add the dependency in build.gradle(module) : <br />
<b>dependencies { </b><br />
<b>implementation 'com.github.Sivaranjan89:stringbox:1.0'</b><br />
<b>}</b><br />


### Set your own Database name
StringBox.setDatabaseName(String name)
####This is optional. Even if your don't spcify a name, It will create a database with a default name.

### Create Database
StringBox.getInstance(this)

### Create Table
ArrayList< String > data = new ArrayList<>();</br>      
        data.add(COLUMN_NAME); </br>
        data.add(COLUMN_GENDER); </br>
        data.add(COLUMN_DOB); </br> 
        StringBox.getInstance(this).createTable(TABLE_NAME, data); </br>
#### The above code will create a table with 3 columns -> Name, Gender and DOB.


### Create Row
HashMap< String, String > map = new HashMap<>(); </br> 
        map.put(COLUMN_NAME, "Shiva"); </br>  
        map.put(COLUMN_GENDER, "Male"); </br>  
        map.put(COLUMN_DOB, "26/04/1989"); </br>  
        StringBox.getInstance(this).addRow(TABLE_NAME, map); </br>  
#### The above code will create one row in the table name specified. 
####Since the table has 3 columns, We specify in the hashmap as to which value belongs to which column.
####COLUMN_GENDER -> "Male" which will insert the value to the column GENDER for this row
  
 
### Get All rows from one Specific Column
ArrayList< String > names = StringBox.getInstance(this).getAllRowsFromColumn(TABLE_NAME, COLUMN_NAME); </br>
#### The above code will get all the rows from column "Name".
 

### Modify a specific row
HashMap< String, String > map = new HashMap<>();</br>
        map.put(COLUMN_NAME, "Shiva");</br>
        map.put(COLUMN_GENDER, "Male");</br>
        map.put(COLUMN_DOB, "26/04/1989");</br>
        StringBox.getInstance(this).modifyRow(TABLE_NAME, map, rowToModify);
#### The above code will modify the row specified with the new values provided in hashmap. 
#### rowToModify is an int variable which refers to a row position in the table. Ex: First row will be position 0


### Get the total rows count from a Table
StringBox.getInstance(this).getRowsCount(TABLE_NAME)
#### The above code will return the total rows count from the table name provided.


### Delete a Specific row from Table
StringBox.getInstance(this).deleteRow(TABLE_NAME, rowToDelete);
#### The above code will delete the row in the specified position. 
#### rowToDelete is an int variable which refers to a row position in the table. Ex: First row will be position 0


### Encrypt you String using AES
StringBoxUtils.encryptAES("myName", "Shiva");
#### The above code will encrypt the string "Shiva" using AES algorithim and return the encrypted string. 
#### This can later be decrypted using the password given which is "myName". The password value is your choice.


### Decrypt you String
StringBoxUtils.decryptAES("myName", encodedStr)
#### The above code will decrypt the encodedStr passed using the password and return the decrypted string.


### Encryption CHARSETS
#### If you wish to customize your encryption further, You can use the Charsets provided in StringBoxUtils as shown below,
StringBoxUtils.setEncryptionCharset(StringBoxUtils.CHARSET_UTF8); </br>
or </br>
StringBoxUtils.setEncryptionCharset(StringBoxUtils.CHARSET_UTF16);
#### You can customize your encoding charset using the above lines. UTF-8 or UTF-16


### Convert Image to String
StringBoxUtils.bitMapToString(bitmap) </br>
or </br>
StringBoxUtils.bitMapToString(drawable)
#### Use the above code to convert your images to Strings and save in database


### Convert Strings To Images
StringBoxUtils.bitmapFromString(bitmapString)</br>
or</br>
StringBoxUtils.drawableFromString(drawableString)</br>
#### Use the above code to retrieve the image from the string


### Shared Preferences - Set Preferences
StringBox.saveToPreferences(String key, String value) </br>
StringBox.saveToPreferences(String key, boolean value) </br>
StringBox.saveToPreferences(String key, int value) </br>
StringBox.saveToPreferences(String key, float value) </br>
StringBox.saveToPreferences(String key, long value) </br>
StringBox.saveToPreferences(String key, ArrayList<String> value) </br>
StringBox.saveToPreferences(String key, List<String> value) </br>
#### Use the above codes to save to shared preferences


### Shared Preferences - Get Preferences
getStringPreference(key) </br>
getBooleanPreference(key) </br>
getIntegerPreference(key) </br>
getFloatPreference(key) </br>
getLongPreference(key) </br>
getStringArrayPreference(key) - Returns as ArrayList< String > </br>
#### Use the above codes to retrieve the values from sharedpreferences.
