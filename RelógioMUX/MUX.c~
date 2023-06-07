#include <8052.h>

int UnidSegundos=0;
int DezSegundos=0;
int UnidMinutos=0;
int DezMinutos=0;

unsigned char Decod7Seg[]={192,249,164,176,153,146,130,248,128,144};

void recarregaTimer(){

	TR0=0;
	TH0=0x0FF;
	TL0=0x0DC;
	TR0=1;

}

void main(){

	TMOD=1;
	EA=1;
	ET0=1;
	TH0=0x0FF;
	TL0=0x0DC;
	TR0=1;

	while(1){}

}

void interrupcaoTimer1() __interrupt 1{

	if(++UnidSegundos==10){

		UnidSegundos=0;
		DezSegundos++;
		
		if(DezSegundos==6){

			DezSegundos=0;
			UnidMinutos++;
			
			if(UnidMinutos==10){

				UnidMinutos=0;
				DezMinutos++;
				
				if(++DezMinutos==6){DezMinutos=0;}

			}

		}

	}
	Display7Seg();
}

void Display7Seg(){

	if(UnidSegundos<10){

		P1=255;
		P2=Decod7Seg[UnidSegundos];
		P1_0=0;

		if(DezSegundos<6){

			P1=255;
			P2=Decod7Seg[DezSegundos];
			P1_1=0;

			if(UnidMinutos<10){

				P1=255;
				P2=Decod7Seg[UnidMinutos];
				P1_2=0;

				if(DezMinutos<6){

					P1=255;
					P2=Decod7Seg[DezMinutos];
					P1_3=0;
					recarregaTimer();

				}

			}

		}

	}
}