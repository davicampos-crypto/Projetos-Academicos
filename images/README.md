# Pasta de Imagens

Esta pasta contém imagens de projetos desenvolvidos no Tinkercad e outras demonstrações visuais.

## Carrinho de controle remoto

<img width="1166" height="633" alt="image" src="https://github.com/user-attachments/assets/c3e7eee3-3821-434a-bcd8-7135203bc0eb" />

## Funcionamento:
Carrinho movido via bluetooth por aplicativo de celular, programado em linguagem C para microcontroladores.


## Jogo desenvolvido em placa lcd

<img width="676" height="358" alt="image" src="https://github.com/user-attachments/assets/7a21dff7-d952-4d94-9eca-e586c633325e" />

## Funcionamento:
Jogo programado em linguagem C para microcontroladores, cujo funcionamento consiste em acertar o alvo com uma seta, apertando os botões.

## codigo utilizado:
```cpp

#include <LiquidCrystal.h>
#define sobe 7 //define uma constante
#define desce 6 //define uma constante
bool alvoposicaoY=0;//define uma variavel
  byte flexaposicaoX=0;//define uma variavel
  byte flexaposicaoY=0;//define uma variavel
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);//entradas do lcd

void setup()
{
  pinMode(sobe, INPUT_PULLUP);//define o botao como entrada
      pinMode(desce, INPUT_PULLUP);//define o botao como entrada
  lcd.begin(16, 2); // seta o numero de colunas e lacunas do lcd
  lcd.setCursor(1, 0);//coloca o cursor na primeira linha 
lcd.print("JOGO DE DARDOS");//digita no lcd
  delay(2000);//espera um tempo
  lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("               ");//apaga o que estava escrito
}

void loop()
{
    
  bool cima = digitalRead(sobe);//define a variavel como a leitura digital do botao
  bool baixo = digitalRead(desce);//define a variavel como a leitura digital do botao
  if(cima ==0){//se o botao cima for pressionado
    flexaposicaoY=0;}//flexa vai para linha de cima
  if(baixo == 0){//se o botao baixo for pressionado
    flexaposicaoY=1;}//flexa vai pra baixo
flexaposicaoX++;//acrescenta em um o valor de posicao da flexa
   lcd.setCursor(15, alvoposicaoY);//coloca o cursor no alvo
  lcd.print(" ");//apaga o rastro do alvo

  alvoposicaoY=!alvoposicaoY;//irverte o valor da variavel booleana
  
   lcd.setCursor(flexaposicaoX-1, flexaposicaoY);//coloca o cursor na posição 
  lcd.print(" ");//apaga o rastro da flexa
   lcd.setCursor(flexaposicaoX-1, !flexaposicaoY);//coloca o cursor na posição
   lcd.print(" ");//apaga o rastro da flexa
  lcd.setCursor(flexaposicaoX, flexaposicaoY);//coloca o cursor na posição da flexa 
  
  lcd.print(">");//coloca a flexa 
  
  lcd.setCursor(15, alvoposicaoY);//coloca o cursor na posição
  lcd.print("O");//coloca o alvo no lugar
  delay(200);//espera um tempo
 ;

  if (flexaposicaoX==15){//se a flexa alcançar a posicao 15
    if(flexaposicaoY==alvoposicaoY){//se a flexa acertar o alvo
      lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("                ");//apaga o que estava escri
       lcd.setCursor(0, 1);//coloca o cursor na segunda linha 
  lcd.print("                ");//apaga o que estava escri
      lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
      lcd.print("    voce venceu");//declara vitoria
    delay(2000);//espera um tempo
    lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("               ");//apaga o que estava escrito
      lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
      lcd.print("tente novamente");//escreve tente novamente
      delay(2000);//espera um tempo
       lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("               ");//apaga o que estava escrito
        delay(2000);//espera um tempo
      flexaposicaoX=0;//define a posicao da flexa como 0
    }
    if(flexaposicaoY==!alvoposicaoY){//se a flexa errar o alvo
      lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("                ");//apaga o que estava escri
       lcd.setCursor(0, 1);//coloca o cursor na segunda linha 
  lcd.print("                ");//apaga o que estava escri
      lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
      lcd.print("    voce perdeu");//declara derrota
    delay(2000);//espera um tempo
    lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("               ");//apaga o que estava escrito
      lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
      lcd.print("tente novamente");//escreve no lcd
      delay(2000);//espera um tempo
       lcd.setCursor(0, 0);//coloca o cursor na primeira linha 
  lcd.print("               ");//apaga o que estava escrito
        delay(2000);//espera um tempo
      flexaposicaoX=0;//define a posicao da flexa como 0
    }
  } 
}
```
