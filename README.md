# Manhwa Splitter Studio

เว็บแอปสำหรับงาน Manhwa Typesetting ทำงานใน Browser และ Deploy ได้ด้วย GitHub Pages โดยไฟล์ภาพประมวลผลในเครื่องผู้ใช้ ไม่ได้อัปโหลดไปยัง Backend ของแอป

## ฟีเจอร์

- **Image Splitter:** เลือกโฟลเดอร์ภาพ, เรียงชื่อไฟล์แบบ natural sort, ดูภาพยาวแบบต่อเนื่อง, กำหนดระยะเส้นแบ่ง, เพิ่ม/ลาก/ลบเส้น และ Export PSD เป็นชิ้น ๆ
- **Width Resizer:** ตรวจขนาดภาพ, เลือกความกว้าง 600/700/800/900 px หรือกำหนดเอง และรักษาสัดส่วน
- **Cover & Watermark:** อัปโหลดภาพปกและลายน้ำ, ตั้งค่า opacity, สุ่มตำแหน่งแนวนอน, วาง Watermark กลางแนวตั้ง
- **PSD Layers:** ภาพหลัก, ภาพปก และ Watermark เป็น Layer แยก
- **ZIP Export:** ผลลัพธ์แยกโฟลเดอร์ `_psd`, `_resize_psd`, `_success_psd` และเก็บภาพ Original ใน `OG-Original`

## วิธีติดตั้งบน GitHub

1. สร้าง GitHub repository ใหม่ เช่น `manhwa-splitter-studio`.
2. อัปโหลดไฟล์ทั้งหมดใน repository นี้ โดยให้ `index.html` อยู่ที่ root.
3. เข้า **Settings → Pages**.
4. ที่ **Build and deployment** เลือก **Deploy from a branch**.
5. เลือก branch `main` และ folder `/ (root)` แล้วกด Save.
6. รอ GitHub สร้างเว็บ แล้วเปิด URL ที่แสดงในหน้า Pages.

## วิธีใช้

1. เปิดเว็บบน Chrome, Edge หรือ Browser ที่รองรับ `webkitdirectory`.
2. เลือกโฟลเดอร์ภาพในหน้า Splitter หรือ Resizer.
3. ตรวจสอบลำดับภาพและขนาดก่อนเริ่มงาน.
4. Splitter: ระบุระยะเส้นแบ่งแล้วกด **สร้างเส้นแบ่ง**; ลากเส้นเพื่อปรับ หรือกด × เพื่อลบ.
5. Resizer: เลือก preset หรือใส่ความกว้างเป้าหมาย.
6. กำหนด Cover/Watermark ได้ในหน้าที่สาม.
7. กด Export แล้วเลือกว่าจะใส่ Cover และ Watermark หรือไม่.
8. เว็บจะดาวน์โหลด ZIP ให้แตกไฟล์ใน Windows.

## ข้อควรทราบ

- เว็บไม่สามารถเขียนไฟล์ลงโฟลเดอร์ต้นฉบับของ Windows โดยตรงได้ จึงดาวน์โหลด ZIP ซึ่งภายในมี `OG-Original/` และโฟลเดอร์ผลลัพธ์.
- PSD ใช้ `ag-psd` ผ่าน CDN และ ZIP ใช้ `JSZip` ผ่าน CDN ดังนั้นต้องมีอินเทอร์เน็ตเมื่อเปิดเว็บครั้งแรก/ใช้งานไลบรารี.
- PSD จะมี Layer แยกสำหรับภาพหลักและ Watermark; Cover Image จะเป็น Layer แยกในไฟล์แรกและไฟล์สุดท้ายเมื่อเลือก Cover.
- งานภาพขนาดใหญ่มากอาจใช้ RAM สูง เพราะการประกอบและสร้าง PSD เกิดขึ้นใน Browser. ควรแบ่งงานเป็นชุดหากมีหลายร้อยภาพหรือภาพมีความละเอียดสูงมาก.
- รองรับชนิดภาพที่ Browser เปิดได้; แนะนำ PNG/JPG/WebP. GIF/AVIF อาจขึ้นกับความสามารถของ Browser.
- ตรวจสอบไฟล์ PSD ที่สร้างกับ Photoshop เวอร์ชันที่ใช้งานจริงก่อนใช้กับงาน production. ไลบรารีภายนอกและ API ของ Browser อาจเปลี่ยนแปลงได้.

## Dependencies

- [ag-psd](https://github.com/Agamnentzar/ag-psd)
- [JSZip](https://stuk.github.io/jszip/)

ทั้งสองไลบรารีโหลดจาก CDN ใน `js/app.js`.
