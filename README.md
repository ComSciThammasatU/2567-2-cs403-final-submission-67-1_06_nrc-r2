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

## 1. รันโมเดลใน `sentiment.py`

### 1.1 ทำการติดตั้ง Chormdriver ที่เป็นเวอร์ชั่น chorm ของเครื่อง
https://developer.chrome.com/docs/chromedriver/downloads?hl=th

### 1.2 ทำการเปลี่ยนที่อยู่ของ Chormdriver ในเครื่อง
```python
df = pd.read_csv(r"C:\Users\aommelet\OneDrive - Thammasat University\เดสก์ท็อป\CommentCarity\scrap\LabeledData.csv", encoding='utf-8-sig') # แก้เป็นชื่อผู้ใช้งานฐานข้อมูลของคุณ
df = df.drop_duplicates(subset='text', keep='first').drop(columns=['product'])
df.info()
```
### 1.3 ทำการกดปุ่ม Run all เพื่อรันโมเดล และเมื่อได้ผลลัพท์มาให้ทำการย้ายไฟล์ผลลัพธ์ด้านล่างนี้ไปที่โฟล์เดอร์ analyze_model เพื่อเตรียมไฟล์ Model สำหรับ Sentiment Analysis
```file
cvec.pkl

le_category.pkl

le_sentiment.pkl

xgb_category.json

xgb_category.pkl

xgb_sentiment.json

xgb_sentiment.pkl
```
## 2. รัน Web Frontend 

### 2.1 แก้ไขการตั้งค่าใน `config.py`

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
### 2.2 เปิด Terminal แบบ Command Prompt แล้วติดตั้ง Dependency
```bash
cd FE
npm install
npm install --legacy-peer-deps
```
### 2.3 รัน Frontend (FE)
```bash
ng serve
```
```bash
ระบบจะรันที่: http://localhost:4200
```
## 3. รัน Backend
### 3.1 เปิด Terminal แล้วรัน Flask app

```bash
cd BE
py app.py
```
## 4. รัน SQL

### 4.1 เตรียมฐานข้อมูล
```
เปิดไฟล์ SQL ทั้ง 2 ไฟล์ในเครื่อง:
   - create-scrip.sql – สำหรับสร้างฐานข้อมูล
   - insert-scrip.sql – สำหรับเพิ่มข้อมูล sentiment และ category
```
### 4.2 รันไฟล์ `create-scrip.sql`
### 4.3 รันไฟล์ `insert-scrip.sql`
ทำการ Execute Current Statement ในบรรทัดดังต่อไปนี้ตามลำดับ
```sql
-- เพิ่มข้อมูลเริ่มต้นในตาราง SentimentAnalysis
INSERT INTO SentimentAnalysis (sentimentType) VALUES
('Positive'),
('Negative'),
('Neutral');
```
```sql
-- เพิ่มข้อมูลเริ่มต้นในตาราง CommentCategory
INSERT INTO CommentCategory (commentCategoryName) VALUES
('Product'),
('Delivery'),
('Service'),
('Other');
```
## ⭐️จากนั้นสามารถดำเนินการใช้ WEB APPLICATION 🌐 ได้ตามต้องการ โดยสามารถดูวิธีการใช้การได้ในโฟล์เดอร์ demo⭐️
