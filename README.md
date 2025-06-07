[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/w8H8oomW)


**รหัสโครงงาน:** 67-1_06_nrc-r2

**ชื่อโครงงาน (ไทย):** เว็บแอปพลิเคชันวิเคราะห์ความรู้สึกลูกค้าจากข้อความรีวิวสินค้าบนแพลตฟอร์มอีคอมเมิร์ซ 

**Project Title (Eng):** COMMENTCLARITY WEB APPLICATION FOR SENTIMENT ANALYSIS OF CUSTOMER’S PRODUCT REVIEWS ON E-COMMERCE PLATFORMS

**อาจารย์ที่ปรึกษาโครงงาน:** อ.ดร.นวฤกษ์  ชลารักษ์

**ผู้จัดทำโครงงาน:** 
1. นาย ธรรม์ บรรพกาญจน์   6409682744  than.ban@dome.tu.ac.th
2. นางสาว กัลยวรรธน์ เฉลิมไทย 649490056 kanyawat.cha@dome.ac.th
# 💬💡 CommentClarity
เว็บแอปพลิเคชันที่ใช้ปัญญาประดิษฐ์ (AI) วิเคราะห์รีวิวสินค้าบนแพลตฟอร์มอีคอมเมิร์ซแบบเรียลไทม์ โดยสามารถแยกเป็นหมวดหมู่ต่างๆและจำแนกความรู้สึกของลูกค้าได้
# 🛠️ เครื่องมือที่ใช้ดำเนินงาน
## 🌐 WEB APPLICATION
**Frontend (FE):**
Angular , tailwind.css , typescript

**Backend (BE):**
Python flask,
jwt (security)

**Database (DB):**
mysql
## 🤖 MODEL
# 💻 วิธีการรันโปรเจกต์ CommentClarity

## 1. รัน Web Frontend 

### 1.1 แก้ไขการตั้งค่าใน `config.py`

ตรวจสอบและแก้ไขค่าต่อไปนี้ในไฟล์ `config.py` (สำหรับเชื่อมต่อฐานข้อมูล):

```python
mySQL_config = {
    "HOST": 'localhost',
    "PORT": 3306,
    "USER": 'root',  # แก้เป็นชื่อผู้ใช้งานฐานข้อมูลของคุณ
    "PASSWORD": 'your_password_here',  # แก้เป็นรหัสผ่านของฐานข้อมูล
    "DATABASE": 'comment_clarity_schema',
    "CHARSET": 'utf8mb4'
}

# Flask settings
PORT = 8000
DEBUG = True
```
### 1.2 เปิด Terminal แบบ Command Prompt แล้วติดตั้ง Dependency
```bash
cd FE
npm install
npm install --legacy-peer-deps
```
### 1.3 รัน Frontend (FE)
```bash
ng serve
```
```bash
ระบบจะรันที่: http://localhost:4200
```
## 2. รัน Backend
### 2.1 เปิด Terminal แล้วรัน Flask app

```bash
cd BE
py app.py
```
