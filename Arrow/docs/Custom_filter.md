#### Folder setting

config/view.js
```
    functionFolder : '/extendsView/function',
    filterFolder : '/extendsView/filter',
    variableFile : '/extendsView/variable.js'
```
#### Custom filter sample

Declare : 
```
   module.exports = {
       name: "test", //default file_name
       async :true, // default false 
       handler : function (param,cb) { //if async we must push cb(err,data)
           fs.readFile("file", function (err,data) {
               cb(null,err)
           })
       }
   }; 
```

Use : 
```
    {{ "" | test }} //param = "",second param need add to test(b,c)..
```



#### Function sample
Carefully : Only sync function

Declare :
```
 module.exports = {
       name: "test", //default file_name
       handler : function (param) { 
           .....
       }
   }; 
```

Use : 
```
    {{ test() }} 
```

#### Variable sample
Carefully : Only sync function

Declare :
```
 module.exports = {
       "hello" : "Hello World"
 }; 
```

Use: 
```
    {{ test }}
```