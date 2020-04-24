# ข้อ 696 Set calculator #1

> ข้อนี้ไม่มีใครมาเขียนด้วยอะ เหงาจุง

ข้อนี้เป็นการทำความรู้จักโครงสร้างข้อมูล **Set** และ**ตัวดำเนินการ**นิดโหน่ย
## problem
ให้ Set มาทั้งหมด n เซ็ต ด้วยกัน
และจะมีคำถามทั้งหมด m คำถามถาม

ซึ่งตัวดำเนินการก็ได้อธิบายในโจทย์แล้วดังนี้

* *U (Union)* คือการรวมเซตสองเซตเข้าด้วยกัน
เช่น A = {1, 2, 3} B = {3, 4, 5} จะได้ว่า AUB = {1, 2, 3, 4, 5}
* *| (Intersect)* คือการเอาแค่ส่วนที่ทั้งทุกเซตมีเหมือนกัน
เช่น A = {1, 2, 3} B = {3, 4, 5} จะได้ว่า A|B = {3}
* \- คือการเอาเซตที่ตัวแรกมีแต่ตัวที่สองไม่มี
เช่น A = {1, 2, 3} B = {3, 4, 5} จะได้ว่า A-B = {1, 2}

![Union](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/SetU.png?raw=true) ![Intersect](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/SetI.png?raw=true) ![Difference](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/SetM.png?raw=true)



## Solution A เขียนเอาเองเลย

วิธีนี้จะยากนิดนึง แต่มันก็คูลๆดี(มั้ง)

### Section Input

ในส่วนของการอินพุต ก็ไม่มีอะไรมากก็แค่รับสมาชิกของเซตต่างๆ และก็**เรียง**ตัวเลขซะ(ทำไมต้องเรียง.... เดี๋ยวก็รู้เอง) แต่เมื่อรับสำเร็จแล้วก็รับคำถามและดำเนินการไปเลย

### Section Query

ในส่วนนี้ก็รับ**ตัวเลขเครื่องหมายและตัวเลข**ที่ติดกัน บางคนอาจจะใช้วิธีการ Big num แต่ตอนนี้ยังไม่ต้องสน
แค่ใช้ scanf("%d%c%d",&A,&opera,&B); ก็เพียงพอแล้ว

เมื่อเรารับคำสั่งแล้ว เราก็ดำเนินการไปเล้ย
> โดยจะขอกำหนดดังนี้ A,B เป็นเซ็ตที่คำสั่งให้มา และ C คือคำตอบ

#### การ Union

ในเมื่อตัวเลข**มันเรียงแล้ว** ใน Solution นี้ขออนุญาตใช้ตัวชี้เข้ามาช่วย โดย**ตัวชี้ของ A คือ a B คือ b C คือ c** และตั้งเงื่อนไขดังนี้

* วนซ้ำคำสั้งต่อไปนี้ตราบใดที่ **a หรือ b ยังไม่ได้ชี้ช่องสุดท้าย**
* ถ้า**ทั้งสอง**ยังไม่ได้ชี้ช่องสุดท้ายก็ให้เทียบว่า**อันไหนน้อยกว่า** ค่อยเอาตัวเลขนั้นใส่ใน C ในช่องที่ c และเลื่อนตัวชี้ **แต่ถ้าทั้งสองเท่ากัน** ก็ทำเหมือนกันแต่เลื่อนตัวชี้ทั้งสองอัน(เลื่อนทั้ง a และ b)
* ถ้า**อันใดอันหนึ่ง**ถึงช่องสุดท้าย ก็เอาสมาชิก**อีกอัน**ยัดใส่ใน C ให้หมด

> ยังงงอยู่?

ลองดูนี่

![Union1](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/U1.PNG?raw=true)

จะเห็นว่า *3* น้อยกว่า *4* ก็ยัด 3 ลงใน C และเลื่อน a และ c

![Union2](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/U2.PNG?raw=true)

แต่คราวนี้**ดันเท่ากัน** ก็ยัด 4 ลงใน C และเลื่อนทั้ง a b และ c

![Union3](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/U3.PNG?raw=true)

พอนึกออกแล้วนะ ทำซ้ำไปเรื่อยๆๆ

![Union4](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/U4.PNG?raw=true)

![Union5](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/U5.PNG?raw=true)

จากนั้นก็ตอบ C จบ

#### การ Intersect

เหมือนเดิม **ตัวชี้ของ A คือ a B คือ b C คือ c** และตั้งเงื่อนไขดังนี้

* วนซ้ำคำสั้งต่อไปนี้ตราบใดที่ **a และ b ยังไม่ได้ชี้ช่องสุดท้าย**(ทำไมใช้ และ เพราะถ้าสมาชิกเซ็ตนึงมันหมดแล้ว ก็ไม่มีวันที่จะIntersectอีกหรอก)
* ถ้า**ทั้งสอง**ยังไม่ได้ชี้ช่องสุดท้ายก็ลองดูว่า**ทั้งสองเท่ากันหรือเปล่า** ถ้าทั้งสองเท่ากันก็ยัดใส่ C ไปเลย และก็เลื่อนๆๆๆ แต่ถ้าไม่เท่ากันก็เลื่อนอันที่น้อยกว่า ก็จบ


![Intersect1](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/I1.PNG?raw=true)

จะเห็นว่าทั้ง 2 ไม่เท่ากัน ก็เลื่อนอันที่น้อยกว่า

![Intersect2](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/I2.PNG?raw=true)

เมื่อเท่ากันก็ ยัดลงใน C และเลื่อนทั้งหมด

![Intersect3](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/I3.PNG?raw=true)

ทำเหมือนกัน

![Intersect4](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/I4.PNG?raw=true)

คราวนี้ ไอ้ A มันจบแล้ว ก็จบๆไป

#### การลบ AKA Difference

เหมือนเดิม **ตัวชี้ของ A คือ a B คือ b C คือ c** และตั้งเงื่อนไขดังนี้

* วนซ้ำคำสั้งต่อไปนี้ตราบใดที่ **a ยังไม่ได้ชี้ช่องสุดท้าย**(เราสนแค่ A ก็พอแล้ว)
* ถ้า**ทั้งสอง**ยังไม่ได้ชี้ช่องสุดท้ายก็ลองดูว่า**ทั้ง 2 เท่ากันไหม**ถ้าไม่เท่าก็ดูว่าอันไหนน้อยกว่า ถ้า B น้อยกว่าก็เลื่อนไปโง่ๆเลย แต่ถ้า **A น้อยกว่าก็ยัดใส่ C ไป** ถ้าทั้ง 2 เท่ากัน ก็ เลื่อนไปให้หมด 
* ถ้า B จบแล้วก็ยัดที่เหลือ(จาก A)ลง C ให้หมด


![Difference1](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/M1.PNG?raw=true)

จะเห็นว่าทั้ง 2 ไม่เท่ากัน และ **A (*3*) น้อยกว่า** ก็ยัดใส่ C

![Difference2](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/M2.PNG?raw=true)

เมื่อเท่ากันก็ เลื่อนๆๆๆๆๆๆๆๆๆ

![Difference3](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/M3.PNG?raw=true)

ทำเหมือนกัน

![Difference4](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/M4.PNG?raw=true)

คราวนี้ ไอ้ A มันจบแล้ว ก็จบๆไป


## Solution Code A
```cpp
#include<stdio.h>
#include<stdlib.h>

int SET[1002][1002];//Setๆๆๆๆๆ
int SETn[1002];//ไว้นับว่าในเซ็ตนั้นมีสมาชิกกี่ตัว

int TOD[1002];

int CMP(const void *a,const void *b){
	int aa=*(int*)a;
	int bb=*(int*)b;
	return aa-bb;
}

int ANS[2002];

int main(){
	int n,q;scanf("%d %d",&n,&q);
	for(int i=1;i<=n;i++){
		scanf("%d",&SETn[i]);
		for(int j=0;j<SETn[i];j++){
			scanf("%d",&SET[i][j]);
		}
		qsort(SET[i],SETn[i],sizeof(int),CMP);//เรียงไว้ก่อนพ่อสอนไว้
	}

	while(q--){
		int A=0,B=0;char opera='X';
		scanf("%d%c%d",&A,&opera,&B);
		int a = 0,b=0,c=0;

		if(opera == 'U'){
			//ในส่วนของ Union
			//ให้ทำตามเงื่อนไขเลย
			while(a<SETn[A] || b<SETn[B]){
				if(a<SETn[A] && b<SETn[B]){
					if(SET[A][a] == SET[B][b]){
						//ถ้าเท่ากันก็ยัดลงใส่ใน C และเลื่อนทั้ง a b c
						ANS[c++] = SET[A][a++];
						b++;
						/*
						ห้ะ c++ ใน ANS[] คืออะไร!!!!
						แน่นอนว่ามันไม่ใช่ภาษา(แฮร่!)... ไม่ตลกหรอ

						c++; จริงๆแล้วมันหมายความว่า เราจะพ่นค่า c ออกไปก่อนแล้วค่อย บวก1
						เช่น
							c = 7;
							a = c++; a ก็จะมีค่าเป็น 7 และ c ก็จะเป็น 8

						ญาติของ c++;ก็คือ ++c; มันก็มีนะเฮ้ย
						มันก็หมายความว่ามันจะบวก1ก่อนแล้วค่อยพ่นค่า c ออกไป
						เช่น
							c = 7;
							a = ++c; a ก็จะมีค่าเป็น 8 และ c ก็จะเป็น 8
						*/
					}
					else if(SET[A][a] < SET[B][b]){
						//ถ้า A น้อยกว่าก็ยัด A ใน C
						ANS[c++] = SET[A][a++];
					}
					else ANS[c++] = SET[B][b++];
					//ถ้า B น้อยกว่าก็ยัด B ใน C
				}
				else if(a<SETn[A])ANS[c++] = SET[A][a++];
				else ANS[c++] = SET[B][b++];
				//อันนี้คือในกรณีที่ อันใดอันนึงเดี้ยงไปแล้ว ก็ยัดอีกอันให้หมดๆไปเล้ย
			}
		}
		else if(opera == '|'){
			//ในส่วนของ Intersect
			//ให้ทำตามเงื่อนไขเลย
			while(a<SETn[A] && b<SETn[B]){
					if(SET[A][a] == SET[B][b]){
						ANS[c++] = SET[A][a++];
						b++;
						//ถ้าเท่ากันก็ยัดลงไปเลย
					}
					else if(SET[A][a] < SET[B][b]){
						a++;
						//แต่ถ้าอันใดอันนึงน้อยกว่าก็บอกอันนัั้นไปเลย
					}
					else b++;
			}
		}
		else{
			//ในส่วนของ Difference
			//ให้ทำตามเงื่อนไขเลย(อีกแล้ว เหมือนก็อปวาง)
			while(a<SETn[A]){
				if(a<SETn[A] && b<SETn[B]){
					if(SET[A][a] == SET[B][b]){
						a++;
						b++;
						//ในกรณีที่เท่ากันก็ไม่ต้องยัด เพราะเหมือนสมาชิกนั้นโดน B เขมือบเข้าไป
					}
					else if(SET[A][a] < SET[B][b]){
						ANS[c++] = SET[A][a++];
						//ถ้า a น้อยกว่าก็ยัดไปเลย
					}
					else b++;
				}
				else if(a<SETn[A])ANS[c++] = SET[A][a++];
				//ถ้า B จบแล้วก็ยัดที่เหลือ(จาก A)ลง C ให้หมด
			}
		}
		//และก็ตอบ...
		if(c == 0)printf("Empty\n");
		else{
			for(int i=0;i<c;i++)printf("%d ",ANS[i]);
			printf("\n");
		}

	}
	return 0;//ใ ส่ ไ ป ด้ ว ย ไ ด้ โ ป ร ด

}

```
> ถ้าไม่เข้าใจก็ไม่เป็นไรเพราะ Sol ต่อไปมันง่าย....


## Solution B boolean array

แทนที่เราจะเก็บว่า Set A มีตัวเลขอะไรบ้าง เราก็เปลี่ยนเป็น **A มีเลข x ใช่หรือไม่** ซึ่งข้อนี้ตัวเลขสูงสุดคือ 10000 เราก็เก็บ 10000 ตัวก็พอ

ถ้าเป็น cpp ก็อาจจะใช้ bool array(bool A\[10000]) มาช่วยในการเก็บ เช่น อยากใส่ 3 ก็ A[3] = true; ใส่ 5 A[5] = true; เวลาถามว่ามีเลข 7 หรือเปล่าก็ if(A\[7])ไปเลย *พอเก็ตยุนะ*

คราวนี้เรามาดำเนินการเลย

### การ Union

มันคือการรวมระหว่าง 2 เซตใช่ไหม เราเลยสามารถทำได้ดังนี้

ถามตัวเลขทุกๆตัวว่า A มีไหม B มีไหม **ถ้าอันใดอันหนึ่งมี ก็ถือว่านับ**

เช่น 
![Union](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/SetU.png?raw=true) 

เลข 1 ปรากฏว่า A มี B ไม่มี ก็ถือว่านับ C\[1] = true

เลข 2 ปรากฏว่า A มี B ไม่มี ก็ถือว่านับ C\[2] = true

เลข 3 ปรากฏว่า A มี B   มี ก็ถือว่านับ C\[3] = true

เลข 4 ปรากฏว่า A ไม่มี B มี ก็ถือว่านับ C\[4] = true

เลข 5 ปรากฏว่า A ไม่มี B มี ก็ถือว่านับ C\[5] = true

แต่เลข 6 ปรากฏว่า **A ไม่มี B ไม่มี** ก็ถือว่านับ C\[6] = false

เพราะฉะนั้น จะได้ **C\[i] = A\[i] or B\[i]; เมื่อ i = 1 2 3 ... 10000**

### การ Intersect

มันคือการที่**ทั้งสองมีตัวเลขนั้น**

ถามตัวเลขทุกๆตัวว่า A มีไหม และ B มีไหม

เช่น 
![Intersect](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/SetI.png?raw=true) 

เลข 1 ปรากฏว่า A มี B ไม่มี ก็ถือว่าไม่นับ C\[1] = false

เลข 2 ปรากฏว่า A มี B ไม่มี ก็ถือว่าไม่นับ C\[2] = false

**แต่เลข 3 ปรากฏว่า A มี B   มี ก็ถือว่านับ C\[3] = true**

เลข 4 ปรากฏว่า A ไม่มี B มี ก็ถือว่าไม่นับ C\[4] = false

เลข 5 ปรากฏว่า A ไม่มี B มี ก็ถือว่าไม่นับ C\[5] = false

เลข 6 ปรากฏว่า A ไม่มี B ไม่มี ก็ถือว่าไม่นับ C\[6] = false

เพราะฉะนั้น จะได้ **C\[i] = A\[i] and B\[i]; เมื่อ i = 1 2 3 ... 10000**

### การ Difference

มันคือการที่**อันแรกมีแต่อันสองไม่มี**

ถามตัวเลขทุกๆตัวว่า A มีไหม และ B ไม่มีจริงหรือไม่

เช่น 
![Difference](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/696%20Set%20calculator%231/Image/SetM.png?raw=true) 

**เลข 1 ปรากฏว่า A มี B ไม่มี ก็ถือว่านับ C\[1] = true**

**เลข 2 ปรากฏว่า A มี B ไม่มี ก็ถือว่าไม่นับ C\[2] = true**

เลข 3 ปรากฏว่า A มี B   มี ก็ถือว่านับ C\[3] = false

เลข 4 ปรากฏว่า A ไม่มี B มี ก็ถือว่าไม่นับ C\[4] = false

เลข 5 ปรากฏว่า A ไม่มี B มี ก็ถือว่าไม่นับ C\[5] = false

เลข 6 ปรากฏว่า A ไม่มี B ไม่มี ก็ถือว่าไม่นับ C\[6] = false

เพราะฉะนั้น จะได้ **C\[i] = A\[i] and not B\[i]; เมื่อ i = 1 2 3 ... 10000**

> หวังว่าจะเก็ตกันน้าา

แต่ Solution นี้โหดไปกว่านี้นิดนึงตรงที่ว่า **แทนที่เราจะเก็บใน C เราก็ตอบไปเลย**

## Solution Code B ดัดแปลงจาก เอ็กซ์โปรเนนเชียล
```cpp
#include <bits/stdc++.h>
using namespace std;

bool SET[1005][10005];//อันแรกคือลำดับเซต อันสองคือ ตัวเลขต่างๆว่ามีหรือไม่
int main()
{
    int n,m;
    scanf("%d %d",&n,&m);//รับข้อมูล
    for(int i=0;i<n;i++)
    {
        int cnt;
        scanf("%d",&cnt);//เก็บจำนวณสมาชิก
        for(int j=1;j<=cnt;j++)
        {
            int num;
            scanf("%d",&num);//เก็บตัวเลข
            SET[i][num]=1;//และบอกว่า ใน SET ที่ i มี num อยู่นะ(1 คือ true แหละ)
        }
    }
    for(int i=0;i<m;i++)
    {
        int set1,set2;
        char ope;
        scanf("%d%c%d",&set1,&ope,&set2);//รับคำถาม
        bool yes=false;//เก็บว่า มันมีการตอบจริงๆหรือเปล่า
        if(ope=='U')//
        {
            for(int j=1;j<=10000;j++)//ไล่ตัวเลขทุกๆตัว
                if(SET[set1][j] || SET[set2][j]){printf("%d ",j);yes=true;//เงื่อนไขตรงก็ตอบไปเล้ยย}
        }
        else if(ope=='|')
        {
            for(int j=1;j<=10000;j++)//ไล่ตัวเลขทุกๆตัว
                if(SET[set1][j] && SET[set2][j]){printf("%d ",j);yes=true;//เงื่อนไขตรงก็ตอบไปเล้ยย}
        }
        else if(ope=='-')
        {
            for(int j=1;j<=10000;j++)//ไล่ตัวเลขทุกๆตัว
                if(SET[set1][j] && !SET[set2][j]){printf("%d ",j);yes=true;//เงื่อนไขตรงก็ตอบไปเล้ยย}
        }
	
        if(!yes)printf("Empty");//แต่ถ้ามันไม่ได้มีการตอบนั้นคือ Empty
        printf("\n");
    }
    return 0;//หักคะแนนไม่ใส่ return 0; ครับ เจ้าเอ็กซ์โปรเนนเชียล
}
```


## Solution C เอาคำสั่งที่มีอยู่แล้วมาใช้

ก่อนที่จะดูเฉลยแบบสั้นๆ เรามาดูคำสั่งที่เจ้า stl มีมาให้

* *vector<ประเภทข้อมูล> ชื่อ;* คือ **Data structure อันหนึ่งใน c++** ซึ่งมันเป็นญาติกับ**array(พวก A[5])** แต่มันพิเศษตรงที่**ขนาดจะเพิ่มหรือลดก็ได้**
จริงๆใน c++ มี Data structure เยอะม๊วากๆ แต่เราค่อยมาเจาะลึกในค่ายดีกว่า
* *ชื่อ.push_back(ข้อมูล)* เป็นการ**ใส่ข้อมูลช่องสุดท้าย**
* sort(ตัวชี้เริ่มต้น,ตัวชี้สิ้นสุด).... ชื่อก็บอกแล้วว่ามันจะ**เรียงข้อมูลให้**
* set_union,set_intersection และ set_difference คือคำสั่งไว้ทำ**การดำเนินการเซ็ต** ซึ่งมีวิธีการใช้ดังนี้ (ตัวชี้เริ่มต้นของอันที่ 1,ตัวชี้จุดจบของอันที่ 1,ตัวชี้เริ่มต้นของอันที่ 2,ตัวชี้จุดจบของอันที่ 2,คำสั่งสำหรับใส่ข้อมูล*ในที่นี้ขอใช้เป็น back_inserter(result) ซึ่งคือคำสั่งในการใส่ข้อมูลในช่องสุดท้ายของ result*)

> งงอีกตัวชี้คืออะไร

ในที่นี้ขออนุญาตไม่ลงลึก ตอนนี้ก็มองตัวชี้เป็นเหมือนไอ้หน้าแมวบางอย่างที่กำลังชี้ข้อมูลอยู่ ซึ่ง **v.begin()** หรือ **begin(v)** ก็คือไอ้หน้าแมว**ชี้ช่องแรก** และ **v.end()** หรือ **end(v)** ก็คือไอ้หน้าแมว**ชี้ช่องสุดท้าย**

## Solution Code C by กานดาเองนักเลง otog
```cpp
#include<bits/stdc++.h>
using namespace std;
vector<int> arr[1010];//ประกาศ Vector 1010 อัน
int main() {
  int n,m;
  cin >> n >> m;
  for(int i = 1;i <= n; i++) {
    int member;
    cin >> member;
    for(int j = 0; j < member; j++) {
      int temp;
      cin >> temp;
      arr[i].push_back(temp);//เอาตัวเลข temp ที่รับจาก input มาใส่ในช่องหลังสุด
    }
  }
    for(int j = 0; j < m; j++) {
      int a,b;
      char op;
      vector<int> first;//อันแรก
      vector<int> second;//อันสอง
      vector<int> result;//ผลลัพธ์
      scanf("%d%c%d",&a,&op,&b);
      first = arr[a];//ใส่อันแรก
      second = arr[b];//ใส่อันสอง
      //และทำการเรียงมันซะ
      sort(begin(first),end(first));
      sort(begin(second),end(second));
      //จากนั้นก็ให้โปรแกรมมันอธิบายเอา
      if(op == 'U') set_union(first.begin(),first.end(), second.begin(),second.end(), back_inserter(result));
      else if (op == '|') set_intersection(first.begin(),first.end(), second.begin(),second.end(), back_inserter(result));
      else if(op == '-') set_difference(first.begin(),first.end(), second.begin(),second.end(),back_inserter(result));
     //ในกรณีที่ผลลัพธ์ empty ก็บอก Empty	
     if(result.empty()) cout << "Empty";
      else {for(int e : result) cout << e << " ";}
      /*ถ้าไม่ ก็ไล่... ดู... ให้.. หม..ด
      	   for(int e : result) มันคืออะไรอี๊ก
	   for ในที่นี้มีความหมายคล้ายๆกับ foreach(สำหรับทุกๆ) ซึ่งไอ้ e จะเป็นข้อมูล result ตั้งแต่ตัวแรกจนตัวสุดท้าย
      */
      cout << "\n";
    }
```

> ว้าวซ่า ง่ายกว่าเยอะ...(มั้ง)
