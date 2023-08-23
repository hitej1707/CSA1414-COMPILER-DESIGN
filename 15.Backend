#include <stdio.h>
#include <conio.h>
#include <string.h>
void main()
{
	char code[10][30],str[20],opr[10];
	int i;
	printf("\nEnter the intermediate code:");
	do{
	scanf("%s",code[i]);
	}
	while(strcmp(code[i++],"exit")!=0);
	printf("\nTarget code generation");
	printf("\n*******************");
	i=0;
	do{
		strcpy(str,code[i]);
		switch(str[3]){
			case '+':
			strcpy(opr,"ADD");
			break;
			case '-':
			strcpy(opr,"SUB");
			break;
			case '*':
			strcpy(opr,"MUL");
			break;
			case '/':
			strcpy(opr,"DIV");
			break;
		}
		printf("\n\tMOV %c,R%d",str[2],i);
		printf("\n\t%s\t%c,R%d", opr,str[4],i);
		printf("\n\tMOV R%d,%c",i,str[0]);
	}
	while(strcmp(code[++i],"exit")!=0);
	getch();
}
