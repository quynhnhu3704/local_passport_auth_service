# local_passport_auth_service

## Cách chạy

```bash
npm install
node app.js
```

Server chạy tại: `http://localhost:3000`

---

## API Endpoints

* `POST /auth/register` → Đăng ký
* `POST /auth/login` → Đăng nhập
* `GET /auth/profile` → Trang cá nhân (yêu cầu đã login)
* `GET /auth/logout` → Đăng xuất

---

## Cách test với Postman

### Register

* `POST http://localhost:3000/auth/register`
* Body → Raw JSON:

```json
{
  "username": "quynhnhu",
  "password": "123"
}
```

* Kết quả:

```json
{ "message": "User registered successfully" }
```

---

### Login

* `POST http://localhost:3000/auth/login`
* Body → Raw JSON:

```json
{
  "username": "quynhnhu",
  "password": "123"
}
```

* Kết quả:

```json
{ "message": "Logged in successfully", "user": { ... } }
```

* Tab **Cookies** → thấy `connect.sid=...`

---

### Profile

* `GET http://localhost:3000/auth/profile`
* Postman tự gửi cookie kèm request
* Nếu còn hiệu lực → trả về thông tin user (không bao gồm password)

---

### Logout

* `GET http://localhost:3000/auth/logout`
* Session bị xoá và cookie `connect.sid` cũng bị xoá
* Kết quả:

```json
{ "message": "Logged out" }
```

---

## Hình minh họa

![Register](public/results/register.png)
*Đăng ký user thành công*

![Register - mongo users](public/results/register_mongo_users.png)
*Kiểm tra collection `users` trong MongoDB sau khi register*

![Login](public/results/login.png)
*Đăng nhập thành công, cookie được cấp*

![Profile](public/results/profile.png)
*Truy cập profile khi session hợp lệ*

![Logout](public/results/logout.png)
*Đăng xuất, session và cookie bị xoá*
