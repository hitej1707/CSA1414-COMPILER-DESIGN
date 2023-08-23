%{
int pos_count=0;
int neg_count=0;
%}

%%

[0-9] {pos_count++;}

[-][0-9] {neg_count++;}

%%

int yywrap(){}
int main()
{
printf("enter the numbers");
yylex();
printf("number of positive are:%d\n",pos_count);
printf("number of negative are:%d\n",neg_count);
return 0;
}
