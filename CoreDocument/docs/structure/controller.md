Chứa các logic xử lý trong hệ thống
Cấu trúc khai báo :

```
'use strict';

module.exports = function (controller,component,application) {
    controller.index = function (req, res) {
        res.render('index');
    };
    controller.about = function (req,res) {
        res.render('about');
    };
    controller.post = function (req,res) {
        res.render('post');
    };
    controller.role = function (req,res) {
        res.render('role');
    };
};

```

Ở đây bạn gán thêm các hàm cho thằng controller. 
Component là gọi đến các thành phần khác trong đối tượng đó.
Application là toàn bộ ứng dụng.
Cú pháp logic của controller tương tự so với khai báo trong express.
