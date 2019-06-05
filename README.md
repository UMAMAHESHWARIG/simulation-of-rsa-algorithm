#simulation of rsa


#include<GL/glut.h>
#include<string.h>
#include<stdio.h>
#include<math.h>
GLfloat rotation = 90.0;
float posX = 0, posY = 0, posZ = 0;
void leftman();
void hacker();
void move();
void display();
void dec(char *);
void enc(char *);

void myinit()                      //my init finction
{
 glClearColor(0.0,0.911111,0.911111,0.0);
 glMatrixMode(GL_PROJECTION);
 glLoadIdentity();
 glPointSize(5.0);
 gluOrtho2D(0,1000,0,600);

}
int fillFlag=0;

void text2()
{
int i=0;
char str[]="ROY AND BOB ARE COMMUNICATING WITH EACHOTHER";             //alice and bob and hacking
char str1[]="ROY";
char str2[]="BOB";
char str3[]="HACKER";
glColor3f(0,0,0);
	glRasterPos2f(-850,1200);
		
		for(i=0;i<strlen(str);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str[i]);
		
		}
		glRasterPos2f(-1150,180);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
		glColor3f(0,0,1);
		glRasterPos2f(600,180);
		for(i=0;i<strlen(str2);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str2[i]);
		}glColor3f(0,0,1);
		glRasterPos2f(635,-700);
		for(i=0;i<strlen(str3);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str3[i]);
		}

		
}


void enc(char *str1)                           //decryption of input text
{
int i,j,k;
glColor3f(1.0,1.0,0.0);
glRasterPos2f(350,-350);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
glRasterPos2f(-200,580);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
//glFlush();
}


void dec(char *str1 )                         //encryption of input text
{
int i,j,k;
glColor3f(1.0,1.0,0.0);
glRasterPos2f(320,590);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
glColor3f(1.0,1.0,0.0);
glRasterPos2f(-780,590);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
//glFlush();
}

     
    int p,q,n,t,flag,d[100],temp[100],j,e[100],i;
    char en[100],m[100];
    char msg[100];    
    int prime(int);    
    void ce();    
    int cd(int);     
    void encrypt();
    void decrypt();

    void displayrsa() {
    	printf("\nENTER FIRST PRIME NUMBER P\n");
    	scanf("%d",&p);
    	flag=prime(p);
    	if(flag==0) {
    		printf("\nWRONG INPUT\n");
    		exit(1);
    	}
    	printf("\nENTER ANOTHER PRIME NUMBER Q\n");
    	scanf("%d",&q);     
    	flag=prime(q);     
    	if(flag==0||p==q) {     
    		printf("\nWRONG INPUT\n");     
    		exit(1);    
    	}     
    	printf("\nENTER MESSAGE\n");
    	scanf("%s",msg);     
    	for (i=0;msg[i]!=0;i++)   
    	m[i]=msg[i];    
    	n=p*q;   
    	t=(p-1)*(q-1);     
    	ce();
        printf("\nPOSSIBLE VALUES OF e AND d ARE\n");     
    	for (i=0;i<j-1;i++)    
    	printf("\n%d\t%d",e[i],d[i]);     
    	encrypt();     
    	decrypt();
         
        }
     
   int prime(int pr) {   
    	int i;     
    	j=sqrt(pr);    
    	for (i=2;i<=j;i++) 
{ 
    		if(pr%i==0)    
    		    return 0;     
    	}   
    	return 1;
}
     
    void ce() {    
    	int k;    
    	k=0;    
    	for (i=2;i<t;i++) {    
    		if(t%i==0)     
    		    continue;
      		flag=prime(i);   
    		if(flag==1&&i!=p&&i!=q) {     
    			e[k]=i;    
    			flag=cd(e[k]);    
    			if(flag>0) {    
    				d[k]=flag;
       				k++;
       			}
        			if(k==99)
    			        break;}
    	}
    }
     
    int cd(int x) {
    	int k=1;   
    	while(1) {    
    		k=k+t;    
    		if(k%x==0) 
    		    return(k/x);} 
}
     
    void encrypt() {    
    	int pt,ct,key=e[0],k,len;     
    	i=0;    
    	len=strlen(msg);   
    	while(i!=len) {   
    		pt=m[i];  
    		pt=pt-96;  
    		k=1;
     		for (j=0;j<key;j++) {
    			k=k*pt;
        	       k=k%n;     
    		}
        	temp[i]=k;
    		ct=k+96;
    		en[i]=ct;
    		i++;
     
    	}
        
    	en[i]=-1;
        enc(en);
     
    }
     
    void decrypt() {     
     int pt,ct,key=d[0],k;     
    	i=0;
    	while(en[i]!=-1) {     
    		ct=temp[i];     
    		k=1;  
    		for (j=0;j<key;j++) {     
    			k=k*ct;     
    			k=k%n;     
    		}    
    		pt=k+96;    
    		m[i]=pt;    
    		i++;
    	}
       
    	m[i]=-1;
      dec(m);
    }
     


void text()
{	

char str2[]="COMPUTER GRAPHICS MINI PROJECT";
char str4[]="SIMULATION OF RSA ALGORITHM";
int i=0;
glColor3f(0,0,0);
		glRasterPos2f(320,480);
		for(i=0;i<strlen(str2);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str2[i]);
		}
		glColor3f(0,0,1);
		glRasterPos2f(330,450);
		for(i=0;i<strlen(str4);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str4[i]);
		}

		
}
void monright()           //right laptop
{
glColor3f(0.5,0.5,0.5);
glBegin(GL_POLYGON);	//monitor
glVertex2f(350,350);
glVertex2f(700,350);
glVertex2f(700,600);
glVertex2f(350,600);
glEnd();
glColor3f(0.0,0.1,0.1);
glBegin(GL_POLYGON);	//inside screen
glVertex2f(370,370);
glVertex2f(680,370);
glVertex2f(680,580);
glVertex2f(370,580);
glEnd();

glColor3f(0.8,0.8,0.8);//keyboard outer
glBegin(GL_POLYGON);	
glVertex2f(450,220);
glVertex2f(800,220);
glVertex2f(700,350);
glVertex2f(350,350);
glEnd();
glColor3f(0.5,0.5,0.5);//strips
glBegin(GL_POLYGON);	
glVertex2f(450,220);
glVertex2f(500,220);
glVertex2f(400,350);
glVertex2f(350,350);
glEnd();

glColor3f(0.5,0.5,0.5);//strips
glBegin(GL_POLYGON);	
glVertex2f(450,220);
glVertex2f(800,220);
glVertex2f(770,250);
glVertex2f(480,250);
glEnd();

//glFlush();
                                              

}
void mon()               //left laptop
{

glColor3f(0.5,0.5,0.5);
glBegin(GL_POLYGON);	//monitor
glVertex2f(350,350);
glVertex2f(700,350);
glVertex2f(700,600);
glVertex2f(350,600);
glEnd();
glColor3f(0.0,0.1,0.1);
glBegin(GL_POLYGON);	//inside screen
glVertex2f(370,370);
glVertex2f(680,370);
glVertex2f(680,580);
glVertex2f(370,580);
glEnd();

glColor3f(0.8,0.8,0.8);//strips
glBegin(GL_POLYGON);	
glVertex2f(220,220);
glVertex2f(590,220);
glVertex2f(700,350);
glVertex2f(350,350);
glEnd();
glColor3f(0.5,0.5,0.5);
glBegin(GL_POLYGON);	
glVertex2f(580,220);
glVertex2f(590,220);
glVertex2f(700,350);
glVertex2f(690,350);
glEnd();

glColor3f(0.5,0.5,0.5);
glBegin(GL_POLYGON);	
glVertex2f(220,220);
glVertex2f(590,220);
glVertex2f(600,230);
glVertex2f(230,230);
glEnd();


glColor3f(0.1,0.0,0.0);
glBegin(GL_POLYGON);	
glVertex2f(295,260);
glVertex2f(570,260);
glVertex2f(630,330);
glVertex2f(375,330);
glEnd();

glColor3f(0.0,0.0,0.0);
glBegin(GL_POLYGON);	
glVertex2f(365,235);
glVertex2f(465,235);
glVertex2f(485,255);
glVertex2f(395,255);
glEnd();

//glFlush();

}
void hacker()
{
glColor3f(0.5,0.5,0.5);//face
glBegin(GL_POLYGON);	
glVertex2f(180,340);                             
glVertex2f(180,280);
glVertex2f(220,220);
glVertex2f(340,220);
glVertex2f(380,20);
glVertex2f(380,340);
glEnd();
glColor3f(0.0,0.0,0.0);//hatbase   ///////duplicate man  that is hacker
glBegin(GL_POLYGON);	
glVertex2f(140,370);
glVertex2f(140,340);
glVertex2f(420,340);
glVertex2f(420,370);
glEnd();
glColor3f(0.5,0.5,0.5);
glPointSize(30);
glBegin(GL_POLYGON);//	ears
glVertex2f(380,320);
glVertex2f(180,320);
glEnd();
glColor3f(0.0,0.0,0.0);//hattop
glBegin(GL_POLYGON);	
glVertex2f(200,450);
glVertex2f(180,370);
glVertex2f(380,370);
glVertex2f(360,450);
glEnd();
glColor3f(0.5,0.5,0.5);//shoulder
glBegin(GL_POLYGON);	
glVertex2f(100,100);
glVertex2f(500,100);
glVertex2f(450,200);
glVertex2f(150,200);
glEnd();
glColor3f(0.5,0.5,0.5);//neck
glBegin(GL_POLYGON);	
glVertex2f(260,200);
glVertex2f(320,200);
glVertex2f(320,220);
glVertex2f(260,220);
glEnd();
}

void hacker1()                   //hacker   who is original
{
glColor3f(0.5,0.5,0.5);//face
glBegin(GL_POLYGON);	
glVertex2f(180,340);
glVertex2f(180,280);
glVertex2f(220,220);
glVertex2f(340,220);
glVertex2f(380,280);
glVertex2f(380,340);
glEnd();
glColor3f(0.0,0.0,0.0);//hatbase
glBegin(GL_POLYGON);	
glVertex2f(140,370);
glVertex2f(140,340);
glVertex2f(420,340);
glVertex2f(420,370);
glEnd();
glColor3f(1,1,1);
glPointSize(30);
glBegin(GL_POLYGON);//	ears
glVertex2f(380,320);
glVertex2f(180,320);
glEnd();
glColor3f(0.0,0.0,0.0);//hattop
glBegin(GL_POLYGON);	
glVertex2f(200,450);
glVertex2f(180,370);
glVertex2f(380,370);
glVertex2f(360,450);
glEnd();
glColor3f(0.5,0.5,0.5);//shoulder
glBegin(GL_POLYGON);	
glVertex2f(100,100);
glVertex2f(500,100);
glVertex2f(450,200);
glVertex2f(150,200);
glEnd();
glColor3f(0.5,0.5,0.5);//neck
glBegin(GL_POLYGON);	
glVertex2f(260,200);
glVertex2f(320,200);
glVertex2f(320,220);
glVertex2f(260,220);
glEnd();
}
void lines()
{
glColor3f(1.0,1.0,1.0);
glEnable(GL_LINE_STIPPLE);
glLineStipple(7,0xAAAA);
glLineWidth(5);
glBegin(GL_LINE_STRIP);
glVertex2f(-170,590);
glVertex2f(-170,-350);
glEnd();
glEnable(GL_LINE_STIPPLE);
glLineStipple(7,0xAAAA);
glLineWidth(5);
glBegin(GL_LINE_STRIP);
glVertex2f(-170,-350);
glVertex2f(200,-350);
glEnd();
//glFlush();

}


void displaymonhac()
{
glMatrixMode(GL_MODELVIEW);
glPushMatrix();
glPopMatrix();
glScalef(0.8,0.8,0.0);
glPushMatrix();
glTranslatef(-155,150,0);   //topright laptop
monright();
glPopMatrix();
glPushMatrix();
glTranslatef(-155,-800,0);
monright();                //bottomright latop
glPopMatrix();
glPushMatrix();

glScalef(1.9,1.9,0);
glTranslatef(-850,-350,0);
leftman();                  //mana

glPopMatrix();
glPushMatrix();
glScalef(1,1,0);
glTranslatef(-1240,170,0);
mon();                      // leftman laptop
glPopMatrix();
glPushMatrix();
glTranslatef(500,-600,0);
hacker();
glPopMatrix();
}

void leftman()
{
glColor3f(1,0,0);       //lman right hand part
	glBegin(GL_POLYGON);
	glVertex2i(262,728);
	glVertex2i(233,700);
	glVertex2i(226,670);
	glVertex2i(228,642);
	glVertex2i(255,660);
	glVertex2i(264,680);
	glVertex2i(263,691);
	glEnd();



	glColor3f(1,0,0);       //right hand part
	glBegin(GL_POLYGON);
	glVertex2i(252,600);
	glVertex2i(250,639);
	glVertex2i(255,644);
	glVertex2i(255,660);
	glVertex2i(228,642);
	glEnd();
	glColor3f(0,0,0);  
glPointSize(5.0);              //right hand part
	glBegin(GL_POLYGON);   //hand1
	glVertex2i(228,642);
	glVertex2i(235,600);
        glVertex2i(252,600);
	glEnd();
       

	glColor3f(0,0,1);       //body part
	glBegin(GL_POLYGON);
	glVertex2i(252,600);                                //least x 252.600
	glVertex2i(295,520);
	glVertex2i(309,492);                           //least y val 309,492
	glVertex2i(327,540);
	glVertex2i(327,664);
	glVertex2i(319,699);
	glVertex2i(297,719);
	glVertex2i(255,644);
	glVertex2i(250,639);
	glEnd(); 

	glColor3f(0,0,1);       //body part
	glBegin(GL_POLYGON);
	glVertex2i(252,600);
	glVertex2i(295,520);
	glVertex2i(252,488);
	glVertex2i(249,492);                             //last point 249,492
	glEnd();
       
        glColor3f(0,0,1);       //body part
	glBegin(GL_POLYGON);
	glVertex2i(249,492); 
        glVertex2i(327,492);                            //last point 249,492
	glVertex2i(326,528);
        glVertex2i(249,520);
        glEnd();

	glColor3f(0.0,0.0,1);       //body part
	glBegin(GL_POLYGON);
	glVertex2i(255,644);
	glVertex2i(255,660);
	glVertex2i(264,680);
	glVertex2i(263,691);
	glVertex2i(262,728);
	glVertex2i(270,732);
	glVertex2i(300,728);
	glVertex2i(297,719);
	glEnd();
glColor3f(1,0.871,0.678); 
         glBegin(GL_POLYGON);glClear(GL_COLOR_BUFFER_BIT);//hand
	glVertex2i(228,642);
	
	glVertex2i(235,600);
        glVertex2i(335,580);
        glVertex2i(335,610);
	glEnd();
glColor3f(1,0.871,0.678); 
         glBegin(GL_POLYGON);glClear(GL_COLOR_BUFFER_BIT);//handfist 1
	glVertex2i(325,615);
	
	glVertex2i(325,605);
        glVertex2i(340,605);
        glVertex2i(340,615);
	glEnd();

glColor3f(1,0.871,0.678); 
         glBegin(GL_POLYGON);//handfist 2
	
	
	glVertex2i(325,605);
        glVertex2i(325,575);
        glVertex2i(350,575);
         glVertex2i(350,605);
	glEnd();

        glColor3f(1,0.871,0.678); 
	glBegin(GL_POLYGON);
	glVertex2i(300,728);
	glVertex2i(285,760);
	glVertex2i(278,766);
	glVertex2i(276,760);
	glVertex2i(270,748);
	glVertex2i(273,744);
	glVertex2i(270,732);
	glEnd();


	glColor3f(1,0.871,0.678);       //6face part
	glBegin(GL_POLYGON);
	glVertex2i(300,728);
	glVertex2i(278,766);
	glVertex2i(276,780);
	glVertex2i(284,784);
	glVertex2i(285,783);
	glVertex2i(306,748);
	glVertex2i(270,732);
	glEnd();
	glColor3f(1,0.871,0.678);       //6face part
	glBegin(GL_POLYGON);
	glVertex2i(306,773);
	glVertex2i(305,794);
	glVertex2i(330,800);
	glVertex2i(332,768);
	glVertex2i(333,760);
	glVertex2i(328,750);
	glVertex2i(312,752);
	glEnd();

	glColor3f(0.000,0.000,0.000);       //hair part back
	glBegin(GL_POLYGON);
	glVertex2i(276,820);
	glVertex2i(258,796);
	glVertex2i(258,768);
	glVertex2i(270,748);
	glVertex2i(273,744);
	glVertex2i(276,760);
	glVertex2i(285,760);
	glVertex2i(276,780);
	glVertex2i(284,784);
	glEnd();

	glColor3f(0.000,0.000,0.000);       //part forehead
	glBegin(GL_POLYGON);
	glVertex2i(276,820);
	glVertex2i(284,784);
	glVertex2i(285,783);
	glVertex2i(285,792);
	glVertex2i(300,796);
	glVertex2i(305,794);
	glVertex2i(330,800);
	glVertex2i(315,820);
	glVertex2i(276,820);
	glEnd();

	glColor3f(0.000,0.000,0.000);       //hair part
	glBegin(GL_POLYGON);
	glVertex2i(300,796);
	glVertex2i(305,794);
	glVertex2i(306,773);
	glVertex2i(312,752);
	glVertex2i(306,748);
	glEnd();
    
	glColor3f(0.000,0.000,0.000);       //hair part
	glBegin(GL_POLYGON);
	glVertex2i(306,748);
	glVertex2i(303,736);
	glVertex2i(306,716);
	glVertex2i(312,720);
	glVertex2i(312,752);
	glEnd();
 
	glColor3f(0.000,0.000,0.000);       //hair part
	glBegin(GL_POLYGON);
	glVertex2i(306,716);
	glVertex2i(312,720);
	glVertex2i(328,727);
	glVertex2i(330,716);
	glVertex2i(316,712);
	glEnd();

	glColor3f(0.000,0.000,0.000);       //hair part
	glBegin(GL_POLYGON);
	glVertex2i(312,752);
	glVertex2i(312,740);
	glVertex2i(326,736);
	glVertex2i(328,751);
	glEnd();
	glColor3f(0.000,0.000,0.000);       //hair part
	glBegin(GL_POLYGON);
	glVertex2i(328,750);
	glVertex2i(326,736);
	glVertex2i(330,720);
	glVertex2i(328,720);
	glVertex2i(324,736);
	glEnd();
	glColor3f(1,0.871,0.678);       //face part
	glBegin(GL_POLYGON);
	glVertex2i(328,720);
	glVertex2i(324,736);
	glVertex2i(312,720);
	glVertex2i(312,740);
	glVertex2i(318,740);
	glVertex2i(321,740);
	glVertex2i(323,740);
	glEnd();
	glColor3f(1,0.871,0.678);       //face part
	glBegin(GL_POLYGON);
	glVertex2i(306,748);
	glVertex2i(285,783);
	glVertex2i(285,792);
	glVertex2i(300,796);
	glEnd();
	glColor3f(1.000,1.000,1.000);       //eye part
	glBegin(GL_POLYGON);
	glVertex2i(312,778);
	glVertex2i(312,776);
	glVertex2i(316,774);
	glVertex2i(316,776);
	glVertex2i(324,780);
	glEnd();
	glColor3f(0.000,0.000,0.000);
	glBegin(GL_POINTS);
	glVertex2i(316,778);
	glEnd();
	glColor3f(0.000,0.000,0.000);
	glBegin(GL_LINES);
	glVertex2i(310,778);
	glVertex2i(323,780);
	glEnd();
}

void man2()
{ 
glBegin(GL_POLYGON);
			glColor3f(1,0.871,0.678);
			glVertex2f(550,670); 			
			glVertex2f(530,610);
			glVertex2f(580,575);
			glVertex2f(610,665);
			glEnd();           ///square face
glBegin(GL_POLYGON);
			glColor3f(0,0,0);//head
			glVertex2f(510,675);
			glVertex2f(550,660);
			glVertex2f(610,665);//hair
			glVertex2f(610,685);
			glVertex2f(600,700);
			glVertex2f(590,710);
			glVertex2f(550,710);
			glEnd();
glBegin(GL_POLYGON);glVertex2f(525,700);
			glColor3f(1,0.871,0.678);			
			glVertex2f(535,610);//head
			glVertex2f(500,625);	
			glVertex2f(525,575);
			glVertex2f(590,575);
			glEnd();
glBegin(GL_POLYGON);
			glColor3f(1,0.871,0.678);
			glVertex2f(510,675);//face
			glVertex2f(510,640);
			glVertex2f(550,660);
			glEnd();
glBegin(GL_POLYGON);
			glColor3f(1,0.871,0.678);
			glVertex2f(510,640);//face
			glVertex2f(500,625);
			glVertex2f(535,610);
			glVertex2f(550,660);
			glEnd();
glPointSize(6.0);//eye
glBegin(GL_POINTS);
			glColor3f(0,0,0);
			glVertex2f(528,645);
			glEnd();

               glBegin(GL_LINE_STRIP);
			glColor3f(0,0,0);
			glVertex2f(520,650);
			glVertex2f(525,655);
			glVertex2f(535,655);
			glEnd();//eye line

                  glBegin(GL_POLYGON);
			glColor3f(0.502,0.502,0);//neck 
			glVertex2f(525,575);
			glColor3f(0,0,0);
			glVertex2f(500,525);
			glVertex2f(590,575);
			glEnd();
                    glBegin(GL_POLYGON);	//hand1
			glColor3f(1,0.894,0.769);
			glVertex2f(440,450);
			glVertex2f(440,390);
			glVertex2f(500,450);
			glVertex2f(500,390);
			glEnd();
                 glBegin(GL_POLYGON);			
			glColor3f(0.545,0.000,0.000);
			glVertex2f(500,525);
			glVertex2f(475,400);
			glVertex2f(475,375);
			glVertex2f(560,375);
			glVertex2f(575,400);
			glVertex2f(565,500);
			glVertex2f(600,525);
			glVertex2f(580,575);
			glEnd();                          //body dress
                       glBegin(GL_POLYGON);
			glColor3f(0.545,0.000,0.000);
			glVertex2f(475,375);           //lowersquaredress
			glColor3f(0.545,0.000,0.000);
			glVertex2f(460,225);
			glColor3f(0,0,0);
			glVertex2f(600,225);
			glColor3f(0,0,0);
			glVertex2f(600,375);
			glEnd();
                        glBegin(GL_POLYGON);               //lefthandshd
			glColor3f(1,0.871,0.678);
			glVertex2f(565,500);
			glVertex2f(575,400);
			glVertex2f(615,400);
			glVertex2f(615,475);
			glVertex2f(600,525);
			glEnd();
                    glBegin(GL_POLYGON);
			glColor3f(1,0.894,0.769);          //leftfingure 
			glVertex2f(500,400);
			glVertex2f(450,420);
			glVertex2f(450,355);
			glVertex2f(500,365);
		    glEnd();
                     glBegin(GL_POLYGON);
			glColor3f(1,0.871,0.678);
			glVertex2f(615,415);              //shdltofingure
			glVertex2f(500,400);
			glVertex2f(500,365);		      
			glVertex2f(615,365);
		    glEnd();
}
void formula()
{
char str[]="n=P*Q";
char str1[]="q(n)=(P-1)*(Q-1)";
char str2[]="ENCRYPTION:message^e mod n";
char str3[]="DECRYPTION:encryption^d mod n";
glColor3f(.0,0.0,0.0);
glRasterPos2f(-1200,-200);
		for(i=0;i<strlen(str);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str[i]);
		}
glRasterPos2f(-1200,-300);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
glRasterPos2f(-1200,-400);
		for(i=0;i<strlen(str2);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str2[i]);
		}
glRasterPos2f(-1200,-500);
		for(i=0;i<strlen(str3);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str3[i]);
		}
}

void displayman()
{                             //right side man
glMatrixMode(GL_MODELVIEW);
glPushMatrix();
glPopMatrix();
glScalef(0.4,0.3,0);
glPushMatrix();
glTranslatef(1200,800,0);
man2();
}

void move()
{
int i,j,k;
char str20[]="MORAL";
glColor3f(1.0,1.0,0.0);
glRasterPos2f(220,380);
		for(i=0;i<strlen(str20);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str20[i]);
		}
//glFlush();
}
void square()
{
glColor3f(1,0,0);
glBegin(GL_POLYGON);
glVertex2f(-540,550);
glVertex2f(-540,650);
glVertex2f(200,650);
glVertex2f(200,550);
glEnd();
}

void dialogue()                            //dialouge box
{
glColor3f(1,0,0);
glBegin(GL_POLYGON);
glVertex2f(400,480);
glVertex2f(400,520);
glVertex2f(150,520);
glVertex2f(150,480);
glVertex2f(300,480);
glVertex2f(140,460);
glVertex2f(400,480);
glEnd();
}

void rsatext()                                         //RSA
{
int i=0;
char str1[]="RSA ALGORITHM";
glColor3f(0,0,0);
 glRasterPos2f(-200,1100);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}

}
void move3()                                         //display mssg when hacked
{
int i=0;
char str[]="message hacked";
char str1[]="MORAL                                                                        "; .
glColor3f(.498,1,0);
 glRasterPos2f(200,500);
		for(i=0;i<strlen(str);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str[i]);
		}
glRasterPos2f(550,150);
		for(i=0;i<strlen(str);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
   
    //glFlush();
}
void question()
{
char str1[]="?????";
glColor3f(0,0,0);
 glRasterPos2f(850,-100);
		for(i=0;i<strlen(str1);i++)
		{
			glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24,str1[i]);
		}
}
void displaytextmoving()            //move the text in square
{
    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
    glPushMatrix();
    glTranslatef(posX,posY,posZ);
    move();
    glPopMatrix();
    glFlush();
}


float move_unit = 167.0f;
void keyboardown(int key, int x, int y)
{
    switch (key){
        case GLUT_KEY_RIGHT:
            posX+=move_unit;;
            break;

        default:
         break;
    }
   glutPostRedisplay();
glutSwapBuffers();
}

void mans()
{
glClear(GL_COLOR_BUFFER_BIT);
displayman();                      
displaymonhac();
square();
lines();
text2();
displaytextmoving();
glFlush();
}

void mans1()
{

glClear(GL_COLOR_BUFFER_BIT);
displayman();                      
displaymonhac();
square();
lines();
rsatext();
glFlush();
}


int Flag1=0,Flag2=0,Flag3=0;
void displaykey()   //keuboard
{
if(Flag1==1)                //press x
{
dialogue();
move3();
}

if(Flag1==2)                     //press y
{
glClear(GL_COLOR_BUFFER_BIT);
glFlush();
mans1();

}
if(Flag1==3)

question();
formula();                              //press z
displayrsa();
}
glFlush();
}

void keys(unsigned char key,int x,int y)
{
if(key=='x')
{Flag1=1;
}
if(key=='y')
Flag1=2;
if(key=='z')
{Flag1=3;
}
displaykey();
glutSwapBuffers();
}

void display()
{
glClear(GL_COLOR_BUFFER_BIT);          //option 1
if(fillFlag==1)
{
text();
}
else if(fillFlag==2)                   //option 2
{
mans();
}
else if(fillFlag==3)                   //option 2
{
exit (0);
}
glutSwapBuffers();
}

void fillMenu(int option)
{
if(option==1)
fillFlag=1;
else if(option==2)
fillFlag=2;
else if(option==3)
fillFlag=3;
display();
}

void main(int argc, char **argv)
{
glutInit(&argc,argv);
glutInitDisplayMode(GLUT_DOUBLE|GLUT_RGB);
glutInitWindowPosition(00,00);
glutInitWindowSize(1200,800);
glutCreateWindow("Simulation of RSA algorithm");
myinit();
glutKeyboardFunc(keys);
glutDisplayFunc(display);
glutSpecialFunc(keyboardown);
glutCreateMenu(fillMenu);
glutAddMenuEntry("front page",1);
glutAddMenuEntry("rsa",2);
glutAddMenuEntry("exit",3);
glutAttachMenu(GLUT_RIGHT_BUTTON);
glutMainLoop();
}
