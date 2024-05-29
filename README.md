# Database Programming

โปรเจคนี้เป็นส่วนหนึ่งของรายวิชา 2603491 การโปรแกรมสำหรับฐานข้อมูล ภาควิชาสถิติ คณะพาณิชยศาสตร์และการบัญชี จุฬาลงกรณ์มหาวิทยาลัย

## สารบัญ

- [หัวข้อที่ศึกษา](#หัวข้อที่ศึกษา)
- [วัตถุประสงค์](#วัตถุประสงค์)
- [ขั้นตอนในการติดตั้ง (Viusal Studio Code)](#ขั้นตอนในการติดตั้ง-visual-studio-code)
- [รายงาน](#รายงาน)

## หัวข้อที่ศึกษา

ระบบการวิเคราะห์และรายงานผลประกอบการร้านชาบู 3 พี่น้องผ่านเว็บไซต์เพื่อการจัดการ

## วัตถุประสงค์

ในปัจจุบันการแข่งขันในตลาดธุรกิจชาบูบุฟเฟต์ในไทยมีการเติบโตเป็นอย่างมาก โดยเฉพาะอย่างยิ่งในการค้นหาธุรกิจบุฟเฟ่ต์ในประเทศไทยเทียบตั้งแต่พ.ศ. 2547 จนถึง ปี 2566 ที่มากขึ้นถึง 1 แสนครั้ง ต่อ เดือน (สุรสิทธิ์ สัจจะเดว์, 2565) นอกจากนี้การสืบค้นหา Brand Keywords ประเภทบุฟเฟ่ต์ชาบูยังมาถึงร้อยละ 15.4 ของการสืบค้นทั้งหมด การบริหารจัดการต้นทุนและผลประกอบการขายเพื่อการแข่งกับกับคู่แข่งจึงเป็นส่วนที่มีความสำคัญเป็นอย่างยิ่งสำหรับผู้ประกอบการ พบว่าทางร้านชาบู 3 พี่น้องจัดการข้อมูลผลการดำเนินงานทุกเดือนจากการดึงข้อมูลระบบ POS บน loyverse และนำมาทำรายงานบน Microsoft Excel ทุกสิ้นเดือน เป็นผลให้ผู้ประกอบการร้านชาบู 3 พี่น้องต้องเสียเวลาและทรัพยากรในการจัดการรูปดังกล่าวเป็นจำนวนมาก ร้านจึงมีความจำเป็นต้องจัดการรายงานสรุปผลการดำเนินงานให้สะดวกรวดเร็วมากขึ้นด้วยการจัดการระบบฐานข้อมูล จากการดำเนินงานจะพบว่าในเดือนล่าสุดธุรกิจมีการขาดทุนทำให้ผู้ประกอบการต้องการทราบข้อมูลการจัดการและบริหารต้นทุนของการดำเนินงานทั้งหมด 3 สาขา อีกทั้งการจัดการในระบบ POS บน loyverse สามารถติดตามจำนวนยอดขายได้ในช่วงสิ้นเดือน แต่หากทางร้านชาบู 3 พี่น้องต้องการข้อมูลสรุปยอดขายเพื่อนำไปจัดทำการส่งเสริมทางการตลาดจะทำให้ต้องรอข้อมูลจนถึงสิ้นเดือนส่งผลให้ธุรกิจเสียโอกาสที่จะสร้างยอดขาย ด้วยปัญหาดังกล่าว ทางคณะผู้จัดจึงได้ทำการสร้างระบบฐานข้อมูลและ Web Application เพื่อใช้ในการวิเคราะห์ข้อมูลยอดขายและต้นทุนจากการดำเนินงาน รวมถึงการทำรายงานผลประกอบการจากการวิเคราะห์ข้อมูลให้สะดวกและรวดเร็วมากขึ้น

## ขั้นตอนในการติดตั้ง (Viusal Studio Code)
1. Clone โปรเจคจาก GitHub หรือดาวน์โหลด ZIP file
2. เปิด MySQL Workbench เลือกแท็ป Administration หรือ Server เลือก Data Import/Restore
3. เลือก Import from Dump Project Folder คลิก ... เลือกโฟลเดอร์ shabu3peenong ในโฟลเดอร์ที่ Clone มา
4. ที่ Default Target Schema: เลือก New... และพิมพ์ชื่อ shabu3peenong
5. คลิก Start Import
6. เปิด Visual Studio Code เลือก Open Folder เลือก Folder Project
7. คลิก Terminal เลือก New Terminal
8. บน Terminal พิมพ์ pip install --user pipenv (pip3 install --user pipenv สำหรับ Mac)
9. บน Terminal พิมพ์ pipenv shell เพื่อเข้าสู่ Visual Environment
10. บน Terminal พิมพ์ pipenv install เพื่อติดตั้ง Package เช่น Django
11. บน Terminal พิมพ์ cd shabu3peenong เพื่อเข้าโฟลเดอร์โปรเจค
12. เปิด settings.py ในโฟลเดอร์ Project/shabu3peenong เลื่อนลงมาที่ส่วน Database เปลี่ยน PASSWORD เป็นรหัสผ่านที่ใช้เข้า MySQL ของตัวเอง

        DATABASES = {
            'default': {
                'ENGINE': 'mysql.connector.django',
                'NAME': 'shabu3peenong',
                'USER': 'root',
                'PASSWORD': 'รหัสผ่านที่ใช้เข้า MySQL ของตัวเอง', <- เปลี่ยนแค่ตรงนี้
                'HOST': '127.0.0.1',
                'PORT': '3306',
            }
        }

13. บน Terminal พิมพ์ python manage.py check หรือ python manage.py runserver หากขึ้น System check identified no issues (0 silenced). ถือว่าเสร็จสมบูรณ์

## รายงาน

ดาวน์โหลดรายงานได้ที่ [รายงาน.pdf](Report/รายงาน.pdf) หรือ [รายงาน.docx](Report/รายงาน.docx)
