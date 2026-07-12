# siamsun-monitoring-stack

# โปรเจค: ระบบ Monitoring สำหรับ SME — สยามซัน ออโต้เซลส์

## ปัญหา
SIAMSUN AUTO SALE มีพนักงาน 27-50 คน
- ไม่มีระบบ monitor — เวลามีปัญหาต้องรอ user แจ้งอย่างเดียว
- เจอปัญหา "เน็ตช้า/หลุดวันละครั้ง" ไม่รู้ว่าต้นตอมาจากอะไร

## วิธีแก้
ติดตั้ง Uptime Kuma (Open Source) 1 container บน Linux VM:
- 🔍 Ping เช็ค MikroTik ทุก 20 วินาที → รู้ทันทีถ้า Router ดับ
- 🌐 Ping 8.8.8.8 + 1.1.1.1 + HTTP เช็คเว็บไทย → แยกได้ว่า ISP หลุด
- 💾 Ping + Port เช็ค NAS → รู้ว่า NAS ทำงานปกติ
- 📱 แจ้งเตือนเข้า Telegram ทันที
- 📊 Status Page แบบ Real-time


## Tech Stack
```
Uptime Kuma (Docker) → Ping/TCP/HTTP Monitor
                     → Telegram Alert
                     → Status Page
Linux (Ubuntu)       → Host
WireGuard            → เชื่อมต่อไปยัง MikroTik ลูกค้า
```

## ผลลัพธ์
- รู้สถานะ Router, NAS, Internet แบบ Real-time
- แจ้งเตือนเข้าโทรศัพท์ทันทีเมื่อมีปัญหา
- Status page ที่แชร์ให้ลูกค้าดูได้
- Zero cost — ใช้ Open Source ทั้งหมด
- สามารถต่อยอดเพิ่ม SNMP หรือ API integration ได้

## ทักษะที่ได้ใช้
- Linux Administration (Ubuntu, Docker)
- Network (WireGuard, MikroTik, TCP/IP)
- Monitoring & Alerting (Uptime Kuma, Telegram API)
- Problem Solving — ทำของจริงให้ลูกค้าจริง
