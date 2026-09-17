# Week 8 Instructor Demo — GitHub Actions

Repository สำหรับผู้สอนใช้สาธิต CI pipeline แบบ **green → red → green** ใน Lab 8

## Source

- Concept: **Book D** — Hurwitz & Kirsch (2020), *Cloud Computing For Dummies*, 2nd ed., Ch. 11, pp. 149–164
- Implementation: **Instructor extension** — GitHub Actions demonstration

## Prepare the GitHub Repository

สร้าง empty public repository ชื่อ `w8-cicd-instructor-demo` แล้วคัดลอกเนื้อหาในโฟลเดอร์นี้ไปยัง repository นั้น

```bash
git init
git branch -M main
git add .
git commit -m "Create passing app and CI workflow"
git remote add origin https://github.com/<instructor-username>/w8-cicd-instructor-demo.git
git push -u origin main
```

รอให้ Actions run แรกเป็นสีเขียว แล้วเก็บ URL ไว้ใน Instructor Run Record ด้านล่าง

## Produce the Red Run

เปิด `index.test.js` และเปลี่ยน expected value:

```javascript
'Hello, Nina! CI/CD is working.'
```

เป็น:

```javascript
'Hello, Nina! This test should fail.'
```

จากนั้น:

```bash
git add index.test.js
git commit -m "Demo: intentionally break greeting test"
git push origin main
```

รอให้ Actions run เป็นสีแดง เปิด failed step และเก็บ URL ไว้

## Recover to Green

เปลี่ยน expected value กลับเป็นข้อความเดิม แล้วรัน:

```bash
npm test
git add index.test.js
git commit -m "Demo: recover from failed test"
git push origin main
```

## Instructor Run Record

กรอกหลัง push เพื่อเปิดใช้ได้ทันทีในห้อง:

| Evidence | URL | Commit SHA |
|----------|-----|------------|
| First green run | https://github.com/thammarat-ai/w8-cicd-instructor-demo/actions/runs/35240618446 | `527295e` |
| Intentional red run | https://github.com/thammarat-ai/w8-cicd-instructor-demo/actions/runs/35241013912 | `6cc79b8` |
| Recovery green run | https://github.com/thammarat-ai/w8-cicd-instructor-demo/actions/runs/35241258646 | `7c436f2` |

## Demo Checklist

- [x] Green run เปิดได้
- [x] Red run และ assertion error ยังอยู่
- [x] Recovery green run เปิดได้
- [x] ไม่มี credential หรือ `.env` ใน repository
- [x] เปิด URL ทั้งหมดใน incognito window ได้

