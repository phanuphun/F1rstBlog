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

## เบื้องต้น
Tailwind CSS เป็น Framework CSS เพื่อใช้ในการออกแบบเว็บไซต์โดยใช้แนวทาง Utility-first ที่เน้นใช้ class ขนาดเล็กเพื่อกำหนดสไตล์โดยตรงให้กับ html

### โครงสร้างไฟล์สำคัญ
หลงจากการลง tailwind เสร็จแล้ว(ยกเว้นการใช้งานแบบ CDN) จะมีโครงสร้างไฟล์เพิ่มขึ้นมาเพื่อใช้ในการใช้งานตัว tailwind ดังนี้
- **📁 tailwind.conf.js** : เป็นไฟล์สำคัญที่จำเป็นต้องมีทุกครั้งในการใช้งาน และที่สำคัญคือไฟล์นี้จะใช้ในการปรับแต่งตัว tailwind ของเรา เช่นการเพิ่ม plugin ไฟล์นี้จะถูกสร้างขึ้นมาเมื่อเรารันคำสั่ง `npx tailwindcss init`
- **📁 input.css** : ไฟล์นี้เปรียบเสมือนไฟล์ต้นแบบที่เราจะนำเข้า directive ต่างๆดังนี้ `@tailwind base` , `@tailwind components` และ `@tailwind utilities` ในไฟล์นี้เมื่อเราทำการ build จะถูกนำไปเป็นต้นทางสำหรับการ build ไฟล์ css ออกมาตามคำสั่งด้านล่างในส่วนของ output เลย ทั้งนี้เรายังสามารถปรับแต่ง class ได้ในนี้อีกด้วย
- **📁 src/output.css** : เป้นไฟล์ css ที่จะถูก build ออกมาในโฟลเดอร์ **src/** ในไฟล์ tailwind.css นี้จะเป็น css ที่ถูก build มาจาก utility classes ที่เราเลือกใช้ โดยเราสามารถกำหนด directory หรือชื่อใหม่ได้เช่น **dist/tailwind.css** โดยไฟล์นี้จะได้จากการที่เรารันคำสั่ง `npx tailwindcss -i ./src/input.css -o ./dist/tailwind.css --watch`
- **📁 postcss.config.js** : หากตัวโปรเจ็คมีการใช้งาน PostCSS รวมกับ tailwind CSS เพื่อปรับปรุงการ build ไฟล์นี้จะถูกสร้างขึ้นมาเพื่อกำหนด plugin ต่างๆ

<ref-box>
   <b>อธิบายเพิ่มเเติมเกี่ยวกับ directive ของ tailwind</b>
   @tailwind base : สำหรับการตั้งค่าพื้นฐานและ CSS reset
   @tailwind components : สำหรับการจัดการกับ component-based CSS
   @tailwind utilities : สำหรับ utility classes ที่ใช้จัดการ styling เช่น margin, padding, ขนาดฟอนต์ และสีต่าง ๆ
</ref-box>

---
## การใช้งาน

---
## อื่นๆ
### การใช้งาน Theme
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
