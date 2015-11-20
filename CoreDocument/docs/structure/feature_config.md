# Định nghĩa các giá trị trong từng feature

```
'use strict';

module.exports = {
    name : "index" // là tên của feature trong hệ thống , nếu không khai báo sẽ lấy theo tên folder.
    title: "Index Module", // Tiêu đề của ứng dụng.
    author: 'Tran Quoc Cuong', //Tên tác giả
    version: '0.1.0', // QUản lý version
    description: "Hello Arrowjs", // Mô tả tính năng
    permissions: [  //Quyền hạn cho ứng dụng
        {
            name: 'index',
            title: "go to index"
        },
        {
            name: 'about',
            title: "go to about"
        },
        {
            name: 'post',
            title: "go to post"
        }
    ]
};


```