---
title: Tailwind CSS
date: '2024-09-27'
description: 'บันทึกการใช้งาน Tailwind CSS'
tag: Note
tags:
   - Tailwind
   - CSS Framework
img: /img/tailwind/cover.png
path: 'tailwind'
draft: false
---

---
## เบื้องต้น
Tailwind CSS เป็น Framework CSS เพื่อใช้ในการออกแบบเว็บไซต์โดยใช้แนวทาง Utility-first ที่เน้นใช้ class ขนาดเล็กเพื่อกำหนดสไตล์โดยตรงให้กับ html

### โครงสร้างไฟล์สำคัญ
หลงจากการลง tailwind เสร็จแล้ว(ยกเว้นการใช้งานแบบ CDN) จะมีโครงสร้างไฟล์เพิ่มขึ้นมาเพื่อใช้ในการใช้งานตัว tailwind ดังนี้
- **📁 tailwind.conf.js** : เป็นไฟล์สำคัญที่จำเป็นต้องมีทุกครั้งในการใช้งาน และที่สำคัญคือไฟล์นี้จะใช้ในการปรับแต่งตัว tailwind ของเรา เช่นการเพิ่ม plugin ไฟล์นี้จะถูกสร้างขึ้นมาเมื่อเรารันคำสั่ง `npx tailwindcss init`
- **📁 input.css** : ไฟล์นี้เปรียบเสมือนไฟล์ต้นแบบที่เราจะนำเข้า directive ต่างๆดังนี้ `@tailwind base` , `@tailwind components` และ `@tailwind utilities` ในไฟล์นี้เมื่อเราทำการ build จะถูกนำไปเป็นต้นทางสำหรับการ build ไฟล์ css ออกมาตามคำสั่งด้านล่างในส่วนของ output เลย ทั้งนี้เรายังสามารถปรับแต่ง class ได้ในนี้อีกด้วย
- **📁 src/output.css** : เป้นไฟล์ css ที่จะถูก build ออกมาในโฟลเดอร์ **src/** ในไฟล์ tailwind.css นี้จะเป็น css ที่ถูก build มาจาก utility classes ที่เราเลือกใช้ โดยเราสามารถกำหนด directory หรือชื่อใหม่ได้เช่น **dist/tailwind.css** โดยไฟล์นี้จะได้จากการที่เรารันคำสั่ง `npx tailwindcss -i ./src/input.css -o ./dist/tailwind.css --watch`
- **📁 postcss.config.js** : หากตัวโปรเจ็คมีการใช้งาน PostCSS รวมกับ tailwind CSS เพื่อปรับปรุงการ build ไฟล์นี้จะถูกสร้างขึ้นมาเพื่อกำหนด plugin ต่างๆ

<ref-box>
   <b>เพิ่มเติมเกี่ยวกับ directive ของ tailwind</b>
   @tailwind base : สำหรับการตั้งค่าพื้นฐานและ CSS reset
   @tailwind components : สำหรับการจัดการกับ component-based CSS
   @tailwind utilities : สำหรับ utility classes ที่ใช้จัดการ styling เช่น margin, padding, ขนาดฟอนต์ และสีต่าง ๆ
</ref-box>

---
## Classes

---
## อื่นๆ
### การใช้งาน Dark Mode
ใน tailwind css มีระบบ Dark Mode เพื่อรองรับการทำเว็บไซต์ที่มีทั้งโมหดมืดและสว่างได้อย่างง่ายดาย โดยใช้ utility class ที่จะรองรับการเปิดปิดโหมดมืดและสว่าง โดยจะมี 2 วิธีหลักๆ ดังนี้

**วิธีที่ 1 :** การใช้งานการตั้งค่าตามระบบปฏิบัติการของเราตามค่า `prefers-color-scheme` (เป็นหนึ่งใน CSS Media Query ที่ถูกออกแบบมาเพื่อรองรับการพัฒนาเว็บไซต์ที่ต้องการปรับเปลี่ยนธีมโหมดโดยเฉพาะ) ในโหมดนี้จะเป็นค่า Default ที่ถูกตั้งเอาไว้ การที่ธีมของเราจะเปลี่ยนได้จำเป็นต้องมีการระบุ class `dark:` ใน Element ที่เราต้องการเปลี่ยนโหมดก่อน จากโค้ดด้านล่างจะเป็นการกำหนดให้ตัวอักษรมีสีฟ้าซึ่งเป็นค่าเริ่มต้นหรือ `Light Mode` ที่เป็นค่าตรงข้ามจาก `Dark Mode` นั่นเอง กรณีนี้เราต้องการให้เปลี่ยนสีตัวอักษรเป็นสีแดงเมื่อเราเปลี่ยนธีมเป็น Dark Mode ก็ต่อเมื่อเราเปลี่ยนธรมในระบบปฏิบัติการของเรา
```html
<div class="text-blue-500 dark:text-red-500">
   Text
</div>
```


**วิธีที่ 2 :**  การเปิดใช้งานเอง จะเป็นการที่เราสามารถควบคุมการเปลี่ยนธีมได้ด้วยตัวเราเอง โดยอันดับแรกให้เราไปที่ไฟล์ `tailwind.conf.ts` ให้เราเพิ่ม key ที่ชื่อว่า `darkMode` ขึ้นมาโดยปกติค่าเริ่มต้นของ darkMode จะอยู่ที่ `media` ซึ่งก็คือวิธีการแรกที่เลือกการตามตั้งค่าของระบบปฏิบัติการของเรา แต่ในกรณีที่เราต้องการปรับเปลี่ยนเองให้เราเปลี่ยนเป็น `class` ดังนี้
```js
module.exports = {
  darkMode: 'class',
}
```

ให้เราเพิ่ม class `dark` ไปที่แท็ก **html** หรือ **body** เพื่อบ่งบอกว่า Dark Mode ถูกเปิดใช้งานแล้ว เมื่อมีคลาส dark:class ถูกเพิ่มเข้าไป นั่นหมายความว่าโหมดนี้จะถูกเปิดทันที ซึ่งหมายความว่าหากเราต้องการจะทำให้ Light Mode เป็นค่าเริ่มต้นจำเป็นต้องมีส่วนที่เราสามารถควบคุมการเพิ่มและลบ class ในส่วนของคลาส dark ออกไป และการที่เราจะทำแบบนั้นได้เราจำเป็นต้องใช้  javascript เข้าช่วยอีกทีนั่นเอง
```html
<html class="dark">
   <div class="text-blue-500 dark:text-red-500">
      Text
   </div>
</html>
```
```js
// JavaScript สำหรับสลับโหมดมืด
const toggleDarkMode = () => {
  document.documentElement.classList.toggle('dark');
}
```

### การทำ Responsive เพื่อรองรับการใช้งานอุปกรณ์หลายขนาด

---
## Plugin
### การใช้ Tailwind Typography เพื่อรองรับ Markdown
### การใช้ Tailwind Line Clame เพื่อตัดบรรทัดข้อความ

---
## อ้างอิง
<ref-box>
https://tailwindcss.com/docs/installation
https://blog.yunusemre.dev/responsive-design-with-tailwind/
</ref-box>
