# pm2-node-red
# Auto start Node-Red with PM2 on Windows
PM2 เป็น Process Manager ใช้จัดการ Process ต่างๆ ใน Node.js
Node-RED ทำงานเป็น Process หนึ่งใน Node.js
เราสามารถใช้ PM2 สั่งให้ Node-RED ทำงานขึ้นเองอัตโนมัติทุกครั้งที่มีการเปิด Windows ได้ โดยมีการตั้งค่าต่างๆ ดังนี้
ติดตั้งโปรแกรม PM2 ก่อน ให้ใช้คำสั่ง

~~~
npm install -g pm2 
~~~

สั่งแสดง Status ของ PM2

~~~
pm2 status
~~~

pm2 status ยังไม่มี Process รันผ่าน PM2
Start Process Node-RED ด้วย PM2

~~~
pm2 start C:\Users\<User>\AppData\Roaming\npm\node_modules\node-red\red.js
~~~
~~~
pm2 start C:\Users\Administrator\AppData\Roaming\npm\node_modules\node-red\red.js
~~~

~~~
pm2 start app.js -n newname
~~~

สั่ง run Node-RED ผ่าน PM2 โดยแก้คำสั่ง <User> เป็นชื่อ User ของเครื่องที่ใช้งาน
จะเห็นว่าตอนนี้มี process ที่ชื่อ red กำลัง online อยู่
ติดตั้ง Node สำหรับใช้ในการสั่งให้ PM2 auto start
  
~~~
npm install pm2-windows-startup -g
~~~
  
~~~ 
pm2-startup install
~~~
  
ตอนนี้ PM2 ของเรามีรายการ process ที่ต้องการให้ทำงานตอนเริ่มเปิดเครื่องแล้ว คือ process ของ Node-RED ที่ชื่อ red ทำงานอยู่ ให้เรา Save รายการ process นี้ใว้ด้วยคำสั่ง pm2 save
pm2 save

~~~
pm2 save
~~~
  
ทดสอบ Restart เครื่องดู จะพบว่า PM2 สั่ง auto start Node-RED ทุกครั้งที่เปิดเครื่องใหม่
PM2 ยังมีคำสั่งอื่นอื่นอีกหลายอย่าง ลองดูได้ที่ http://pm2.keymetrics.io/docs/usage/quick-start/
