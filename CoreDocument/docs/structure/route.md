Khai báo route trong hệ thống
```
module.exports = function (component,application) {
    return  {
        "/index" : {
            get : {
                handler : component.controllers.index,
                authenticate : 'local',
                prefix : "/admin"
                permissions : 'index',
                key : "cid"
            }
        }
     
    }
};
```

Mỗi route được tính là 1 object với tên của object là URL trong hệ thống. Cấu trúc tương tự như Express.route

Object gồm các HTTP request và 2 hàm param và all
Với từng hàm xử lý cần có 1 hoặc 1 mảng các handler, định nghĩa các hàm xử lý cho route.
Bạn có thể đặt phân quyền cho  route qua thuộc tính permissions. permissions nhận vào 1 quyền hoặc mảng quyền hạn. Nó sẽ trả về cho hàm 
xử lý req.permissions (các quyền hạn được cho phép) và req.hasPermission(xác thực có quyền hay không).

Các thuộc tính prefix và authenticate giúp override các setting trong file structure.js

Với hàm param bạn cần phải khai báo key. Ý nghĩa tương tự express
```
    app.use("cid",function(req,res,next,id){});
```

Để gọi controllers trong file route bạn có thể gọi qua component.controllers.<tên controller>
Chú ý nếu bạn đặt name cho controllers ở structure bạn phải gọi qua name ví dụ component.controllers.backend.<tên controller>