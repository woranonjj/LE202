# รายงานอธิบายความหมายและความสัมพันธ์ของคำสำคัญ
## 1.โปรแซสเซสเซอร์ (processor,microcontroller)
### คอมพิวเตอร์จะต้องมีส่วนที่เป็นสมองที่เรียกว่า processor ซึ่งมีหลายยี่ห้อเช่น RISC-V,AVR,x86,ARM
![hifiveunleashedangled_1_jpg_open_graph](https://user-images.githubusercontent.com/98943488/161917868-e1cdb5a3-c288-437f-8567-00ac3c2a578b.jpg)
### ตัวอย่าง processor จาก RISC-V


## 2.ภาษาแอสเซ็มบลี้ (low level language, assembly)
### คือภาษาที่ทำงานโดยขึ้นกับรุ่นของ processor  โดยภาษา assembly เป็นภาษาระดับต่ำและในแต่ละยี่ห้อนั้นก็จะมีภาษา assembly ที่แตกต่างกัน
![Screenshot 2022-04-06 141841](https://user-images.githubusercontent.com/98943488/161917842-407f2df2-24ab-47c2-a1ae-dba3f02e505e.png)
### ตัวอย่างภาษาassembly จาก RISC-V 


## 3.ภาษาเครื่อง (machine language)
### คือภาษาassembly นั้นคอมพิวเตอร์ยังไม่สามารถเข้าใจได้จึงต้องแปลงเป็นโค้ดที่เป็น Binary ก่อนและในแต่ละยี่ห้อนั้นก็จะมีภาษาเครื่องที่แตกต่างกัน
![img10](https://user-images.githubusercontent.com/98943488/161917898-6ba2f34a-95df-4356-be6d-00d245131252.png)


## 4.ภาษาชั้นสูง (high level language)
### เนื่องจากภาษาassembly,ภาษาเครื่อง มีความละเอียดมากทำให้ใช้เวลาในการเขียนโค้ดเป็นเวลานานจึงใช้ภาษาชั้นสูง เช่น c,c++,java,python เพื่อสามารถเขียนโปรแกรมให้กระชับและเขียนโค้ดได้เร็วขึ้น
![programming-languages-to-learn-in-2015](https://user-images.githubusercontent.com/98943488/161917882-ea22c46a-10a0-47f3-a767-36d8579088f1.png)




# ตัวอย่างการเขียนโปรแกรมจากภาษาชั้นสูงมาเป็นภาษาassemblyและแปลมาเป็นภาษาเครื่อง
![Screenshot 2022-04-06 142435](https://user-images.githubusercontent.com/98943488/161919553-52c5eb37-a86c-45e0-b50b-8bbd940627b8.png)
![Screenshot 2022-04-06 142547](https://user-images.githubusercontent.com/98943488/161919564-85a79814-9aff-417e-8fcc-36418ea84587.png)
![Screenshot 2022-04-06 142609](https://user-images.githubusercontent.com/98943488/161919582-354562e6-acd5-471b-b8ab-3d146f149414.png)
![Screenshot 2022-04-06 142704](https://user-images.githubusercontent.com/98943488/161919589-35a35f4f-399a-4a91-9e84-95952c588289.png)
### จากตัวอย่างข้างต้นจะสังเกตเห็นว่าโปรแกรมทางด้านซ้ายคือการเขียนโปรแกรมจากภาษาชั้นสูงซึ่งมีความสั้นกะทัดรัดและสามารถเข้าใจได้ง่ายเมื่อมาเปรียบเทียบกับด้านซ้ายคือภาษา assembly และภาษาเครื่องจะสังเกตเห็นว่ามีความละเอียดมากและใช้เวลาในการเขียนโปรแกรมเป็นเวลานาน จึงทำให้คนส่วนใหญ่มักจะเขียนภาษาชั้นสูงและให้แปลเป็นภาษา assembly และแปลเป็นภาษาเครื่องเพื่อให้คอมพิวเตอร์เข้าใจ
