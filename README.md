# บทที่ 2: Integration Testing

เว็บไซต์ที่ใช้ทดสอบ: https://www.saucedemo.com/

## IT-01: Top-Down Integration Testing ด้วย Stub

ไฟล์: `tests/integration/IT-01.spec.ts`

แนวคิด Top-Down คือทดสอบจากโมดูลระดับบนก่อน แล้วใช้ Stub แทนโมดูลระดับล่างที่ยังไม่พร้อมหรือไม่ต้องการใช้ของจริง

| ส่วน | เป็น Real หรือ Stub | คำอธิบาย |
|---|---|---|
| หน้า Login และ Login Form | **Real** | เปิดเว็บไซต์ SauceDemo จริง กรอก `standard_user` / `secret_sauce` แล้วกด Login |
| การนำทางไป `inventory.html` | **Real** | ตรวจสอบ URL หลัง Login จริงว่าเข้าสู่หน้า Inventory |
| หน้า Inventory ที่แสดงผล | **Stub** | สร้างด้วย `page.setContent()` แทนหน้า Inventory จริง |
| ข้อความ `Mock Inventory Ready` | **Stub** | ข้อความจำลองที่ Stub สร้างขึ้น |
| สินค้า `Mock Backpack` และ `Mock Bike Light` | **Stub** | ข้อมูลสินค้าจำลอง 2 รายการ ไม่ได้มาจาก SauceDemo |

หมายเหตุ: Stub ในข้อนี้เป็นการจำลอง DOM ระดับ Browser หลัง Login จริง ไม่ใช่การแทน Internal Module ของ SauceDemo โดยตรง

## IT-02: Bottom-Up Integration Testing ด้วย Driver

ไฟล์: `tests/integration/IT-02.spec.ts`

แนวคิด Bottom-Up คือทดสอบจากโมดูลระดับล่างก่อน โดยใช้ Driver เป็นตัวเรียกใช้งานและเตรียมสถานะแทนโมดูลระดับบน

### บทบาทของ Driver

ฟังก์ชัน `driverOpenInventory()` ทำหน้าที่เป็น Driver โดย

1. ใช้ `BrowserContext.addCookies()` กำหนด Cookie `session-username` เป็น `standard_user` บนโดเมน `www.saucedemo.com` เพื่อจำลองสถานะที่ Login แล้ว
2. เปิด `https://www.saucedemo.com/inventory.html` โดยตรง ไม่ผ่าน Login Form

### ส่วนที่เป็น Real

| ส่วน | เป็น Real หรือ Driver | คำอธิบาย |
|---|---|---|
| การเตรียมสถานะ Login ด้วย Cookie | **Driver** | แทนขั้นตอน Login Form ที่เป็นโมดูลระดับบน |
| หน้า Inventory | **Real** | หน้าจริงของ SauceDemo แสดงสินค้า 6 รายการ |
| การเพิ่มสินค้าลง Cart และ Cart Badge | **Real** | ทำงานจริงบนเว็บไซต์ |
| หน้า Shopping Cart | **Real** | แสดง Sauce Labs Backpack และ Sauce Labs Bike Light จริง |

## วิธีรันและดูรายงาน

```bash
npx playwright test tests/integration
npx playwright show-report
```