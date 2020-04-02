# ข้อ 685 Pattern_วงกลม
/!\\ ขอบอกก่อนครับว่าข้อนี้**มีหลายคำตอบ** /!\\
## Problem
ตามนั้นแหละ ให้ตัวเลขมาแล้วสร้างวงกลม
> แต่เดี๋ยวก่อน เราจะสร้างวงกลมยังไงดีทั้งๆที่หน้าต่างเป็น สี่เหลี่ยมเหมือน minecraft
## Solution
อย่างไรก็ตาม เรากลับมาที่คำถามว่า **อะไรคือวงกลม**

วงกลมคือ จุดต่างๆที่**ห่างจากจุดศูนย์กลางในระยะที่เท่าๆกัน**ซึ่งเราจะเรียกอีระยะนั้นคือ รัศมี

กลับมาที่โจทย์ของเรา ถ้าสังเกตนิดนึงจะเห็นว่า วงกลมนั้นมีรัศมีเป็น (n-1)/2 หรือในภาษาซีก็คือ n/2 ไปเลย

> แล้วสรุปทำยังไง

เราก็ไล่ดูทุกๆจุด(ทุกๆตำแหน่งในหน้าจอ) และ เอาคำนิยามมากลับหลัง ซึ่งจะได้เป็นคำว่า *จุดต่างๆที่ห่างจากจุดศูนย์กลางในระยะที่เท่าๆกัน* นั้นคือ **วงกลม** 
ซึ่งเราสามารถหาระยะห่างโดยการ ![สมการหาระยะห่าง](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EA.PNG?raw=true) *ในที่นี้ขอไม่ใส่ sqrt จะได้คำนวณง่ายๆและเป็นจำนวนเต็มด้วย*

หรือเราใช้สมการวงกลมจากภาคตัดกรวยก็ได้

![สมการภาคตัดกรวย](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EB.PNG?raw=true)

*ส่วนสมการมายังไง ก็ลองหาใน Internet ได้ ในที่นี้ขอไม่พิสูจน์น้าา*

ก็จะได้วงกลมแล้ว........มั้ง

![รูปวงกลมที่กำลังจะเป็นวงกลม](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/A.PNG?raw=true)

> มันไม่วงกลมเลย

เพราะความที่หน้าต่างก็เป็นสี่เหลี่ยม เลยทำให้วงกลมมันขาดๆตอนๆ

ถ้าเราลากวงกลมผ่านอีตัวเลขนั้นๆ เราจะสังเกตเห็นได้ว่าไอ้วงกลมที่เราลากผ่าน **ไอ้ตัวเลขนั้นใกล้กับ 25 อยู่**

![รูปวงกลมที่เป็นวงกลม](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/B.PNG?raw=true)

ดังนั้น แทนที่เราจะเช็คแค่ว่า ![สมการภาคตัดกรวย](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EC.PNG?raw=true) เราก็ดูว่า ![สมการภาคตัดกรวย2](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/ED.PNG?raw=true) มันใกล้เคียงกับ ![r^2](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EE.PNG?raw=true) หรือไม่

*จริงๆเราสามารถมองเป็นอีกแบบก็ได้คือ วาดวงกลมสองอันซ้อนกัน แล้วถ้าอีจุดนั้นอยู่ในระหว่างวงกลม 2 อันนั้น ก็ถือว่าจุดนั้นก็เป็นวงกลม*

ไอ้ความ**ใกล้เคียง**แหละเลยทำให้**ข้อนี้มีหลายคำตอบ** ดังนั้นหาก Sol ใครมาถึงตรงนี้(ได้ 60 80 คะแนนกัน) ก็ถือว่าผ่านแล้ว

โดยในที่นี้ขอใช้สมการคือ ![สมการภาคตัดกรวย3](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EF.PNG?raw=true) *ก็คือถ้าเราคำนวณได้ระหว่าง ![สมการภาคตัดกรวย3-](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EG.PNG?raw=true) ถึง ![สมการภาคตัดกรวย3+](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EH.PNG?raw=true)


ซึ่งสามารถเขียนในรูป Abs ได้คือ ![สมการสุดท้าย](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/17-%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A3%E0%B8%AD%E0%B8%81%20%E0%B8%99%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%94%E0%B9%89/685%20Pattern_%E0%B8%A7%E0%B8%87%E0%B8%81%E0%B8%A5%E0%B8%A1/ImageStuff/EI.PNG?raw=true)

## Solution Code
```c
#include<stdio.h>

int ABS(int a){//คำสั่งหาค่าสัมบูรณ์
	if (a<0) return a*(-1);//ถ้ามันติดลบก็ทำให้มันเป็นบวกซะ
	else return a;
}

int main(){

	int n;scanf("%d",&n);
	int r = (n-1)/2;//รัศมี จริง n/2 ก็เพียงพอแล้วอิอิ

	for(int i=0;i<n;i++){
		for(int j=0;j<n;j++){//ไล่ดูทุกตำแหน่ง

			int DX = j-r;//ผลต่าง x
			int DY = i-r;//ผลต่าง y


			if ((ABS((DX*DX+DY*DY)-r*r))<=r){//ตามสมการเลย
				printf("#");
			}
			else printf("-");


		}
		printf("\n");
	}
	return 0;

}

```

อย่างที่บอกครับ ข้อนี้มีหลายวืธีครับ ดังนั้นอย่าโกรธกันน้าาา

*HAPPY APRIL FOOL DAY*
