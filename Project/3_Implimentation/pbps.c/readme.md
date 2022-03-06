#include<reg51.h>

#include<string.h>

sbit r1 = P1^7;

sbit r2 = P1^6;

sbit r3 = P1^5;

sbit r4 = P1^4;

sbit c1 = P1^3;

sbit c2 = P1^2;

sbit c3 = P1^1;

sbit c4 = P1^0;

sfr lcd = 0xA0;

sbit rs = P3^0;

sbit rw = P3^1;

sbit en = P3^2;

sbit ab = P3^3;

sbit sw = P3^4;


unsigned int p,k,g=1;

unsigned int CmpPassword=0;

 char a[4];
 
 char pass[4]={"1234"};
 

void delay(unsigned int x) 

{
	unsigned int i,j;
	
	for(i=0;i<x;i++)
	
	for(j=0;j<50;j++);
}

void lcd_cmd(unsigned char cmd)

{

 lcd=cmd;
 
 rs=0;
 
 rw=0;
 
 en=1;
 
 delay(100);
 
 en=0;
 
 }

void lcd_data(unsigned char value)

{ 

 lcd=value;
 
 rs=1;
 
 rw=0;
 
 en=1;
 
 delay(100);
 
 en=0;
 
 }
 
 void lcd_string(unsigned char *msg)
 
 {
	 unsigned int i=0;
	 
	 for(i=0 ; msg[i]!='\0';i++)
	 
	 {
	 
  lcd_data(msg[i]);
  
 }
 
 }
 
 lcd_init()
 
 {
	 lcd_cmd(0x38);
	 
	 lcd_cmd(0x0e);
	 
	 lcd_cmd(0x01);
	 
	 lcd_cmd(0x06);
	 
 }

 unsigned char keyscan(void)
 
{ P2=0xff;
	
	while(1)
	
	{
	
		r1=0;
		
		r2=1;
		
		r3=1;
		
		r4=1;
		
		if(c1==0)
		
		{
		
			k='7';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c2==0)
		
		{
		
			k='8';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c3==0)
		
		{
		
			k='9';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c4==0)
		
		{
		
			k='/';
			
			delay(2000);
			
			return k;
			
		}

		r1=1;
		
		r2=0;
		
		r3=1;
		
		r4=1;
		
		if(c1==0)
		
		{
			k='4';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c2==0)
		
		{

			k='5';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c3==0)
		
		{
			k='6';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c4==0)
		
		{
			
			k='*';
			
			delay(2000);
			
			return k;
			
		}
		
    r1=1;
    
		r2=1;
		
		r3=0;
		
		r4=1;
		
		if(c1==0)
		
		{
		
			k='1';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c2==0)
		
		{
		

			k='2';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c3==0)
		
		{
		
			k='3';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c4==0)
		
		{
			k='-';
			
			delay(2000);
			
			return k;
			
		}
		
		r1=1;
		
		r2=1;
		
		r3=1;
		
		r4=0;
		
		if(c1==0)
		
		{ k='C';
		
			delay(2000);
			
			return k;
			
		}
		
		else if(c2==0)
		
		{

			k='0';
			
			delay(2000);
			
			return k;
			
		}
		
		else if(c3==0)
		
		{
			k='=';
			delay(2000);
			return k;
		}
		
		else if(c4==0)
		
		{
		
			k='+';
			
			delay(2000);
			
			return k;
			
		}
		
	}
	
 }
 

 void main(void)
 
 {
 
	 unsigned int i;ab=0;sw=0;
	 
		
	lcd_init();
	
	 
	while(1)
	
	{
	
		lcd_cmd(0x01); //to clear the screen
		
		
		lcd_string(" ENTER YOUR");
		
		lcd_cmd(0xc0);
		
		lcd_string(" PASSWORD");
		
		if(i==4)  //this is used after getting output to close the circuit by entering the password again
		
		{
			
			i=0;
			
			for(i=0;i<4;i++)
			
		{
		
			keyscan();
			
			
			a[i]=k;
			
			
			if(i==0)
			
			{
			
			  lcd_cmd(0x01);
			  
				lcd_data(' ');
				
			}
			
			lcd_data('*');   //lcd_data( k ); for displaying numbers
			
		}
 
			
		if(a[0]==pass[0] && a[1]==pass[1] && a[2]==pass[2]  && a[3]==pass[3])   //&& a[4]==pass[4])  comparing entered values and stored values
		
		{
		
		CmpPassword = strcmp(pass,a);  //here the password is compared by string compare function
		
		}	
		
						if(CmpPassword == 1) //if comparision is right then off the circuit
						
						{ 
							
							
							  
								lcd_cmd(0x80); //point the cursor to starting point
								
				        lcd_string("CORRECT PASSWORD");
					
							delay(3500);
							
							ab=0;  // switching on & off
							
							delay(500); 
							
							lcd_cmd(0x08); //to stop displaying
							
							  
													
						}
						
						if(CmpPassword == 0) //if comparision is wrong 
						
						{
						
							//lcd_cmd(0x80);
							
				        //lcd_string("WRONG PASSWORD");
					
						p++;
						
			lcd_cmd(0x01);
			
			lcd_string("WRONG PASSWORD!");
			
			lcd_cmd(0xc0);
			
			lcd_string(" ACCESS DENIED");
			
			delay(2000);
			
							
							lcd_cmd(0x01); //to clear the screen
		if(p<3)
		
		{
		
		lcd_string(" ENTER YOUR");
		
		lcd_cmd(0xc0);
		
		lcd_string(" PASSWORD");
		
		}
		
			//g=1;
			
			if(p==3)  //after 3 succesive times of wrong password 
			
			{
			
				  sw=1;  //used for glowing buzzer
				  
			
					lcd_cmd(0x01);
					
					lcd_string(" PLEASE CONTACT");
					
					lcd_cmd(0xc0);
					
					lcd_string("CUSTOMER CARE");
					
				delay(5000);
				
				while(1)   //this loop is used to off the buzzer after some delay of 5k(msec)
				
				{
				
				sw=0;
				
				}
				
					while(p==3);
					
				
			}
							 
							 delay(1000);	
							 
							
						}
						
					}
					
		
 
		for(i=0;i<4;i++)
		
		{
		
			keyscan();
			
			
			a[i]=k;
			
			
			if(i==0)
			
			{
			
			  lcd_cmd(0x01);
			  
				lcd_data(' ');
				
			}
			
			lcd_data('*');   //lcd_data( k ); for displaying numbers
			
		}
 
			
		if(a[0]==pass[0] && a[1]==pass[1] && a[2]==pass[2]  && a[3]==pass[3])   //&& a[4]==pass[4])  comparing entered values and stored values
		
		{
		
			g=1;
			
		}
		
	  else
	  
	  {
	  
			g=0;
			
		}
		
		
  if(g==1)	//if entered password == stored password then we get output
  
	{
	
			lcd_cmd(0x01);
			
			lcd_string("PASSWORD MATCHED");
			
			lcd_cmd(0xc0);
			
			lcd_string("ACCESS GRANTED");	
			
		
      ab=1;	
      
		  p=0; 
		
		if(ab==1)     //this loop displayed after getting output
		
		 {
		 
			 lcd_cmd(0x01);
			 
			 lcd_string("WELCOME TO VMEG");
			 
			 lcd_cmd(0xc0);
			 
			 lcd_string(" SUBSTATION ");
			 
		 }
		 
		 
	delay(5000);
	
		
	  //this loop is used to off the lcd display after getting output
	  
	
		//lcd_cmd(0x08);
		
		
		
	}
	
	
	
				
  
	
	else if(g==0)
	
		{
			p++;
			
			lcd_cmd(0x01);
			
			lcd_string("WRONG PASSWORD!");
			
			lcd_cmd(0xc0);
			
			lcd_string(" ACCESS DENIED");
			
			delay(2000);
			
			delay(2000);
			
			//g=1;
			
			if(p==3)
			
			{
			
				  sw=1;  //used for glowing buzzer
				  
			
					lcd_cmd(0x01);
					
					lcd_string(" PLEASE CONTACT");
					
					lcd_cmd(0xc0);
					
					lcd_string("CUSTOMER CARE");
					
				delay(5000);
				
				while(1)   //this loop is used to off the buzzer after some delay of 5k(msec)
				
				{
				
					sw=0;
					
				}
					
					while(p==3);
				
			}
			
   }
   
  }
  
}
