## ข้อ 154 Problem G. Range Sum Query
### Problem
ถ้าแปลโจทย์ไม่ออก เดี๋ยวจะแปลให้ฟัง

โจทย์ประมาณว่าให้ตัวทดสอบ **t** อัน (1 <= t <= 5)
แต่ละอันจะมีตัวเลข **n** ตัวเลขและจะถาม **q** คำถาม (1 <= n,q <= 100,000)
โดยตัวเลขนั้นจะเป็นจำนวนเต็มที่ไม่ติดลบ

ส่วนคำถาม จะรับตัวเลข 2 ตัวก็คือ **i,j** (1 <= n,q <= 10,000)

หน้าที่ของคุณคือ **การที่หาผลรวมตั้งแต่ ตัวที่ i จนถึง j**

### Solution A
วิธีนี้จะเป็นตรงๆไปเลยก็คือ
1. รับตัวเลขมา n ตัว
2. รับคำถามมา(รับ i,j แหละ)
3. ในแต่ละคำถามก็วนตรงๆ(วนตั้งแต่ i ถึง j)และบวกเข้าไป
4. ตอบ

>ฟังดูง่ายๆข้อนี้ แต่หารู้ไม่ว่า วิธีนี้เป็นวิธีที่**ช้า**
>เพราะ คิดง่ายๆ สมมติเคสที่แย่ที่สุดก็คือ มี 5 เทส 100000 คำถาม และหาผลรวมตั้งแต่ 0 ถึง 10000 ทุกครั้ง
>ก็จะได้เวลาทำง่ายที่คิดง่ายๆคือ 5\*100000\*10000 = 5000000000(5 พันล้าน)ในขณะที่แบบดีที่สุดคือการคำนวณ 2 พันล้านใน 1 วินาที(แปลว่าใช้เวลา 2.5 วินาทีโดยประมาณ)


### Solution B
วิธีนี้จะใช้หลักของคณิตศาสตร์หน่อยๆ
ซึ่ง เราจะมาเรียนรู้ไปด้วยกัน

คำสั่งแรก ให้หาผลรวมของ 1+2+3+...+30
ซึ่งมันก็คือ 
![Image](https://github.com/Nepumi/-Otog-15-Back-to-the-OTOG-Warm-Up-Contest/blob/master/RES/B.PNG?raw=true) แหละ

แต่ถ้าอยากหาผลรวมของ 10+11+12+...+30 โดยที่ ![Image](https://github.com/Nepumi/-Otog-15-Back-to-the-OTOG-Warm-Up-Contest/blob/master/RES/C.PNG?raw=true) x ต้องเริ่มที่ 1 เท่านั้น จะทำยัง

สิ่งที่ทำได้ก็คือการที่นำ ![Image](https://github.com/Nepumi/-Otog-15-Back-to-the-OTOG-Warm-Up-Contest/blob/master/RES/D.PNG?raw=true)

งงละสิ ดูรูปนี้จะช่วยให้ดีขึ้น

![Image](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/15-Back%20to%20the%20OTOG%20Warm%20up%20contest/IMAGE/A.PNG?raw=true)

หรือก็คือ ผลรวมตั้งแต่ i,j ได้โดยการ 
![Image](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/15-Back%20to%20the%20OTOG%20Warm%20up%20contest/IMAGE/E.PNG?raw=true)

แค่นี้แหละ เราจะเปลี่ยนจาก
![Image](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/15-Back%20to%20the%20OTOG%20Warm%20up%20contest/IMAGE/F.PNG?raw=true)
เป็น
![Image](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/15-Back%20to%20the%20OTOG%20Warm%20up%20contest/IMAGE/G.PNG?raw=true)
ในที่นี้ขอเรียก**ผลรวมตั้งแต่ 1 ถึง i ว่า** ``` PF[i] ```

ดังนั้น หากต้องการผลรวมตั้งแต่ i ถึง j ก็คือ ``` PF[j] - PF[i-1] ```

>เว้นแต่ว่า หาก i = 1 คำตอบก็คือ ``` PF[j] ``` ทันที

เราขอเรียกวิธีนี้ว่า **Qsum** หรือทางการจะเรียกว่า **Prefix** นั้นเอง  

![Image](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/15-Back%20to%20the%20OTOG%20Warm%20up%20contest/IMAGE/H.PNG?raw=true)

#### มาสร้าง Prefix(PF) กัน
1. กำหนดให้ PF[0] = L[0]
2. ให้ PF[i] = PF[i-1] + L[i] โดยที่ i ไล่จาก 1 ถึง n-1
>PF[i] = PF[i-1] + L[i] หมายความว่า ผลรวมที่ i = มีค่าเท่ากับผลรวมที่ i-1 + ตัวเลขปัจจุบัน

### Code Solution B

```c
#include<stdio.h>

long long PF[100002];/*Prefix ถามว่าทำไมใช้ long long
เพราะว่าตัวเลขมีทั้งหมด 100000 ตัว สูงสุดอยู่ที่ 1000000 หากเอามารวมกันทั้งหมด
ก็จะได้ 1แสนล้าน ในขณะที่ int เก็บได้สูงสุดที่ 2 พันล้าน
*/
int L[100002];//L for Lek :)

int n,q;//ขอประกาศ n,q ไว้นอก main() เพื่อที่จะสามารถเรียกใช้จากไหนก็ได้

void Make_PF(){//คำสั่งในการสร้าง PF

	PF[0] = L[0];
	for(int i=1;i<n;i++)PF[i] =(long long)(PF[i-1] + L[i]);

}

long long Sum_Range(int i,int j){//คำสั่งในการหาผลรวมตั้งแต่ i ถึง j
	if (i==0){
		return PF[j];
	}
	else{
		return PF[j]-PF[i-1];
	}
	//ไม่งงเนอะ
}

int main(){

	int t;scanf("%d",&t);
	while(t--){//วนไปจนครบ t ครั้ง
		scanf("%d %d",&n,&q);
		for(int i=0;i<n;i++)scanf("%d",&L[i]);//รับค่า n ตัว
		Make_PF();//มาสร้าง PF กันนน
		while(q--){
			int i,j;scanf("%d %d",&i,&j);
			printf("%lld\n",Sum_Range(i,j));
		}
		printf("\n");
	}

	return 0;//ใส่ไว้ไม่ทำให้แมวระเบิดหรอก

}

```
