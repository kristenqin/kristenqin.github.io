第六周 java编程环境搭建

> 先尝试直接找一个java cloud工具

```java

/*
Online Java - IDE, Code Editor, Compiler

Online Java is a quick and easy tool that helps you to build, compile, test your programs online.
*/
import java.io.*;
class Parser{
    static int lookahead;
    public Parser() throws IOException{
        lookahead = System.in.read();
    }
    void expr() throws IOException{
        term();
        while(true){
            if(lookahead == '+'){
                match('+');term();System.out.write('+');
            }
            else if(lookahead == '-'){
                match('-');term();System.out.write('-');
            }
            else return;
        }
    }
    void term() throws IOException{
        if(Character.isDigit((char)lookahead)){
            System.out.write((char)lookahead);match(lookahead);
        }
        else throw new Error("syntax error");
    }
    void match(int t) throws IOException{
        if(lookahead == t) lookahead = System.in.read();
        else throw new Error("syntax error");
    }
}
public class Main
{
    public static void main(String[] args) throws IOException{
        Parser parse = new Parser();
        parse.expr();
        System.out.write('\n');
    }
}

```



