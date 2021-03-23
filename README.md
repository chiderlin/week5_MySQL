# week5_MySQL
practice MySQL command line to handle data


## 要求三
#### insert into user(name, username, password) values ("ply","ply","ply");
#### insert into user(name, usernamem password) values ("test1","test1","test1");
#### insert into user(name, usernamem password) values ("test2","test2","test2");
#### insert into user(name, usernamem password) values ("test3","test3","test3");
#### insert into user(name, usernamem password) values ("test4","test4","test4");
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/1.JPG)
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/2.JPG)

### select count(id) from user;
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/3.JPG)

### select * from user order by time desc;
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/4.JPG)

### select * from user where id=2 or id=3 or id=4 order by time desc;
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/5.JPG)

### select * from user where username="ply";
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/6.JPG)

### select * from user where username="ply" and password="ply";
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/7.JPG)

### update user set name="丁滿" where username="ply";
### select * from user;
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/8.JPG)

### truncate table user;
### select * from user;
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/9.JPG)


## 要求四
#### create table message(
####    id bigint auto_increment,
####    user_id bigint not null,
####    content varchar(255) not null,
####    time datetime not null default now(),
####    primary key(id),
####    foreign key(user_id) references user(id)
#### );

#### show tables;
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/4-1.JPG)


### select message.user_id, message.content, user.name from message
### inner join user on message.user_id=user.id
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/4-2.JPG)


### select message.user_id, message.content, user.name from message
### inner join user on user.id=message.user_id where user.username="ply";
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/4-3.JPG)


## 補充

### - (cmd 輸入的指令)錯誤:mysqldump要取出sql資料時無法通過驗證。
**mysqldump: Got error: 2059: Authentication plugin 'caching_sha2_password' cannot be loaded: when trying to connect** 
(雖然這裡的語法也打錯，但先繼續~)
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/error_msg.JPG)


### - 原因: mysql因為版本8.0使用caching_sha2_password，要改回以前mysql版本的mysql_native_password mode 
資料來源:
https://stackoverflow.com/questions/49194719/authentication-plugin-caching-sha2-password-cannot-be-loaded


### - 使用方法
##### alter user 'root'@'localhost'identified with mysql_native_password by 'yourpassword';
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/DEBUG.JPG)

### - cmd 輸入的指令
#### mysqldump -u帳號 -p密碼 DBName TableName > PATH\檔名.sql 
#### mysqldump -uroot -pXXXXXX website user message > PATH\data.sql
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/ok.JPG)

### 成功取得sql檔
---

### Mysql其他語法取得sql資訊
![image](https://github.com/chiderlin/week5_MySQL/blob/main/pic/final.JPG)
