~~~
Ex-4-GENERATION OF LEXICAL TOKENS LEX FLEX TOOL
AIM
 To write a lex program to implement lexical analyzer to recognize a few patterns.
 ALGORITHM
1.	Start the program.
2.	Lex program consists of three parts.
3.	Write a program in the vi editor and save it with .l extension.
4.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c
5.	Compile that file with C compiler and verify the output.
 Program 
/* program name is lexp.l */
%{
/* program to recognize a c program */
int COMMENT=0;
%}
identifier [a-zA-Z][a-zA-Z0-9]*
%%
#.* { printf("\n%s is a PREPROCESSOR DIRECTIVE",yytext);}
int |
float |
char |
double |
while |
for |
do |
if |
break |
continue |
void |
switch |
case |
else |
goto {printf("\n\t%s is a KEYWORD",yytext);}
"/*" {COMMENT = 1;}
 
"*/" {COMMENT = 0;}
{identifier}\( {if(!COMMENT)printf("\n\nFUNCTION\n\t%s",yytext);}
\} {if(!COMMENT) printf("\n BLOCK ENDS");}
\( ECHO;
= {if(!COMMENT)printf("\n\t%s is an ASSIGNMENT OPERATOR",yytext);}
\<= |
\>= |
\< |
== |
\> {if(!COMMENT) printf("\n\t%s is a RELATIONAL OPERATOR",yytext);}
%%
int main(int argc,char **argv)
{
if (argc > 1)
{
FILE *file;
file = fopen(argv[1],"r");
if(!file)
{
printf("could not open %s \n",argv[1]);
exit(0);
}
yyin = file;

} int yywrap()
{
return 0;
}
# INPUT
$vi var.c
#include<stdio.h>
main()
{
int a,b;
}
~~~
# OUTPUT
![image](https://github.com/niranjanadevi-s/Ex-4---GENERATION-OF-LEXICAL-TOKENS-LEX-FLEX-TOOL/assets/141748873/f512e016-d731-426a-b10a-49cbb1fad6a3)

# RESULT
The lexical analyzer is implemented using lex and the output is verified.

