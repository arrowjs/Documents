## Arrow Structure
Hệ thống arrowjs tự động load dữ liệu dựa theo structure.js trong config.
Ứng dụng Arrowjs được chia thành các tính năng (feature) đây là các logic
Có 2 loại tính năng :
-  composit feature
-  singleton feature
Với composit feature là tập hợp của rất nhiều các feature.
Trong structure.js là đối tượng có 2 cấp độ.
Ở cấp 1 bạn khai báo các loại tính năng mong muốn :

```
module.exports = {
    features: {
        "path": {
            "folder": "/features",
            "file": "feature.js"
        },
        "extend": {
            system: true,
            active: true
        },
        "model": {
            "path": {
                "folder": "models",
                "file": "*.js"
            }
        },
        "view": {
            "path": {
                "folder": "view"
            }
        },
        "controller": {
            "path": {
                "folder": "controller",
                "file": "*.js"
            }
        },
        "route": {
            "path": {
                "file": "route.js"
            }
        }
    }
}
```

Ở trong ví dụ ta định nghĩa tính năng tên là **features**

Ở cấp độ 2 ta định nghĩa loại và các thành phần đi kèm của **features**

Với mỗi feature cần có path để lấy thông tin:

```
 "path": {
            "folder": "/features", //thư mục chứa các feature
            "file": "feature.js", //File config từng feature
            "singleton" : false   //Định nghĩa loại feature - mặc định là false         
        },
 ```
	
Mỗi feature trong Arrowjs được cấu trúc theo mô hình MVC: 

```
		"extend": {
            system: true,
            active: true
        },
        "model": {
            "path": {
                "folder": "models",
                "file": "*.js"
            }
        },
        "view": {
            "path": {
                "folder": "view"
            }
        },
        "controller": {
            "path": {
                "folder": "controller",
                "file": "*.js"
            }
        },
        "route": {
            "path": {
                "file": "route.js"
            }
        }

```	
Với mỗi thành phẩn của feature đều định nghĩa path để có thể lấy được dữ liệu.
path của các thành phần có 2 loại : nhận vào object hoặc array Object.

```
	"path": {
       "folder": "models", 
       "file": "*.js",
	}
```

```
	"path": [{
       "folder": "backend/models", 
       "file": "*.js",
	},{
       "folder": "frontend/models", 
       "file": "*.js",
	}]
```
## Thuộc tích của path


```
	"path": {
       "folder": "models", 
       "file": "*.js",
       "name" : "frontend",
       "prefix" : "/admin",
       "singleton" : true,
       "authenticate" :  true
   }
```
#### Folder 
Là chuỗi hoặc array chuỗi xác định thư mục chứa dữ liệu :

```
 "folder": "models", 
 or
 "folder" : ["models","views"]
```
Chuỗi bắt đầu từ "/" sẽ tính từ thư mục gốc của ứng dụng Arrowjs.
Chuỗi còn lại tính từ thư mục của từng feature,

Ký tự đặc biệt

```
"folder" : "view/:theme/$component"
```
":theme" : truyền giá trị config có key là "theme"" vào trong đường dẫn
"$component" : truyền vào tên của feature hiện thời.

#### File
là chuỗi định nghĩa file lấy cấu hình
```
"file": "*.js", 
 or
 "file" : index.js
```
Với "*.js" Arrowjs sẽ loading toàn bộ file javascript trong thư mục.
#### Name
là chuỗi tên định danh giúp tạo ra các namespace:

```
"controller": [{
       "folder": "backend/controllers", 
       "file": "*.js",
       "name" : "frontend"
	},{
       "folder": "frontend/controllers", 
       "file": "*.js",
        "name" : "backend"
	}]
```
Controller sau khi loading sẽ chia vào theo namespace . Bạn phải gọi rõ ràng controller.backend , controller.frontend

#### Prefix

```
"route" : {
	"folder": "backend/routes", 
    "file": "*.js",
	"prefix" : "/admin",
}
      
```
Chuỗi định danh đường dẫn chung của Route (chỉ áp dụng với route settings). Ở trên các route từ thằng backend/routes đều bắt đầu bằng "/admin" . Có thể  override setting này tại từng route.

#### Singleton
Với các tính năng trong hệ thống mặc định là singleton.

#### Authenticate
Chuỗi định danh cấu hình passport hoặc bật tính năng passport. Chỉ áp dụng cho route . 
```
"route" : {
	"folder": "backend/routes", 
    "file": "*.js",
	"authenticate" : "true" // "local",
} 
      
```
Các route load từ thư mục backend/routes cần phải authenticate.