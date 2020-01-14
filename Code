
#include<16f877a.h>
#include<lcd12.c>
#use delay(clock=20000000)
#fuses HS, NOWDT, NOLVP, NOPROTECT
#use rs232(baud=9600, xmit = pin_c6, rcv = pin_c7)


#byte porta = 0x05
#byte portb = 0x06
#byte portc = 0x07
#byte portd = 0x08
#byte porte = 0x09

#byte lcd = 0x08

    char a[]="at";
	char b[]="at+csq";
	char c[]="at+cstt=";
	char d[]="airtelgprs.com";
    char e[]="at+cgatt=1";
    char f[]="at+ciicr";
    char g[]="at+cifsr";
    char h[]="at+cipstart=";
    char tcp[]="tcp";
    char k[]="122.166.179.167";
    char l[]="1234";
   
    char m[]="at+cipsend";

 unsigned int temp,light,moist,carbon;   
 int flag=0,flag1=0,flag2=0;

 void main()
   {
 int x;
	
	set_tris_a(0x0f);				
	set_tris_b(0x00);			
	set_tris_c(0x80);
	set_tris_d(0x00);	
	//set_tris_e(0x02);
	
	lcd_init();
	
	 bit_clear(portb,0);
	 bit_clear(portb,1);
	lcd_gotoxy(1,1);
   
	lcd_gotoxy(1,1);
    lcd_putc("GPRS              ");
    lcd_gotoxy(1,2);
    lcd_putc("Initialising             ");
    delay_ms(10000);
    x=0;
	    for(x=0;x<2;x++)
	    {
	       putc(a[x]);//at
           delay_ms(5);
	    }
	      putc(0x0d);//enter
          delay_ms(2000);
          putc(0x0a);//new line
	    
	    for(x=0;x<6;x++)
	    {
	       putc(b[x]);//at+csq
           delay_ms(5);
	    }
	    
          putc(0x0d);//enter
          delay_ms(2000);
          putc(0x0a);//new line
	    
        for(x=0;x<8;x++)
	    {
	       putc(c[x]);//at+cstt=
           delay_ms(5);
	    }
          putc(0x22);//double quote
          delay_ms(5);
          
        for(x=0;x<14;x++)
	    {
	       putc(d[x]);//airtelgprs.com
           delay_ms(5);
	    }

          delay_ms(1000);
		  putc(0x22);//double quote
		  putc(0x2c);//comma
		  delay_ms(100);
		  putc(0x22);//double quote
	      putc(0x22);//double quote
		  putc(0x2c);//comma
	      putc(0x22);//double quote
		  putc(0x22);//double quote
		  delay_ms(1000);
          putc(0x0d);//enter
          putc(0x0a);//new line
		  delay_ms(2000);
          
        for(x=0;x<10;x++)
	    {
	       putc(e[x]);//at+cgatt=1
           delay_ms(5);
	    } 
         putc(0x0d);//enter
         delay_ms(2000);
         putc(0x0a);//new line
         
        for(x=0;x<8;x++)
	    {
	       putc(f[x]);//at+ciicr
           delay_ms(5);
	    } 
         putc(0x0d);//enter
         delay_ms(4000);
         putc(0x0a);//new line
         
        for(x=0;x<8;x++)
	    {
	       putc(g[x]);//at+cifsr
           delay_ms(5);
	    } 
         putc(0x0d);//enter
         delay_ms(2000);
         putc(0x0a);//new line
  
      
          
        for(x=0;x<12;x++)
	    {
	       putc(h[x]);//at+cipstart=
           delay_ms(5);
	    } 
         
         putc(0x22);//double quote
         delay_ms(5);
         
        for(x=0;x<3;x++)
	    {
	       putc(tcp[x]);//tcp
           delay_ms(5);
	    } 
	     putc(0x22);//double quote
         delay_ms(5);
         putc(0x2c);//comma
         delay_ms(5);
         putc(0x22);//double quote
         delay_ms(5);
         
        for(x=0;x<15;x++)
	     {
	       putc(k[x]);//ip
           delay_ms(5);
	    }
          putc(0x22);//double quote
          delay_ms(5);
          putc(0x2c);//comma
          delay_ms(5);
          putc(0x22);//double quote
          delay_ms(5);
         for(x=0;x<4;x++)
	      {
	       putc(l[x]);//port no
           delay_ms(5);
	      } 
         
          putc(0x22);//double quote
          delay_ms(5);
          putc(0x0d);//enter
          delay_ms(10000);
          putc(0x0a);//new line
          lcd_gotoxy(1,1);
          lcd_putc("CONNECTED               ");


	   lcd_init();
       lcd_gotoxy(1,1);
       lcd_putc("GREEN HOUSE ");
       delay_ms(2000);
       lcd_putc("\f");//lcd clear

     setup_adc_ports( ALL_ANALOG );
     setup_adc(ADC_CLOCK_INTERNAL );
    
while(1)
   {
set_adc_channel(0);
delay_ms(50);
temp = read_adc();
temp=temp*2;
delay_ms(50);
lcd_gotoxy(1,1);
printf(lcd_putc,"Temp=%u%cC     ",temp,0xdf);
delay_ms(100);
//for(x=0;x<10;x++)
//{
//  putc(m[x]);//at
//     delay_ms(5);
//}
// delay_ms(100);
// putc(0x0d);//enter
// delay_ms(1000);
// putc(0x0a);//new line
//    delay_ms(10);
//    //putc('2');
//     printf("T%u",temp);
//    delay_ms(100);
//    putc(0x1a);//ctrl^z
    
set_adc_channel(1);
delay_ms(50);
carbon = read_adc();
carbon=(carbon*100.0)/255.0;
delay_ms(70);
lcd_gotoxy(9,1);
printf(lcd_putc,"C:%u%c ",carbon,0x25);
delay_ms(100);
//for(x=0;x<10;x++)
//{
//  putc(m[x]);//at
//     delay_ms(5);
//}
// delay_ms(100);
// putc(0x0d);//enter
// delay_ms(1000);
// putc(0x0a);//new line
//    delay_ms(10);
//    //putc('2');
//     printf("C%u",carbon);
//    delay_ms(100);
//    putc(0x1a);//ctrl^z
    
set_adc_channel(2);
delay_ms(50);
light = read_adc();
light=(light*100.0)/255.0;
delay_ms(90);
lcd_gotoxy(1,2);
printf(lcd_putc,"L:%u%c ",light,0x25);
delay_ms(100);
//for(x=0;x<10;x++)
//{
//  putc(m[x]);//at
//     delay_ms(5);
//}
// delay_ms(100);
// putc(0x0d);//enter
// delay_ms(1000);
// putc(0x0a);//new line
//    delay_ms(10);
//    //putc('2');
//     printf("L%u",light);
//    delay_ms(100);
//    putc(0x1a);//ctrl^z
//    
set_adc_channel(3);
delay_ms(50);
moist = read_adc();
moist=(moist*100.0)/255.0;
delay_ms(120);
lcd_gotoxy(9,2);
printf(lcd_putc,"M:%u%c ",moist,0x25);
delay_ms(100);
for(x=0;x<10;x++)
{
  putc(m[x]);//at
     delay_ms(5);
}
 delay_ms(100);
 putc(0x0d);//enter
 delay_ms(1000);
 putc(0x0a);//new line
    delay_ms(10);
    //putc('2');
     printf("%u&%u&%u&%u",temp,light,moist,carbon);
    delay_ms(100);
    putc(0x1a);//ctrl^z
    
if((moist>=45) && (flag==0))
{
 bit_set(portb,0);
 flag=1;
}

 if((moist<60) && (flag==1))
{
 bit_clear(portb,0);
 flag=0;
}
 
if((temp>=45) && (flag1==0))
{
 bit_set(portb,1);
 flag1=1;
}

 if((temp<45) && (flag1==1))
{
 bit_clear(portb,1);
 flag1=0;
}

if((light>=95) && (flag2==0))
{
 bit_set(portb,2);
 flag2=1;
}

 if((light<90) && (flag2==1))
{
 
 bit_clear(portb,2);
 flag2=0;
} 
}//while
}//main
