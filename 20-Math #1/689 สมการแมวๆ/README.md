# ข้อ 689 สมการแมวๆ
> ข้อนี้เป็นข้อนึงที่ โปรแกรมเขียนไม่ยาก แต่คิดยากๆๆ
## Problem
ตามนั้นแหละ ให้สมการแมวๆมา กำหนดค่า x แล้วหาผลลัพธ์ y

แต่ความยากของข้อนี้คือ มีการ Input ที่สูงมากๆ การใช้ POW(10,ล้านกว่าๆ) ย่อมทำให้**โลกถึงกาลอวสาน**ได้ ซึ่งแน่นอนว่าขนาด **double ยังไม่รอด แล้วจะหวังอะไรกับ unsigned long long**

ฉะนั้น ข้อนี้ต้องมีอะไรซ่อนอยู่แน่ๆ

## Solution A(70 คะแนน)

> Solution นี้มาจากน้อง X (ไม่ได้ระบุนาม)

ด้วยความที่มีการ Input/Output ที่สูงมากๆ เลยมีการใช้บางสิ่งที่เข้ามาช่วยก็คือ **BigInt** *(AKA. BigNum)* ซึ่งมันคืออะไร๊??? ลองดูข้อ [**698 Lucky Lotto**](https://github.com/Nepumi/OTOG-Editorial-2020/tree/master/20-Math%20%231/698%20Lucky%20Lotto#problem-b-%E0%B9%81%E0%B8%A5%E0%B9%89%E0%B8%A7%E0%B8%97%E0%B8%B3%E0%B9%84%E0%B8%A1%E0%B8%A1%E0%B8%B1%E0%B8%99%E0%B8%A2%E0%B8%B1%E0%B8%87%E0%B8%9A%E0%B8%B6%E0%B9%89%E0%B8%A1%E0%B8%AD%E0%B8%B0)ก่อนก็ได้ เพราะข้อนั้นมีการใช้ Bignum

แต่อย่างไรก็ตาม ด้วยความที่ไอ้แมวตัวนี้**มันโหดเกินไป การใช้ Bignum ก็เลยยังไม่สามารถผ่านได้** แต่เราสามารถนำอี Bignum มา**ใช้ประโยชน์ได้อีกอยู่....**

## Solution B
ข้อนี้สามารถเข้าถึง Solution ได้ 2 วิธี(หรืออาจจะมีมากกว่านั้นก็ได้)

### เข้าถึง Solution B วิธีที่ 1 : Observation

จากสมการ

![สมการแมวๆ](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/A.PNG?raw=true)

ถ้าเราลองแทน x = 0,1,2,3 เราจะเห็นอะไรบางอย่าง

แน่นอนว่าเราแทนในตัวแปรภาษา C,C++ ไม่ได้(เพราะ unsigned long long ก็ไม่ไหว **double ก็ได้แต่ค่าประมาณ**) เราจึงต้องพึ่งแอพเครื่องคิดเลขมหาเทพ หรือใช้ BigInt มาช่วย หรือถ้าล้ำกว่านั้น **ลองเขียนโปรแกรมใส่ภาษา python3 ไปเล้ย เพราะ INT ไม่จำกัด**

จากการลองแทนทำให้ได้ว่า

x = 0 ได้ *35*

x = 1 ได้ *7742863194275835*

x = 2 ได้ *774286319427587742863194275835*

x = 3 ได้ *77428631942758774286319427587742863194275835*

> เห็นอะไรหรือยัง

ความมหัศจรรย์ก็คือผลลัพธ์ มันมี 77428631942758 ซ้ำอยู่

> เห็นแล้วใช่ไหม

ฉะนั้นผลลัพธ์ก็คือ ตัวเลข 77428631942758 วนกัน x ครั้ง และจบด้วย 35

x = 0 ได้ *35*

x = 1 ได้ *77428631942758 35*

x = 2 ได้ *77428631942758 77428631942758 35*

x = 3 ได้ *77428631942758 77428631942758 77428631942758 35*

> ว้า่วซ่า

### เข้าถึง Solution B วิธีที่ 2 : แก้สมการ

จากสมการ(อีกแล้ว)

![สมการแมวๆA](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/A.PNG?raw=true)

เราต้องค่อยๆแก้สมการไปด้วยกัน ถ้าเราสังเกตุดีๆว่าตัวเลขพวกนี้ยังไม่ค่อยน่ารักเท่าไหร่ หรือก็คือ ตัวเลขทั้งหมดนี้ยังไม่ตัดทอนเป็นเศษส่วนอย่างต่ำนั่นเอง(รู้ได้ไงวะ)

ลองเอาตัวเลขทั้ง 3 ตัวไปหา หรม. ก็จะได้เป็น 7 ชะนั้น ลองเอา 7 ไปหารทั้งหมด ก็จะได้ด้ด้ด้ด้ด้

![สมการแมวๆB](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/B.PNG?raw=true)

เปลี่ยนรูปนิดนึงจะได้ง่ายขึ้น

![สมการแมวๆC](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/C.PNG?raw=true)

![สมการแมวๆD](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/D.PNG?raw=true)

![สมการแมวๆE](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/E.PNG?raw=true)

![สมการแมวๆF](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/F.PNG?raw=true)

![สมการแมวๆG](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/G.PNG?raw=true)

![สมการแมวๆH](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/H.PNG?raw=true)

![สมการแมวๆI](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/I.PNG?raw=true)

และสุดท้ายก็จะได้ในรูป

![สมการแมวๆJ](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/J.PNG?raw=true)

คุ้นๆมั้ย มันคือ **อนุกรมเรขาคณิต** ![อนุกรมเรขาคณิตK](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/K.PNG?raw=true)

> นานี๊เดอะฟัก

มันก็คือ **ผลรวม**ของ**ลำดับเรขาคณิต**

![อนุกรมเรขาคณิตL](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/L.PNG?raw=true)


> แล้วลำดับเรขาคณิตมันคืออะหยังอีกกกก

มันก็คือ ลำดับของตัวเลขที่**ค่อยๆคูณไปเรื่อยๆ** ซึ่งไอ้ตัวคุณ จะขอใช้ตัว r ละกัน

![ลำดับเรขาคณิตM](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/M.PNG?raw=true)

ซึ่งในที่นี้จะให้ *a1 = 7742863194275800* และ *r = 10^14 หรือ 1e14*

![สมการแมวๆN](https://github.com/Nepumi/OTOG-Editorial-2020/blob/master/20-Math%20%231/689%20%E0%B8%AA%E0%B8%A1%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%A1%E0%B8%A7%E0%B9%86/IMAGE/N.PNG?raw=true)

จะเห็นว่าถ้าเอา 35 มารวมด้วย ก็จะได้ผลลัพธ์คือ **ตัวเลข 77428631942758 วนกัน x ครั้ง และจบด้วย 35**



กลับมาที่ Solution จริงๆ แค่นี้ก็น่าจะรู้แล้วว่า
* ถ้าถามโหมด 1 ก็แค่เอาเลขโดด 77428631942758 (รวมได้ 73) มาคูณ x และบวกผลรวมของเลขโดด 35 (8) {73\*x+8}
* ถ้าถามโหมด 2 ก็แค่เอา 77428631942758 มาวน x ครั้งและจบด้วย 35

## Solution B Code
```c
#include<stdio.h>

int main(){


	int m,x;scanf("%d %d",&m,&x);
	if(m==1){
		printf("%d",x*73+8);
	}
	else{
		for(int i=0;i<x;i++)printf("77428631942758");
		printf("35");
	}
	return 0;


}

```

>ส่วนไอ้แมวตัวนั้นก็นอนหลับแล้ว คงไม่น่าใส่สมการเพิ่มหรอก -w-
