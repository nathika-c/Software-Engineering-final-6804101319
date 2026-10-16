# สรุปผลการทดสอบ Playwright

- ผู้ส่ง: 6804101319 นางสาวณฐิกา จันทร์เสถียร
- เว็บไซต์ที่ทดสอบ: https://www.saucedemo.com/
- เบราว์เซอร์: Chromium
- วันเวลาที่รัน: 10/16/2026, 2:06:25 PM
- เวลารวม: 7.6 วินาที
- คำสั่งที่ใช้: `npx playwright test`

## ผลรวม

| All | Passed | Failed | Flaky | Skipped |
|---|---|---|---|---|
| 8 | 8 | 0 | 0 | 0 |

## ผลรายข้อ

| ข้อ | ไฟล์ | ชื่อ Test | ผล | เวลา |
|---|---|---|---|---|
| 1 | tests/unit/UT-01.spec.ts | UT-01.1: empty username and password | Passed | 572ms |
| 1 | tests/unit/UT-01.spec.ts | UT-01.2: missing password | Passed | 578ms |
| 1 | tests/unit/UT-01.spec.ts | UT-01.3: invalid login details | Passed | 575ms |
| 2 | tests/unit/UT-02.spec.ts | UT-02: product button state Add to cart -> Remove -> Add to cart | Passed | 653ms |
| 3 | tests/integration/IT-01.spec.ts | IT-01: top-down REAL Login -> browser-level Inventory STUB | Passed | 1.8s |
| 4 | tests/integration/IT-02.spec.ts | IT-02: DRIVER login state -> REAL Inventory and Cart | Passed | 627ms |
| 5 | tests/system/ST-01.spec.ts | ST-01: complete purchase of two products | Passed | 867ms |
| 6 | tests/system/ST-02.spec.ts | ST-02: checkout validation and recovery | Passed | 972ms |

## ข้อผิดพลาดที่พบ

ไม่พบข้อผิดพลาดในการรันครั้งนี้ ทุก Test Case ผ่านทั้งหมด

## ไฟล์รายงาน

- HTML Report: `playwright-report/index.html` (ดูด้วย `npx playwright show-report`)
- JSON Report: `reports/results.json`

ผลสรุปนี้บันทึกจากรายงานที่ Playwright สร้างขึ้นจากการรันจริง ไม่ได้แก้ไขผลด้วยตนเอง