## Models Arrow
Định nghĩa model của từng feature trong hệ thống : 
Models file tuân thủ hoàn toàn  cú pháp của Sequelize 
Để định nghĩa models.associate bạn có thể khai báo trong config/database.js

```
module.exports = function (sequelize, DataTypes) {
    let Category = sequelize.define("category", {
        id : {
            type : DataTypes.INTEGER,
            primaryKey : true,
            autoIncrement : true,
        },
        count: {
            type: DataTypes.INTEGER,
            defaultValue: 0,
        },
        name: {
            type: DataTypes.STRING,
        },
        alias: {
            type :   DataTypes.STRING
        }
    }, {
        tableName: 'arr_category',
        timestamps: false,
     });
    return Category
};
```

```
module.exports = {
    associate : function (models) {
        models.menus.hasMany(models.menu_detail,{ foreignKey: 'id'});
        models.menu_detail.belongsTo(models.menus,{ foreignKey: 'menu_id'});
    }
};
```