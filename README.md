999999# Cafe-manager

#include<stdio.h> 
#include<math.h>
#include<string.h>

//Fuctions For Bill Desigh & For order checking Respectively
void desighOfBill(char name[100],char date[20],char GSTIN[20],char add[100],int order[100],int Paquantity,int Baquantity,int Caquantity,int Faquantity,int sum);
void checkOrder(int order[100],char Garbage[5000]);
void checkOrderForLoop(int order[100],char Garbage[5000],int i);

int main(){

//Variable for taking order
int order[100];

//Varibles for taking input of quantity of each item 
int Pquantity[100];
int Bquantity[100];
int Cquantity[100];
int Fquantity[100];

//Variables For Adding Quantity to sum
int Paquantity = 0;
int Baquantity = 0;
int Caquantity = 0;
int Faquantity = 0;

//Variable for storing garbage
char Garbage[5000];

//Variable for taking response of order from user
char response;

//Variable for calculating sum
int sum = 0;

//Variables For bill details
char name[100];
char date[20] = "06/06/2024";
char GSTIN[20] = "27ABCDE1234H1Z5";
char add[100] = "Near Devkrupa Petrol Pump,Alandi";
 
// Welcome of the user
printf(" \n\t\t\t\t\t\t\tWelcome to Vedant's Cafe!\n");

printf("\n");

//Menu-list
printf(" Our Menu-List : \n\n");
printf(" Pizza = 100Rs\n Burger = 60Rs\n Coffee = 80Rs\n French Frice = 40Rs\n \n\n");

printf("Enter What do You Want : ");
    scanf("%d",&order[0]);

//Conditions for checking user's input is mentioned in our Menu-list or not
if (order[0] == 1 || order[0] == 2 || order[0] == 3 || order[0] == 4)
{
    
}
else{
    checkOrder(order,Garbage);
}

//Taking quantity of items  
printf("Enter it's quantity : ");

if(order[0] == 1){
scanf("%d",&Pquantity[0]);
Paquantity += Pquantity[0];
}

if(order[0] == 2){
scanf("%d",&Bquantity[0]);
Baquantity += Bquantity[0];
}

if(order[0] == 3){
scanf("%d",&Cquantity[0]);
Caquantity += Cquantity[0];
}

if(order[0] == 4){
scanf("%d",&Fquantity[0]);
Faquantity += Fquantity[0];
}

printf("\n");

//Loop for taking multiple orders from user(Same logic as above)
for(int i = 1; 1; i++){
    printf("Do you want anything else(Yes/No) : ");
    scanf(" %c",&response);
    fgets(Garbage,5000,stdin);
 
    printf("\n");

    if(response == 'Y' || response == 'y'){
    printf("Enter What do You Want : ");
    scanf("%d",&order[i]);
    
    if (order[i] == 1 || order[i] == 2 || order[i] == 3 || order[i] == 4)
{
    
}
else{
       checkOrderForLoop(order,Garbage,i);
}
                 
    printf("Enter it's quantity : ");


   if(order[i] == 1){
   scanf(" %d",&Pquantity[i]);
   Paquantity += Pquantity[i];
}

  if(order[i] == 2){
   scanf(" %d",&Bquantity[i]);
   Baquantity += Bquantity[i];
}

  if(order[i] == 3){
   scanf(" %d",&Cquantity[i]);
   Caquantity += Cquantity[i];
}

  if(order[i] == 4){
   scanf(" %d",&Fquantity[i]);
   Faquantity += Fquantity[i];
}
  printf("\n");
    }
    if (response == 'N' || response == 'n'){
    printf("\nYour Order Placed Successfully!\n\n");
    break; 
    }
    
}

//Calculating sum
sum += 100 * Paquantity;
sum += 60 * Baquantity;
sum += 80 *Caquantity;
sum += 90 * Faquantity;

 //Function call for bill
desighOfBill(name,date,GSTIN,add,order,Paquantity,Baquantity,Caquantity,Faquantity,sum);

 return 0;
}

//Function to print bill
void desighOfBill(char name[100],char date[20],char GSTIN[20],char add[100],int order[100],int Paquantity,int Baquantity,int Caquantity,int Faquantity,int sum) {

//Heading of the bill
printf(" \n\t\t\t\t   Vedant's Cafe!\n\t\t\t%s\n",add);
printf("\t   --------------------------------------------------------------\n");

//Printing Bill details
printf("GSTIN : %s\nContact No. : 9767133965\nDate : %s\n",GSTIN,date);

printf("---------------------------------------------------------------------------------------\n");

printf(" Name\t\t\t Qty\t\t\t MRP\t\t\t Total\n");

printf("---------------------------------------------------------------------------------------\n");

//Loop for printing Order of the user
for(int i = 0; order[i] != '\0'; i++){

    if(order[i] == 1){
    printf("Pizza\t\t\t  %d\t\t\t100 Rs\t\t\t %d Rs\n",Paquantity,100 * Paquantity);
    break;
    }
}


for(int i = 0; order[i] != '\0'; i++){
    if(order[i] == 3){
    printf("Coffee\t\t\t  %d\t\t\t80 Rs\t\t\t %d Rs\n",Caquantity,80 * Caquantity);
    break;
    }
}

for(int i = 0; order[i] != '\0'; i++){
    if(order[i] == 2){
    printf("Burger\t\t\t  %d\t\t\t60 Rs\t\t\t %d Rs\n",Baquantity,60 * Baquantity);
    break;
    }
}

for(int i = 0; order[i] != '\0'; i++){
    if(order[i] == 4){
    printf("French Frice\t\t  %d\t\t\t90 Rs\t\t\t %d Rs\n",Faquantity,90 * Faquantity);
    break;
    }
}

float GST = sum * 0.05;
float totalPrice = sum + GST;

printf("---------------------------------------------------------------------------------------\n");

//Printing GST
printf("\t\t\t\t\t\t\t\t\t %d Rs\n\t\t\t\t\t\t\tGST\t\t %.2f Rs\n",sum,GST);

printf("---------------------------------------------------------------------------------------\n");

//Printing total amount with gst
printf("\t\t\t\t\t\t\tTotal Amt\t %.2f Rs\n",totalPrice);

printf("---------------------------------------------------------------------------------------\n");

printf(" \n\t\t\t      Thank You! Visit Again!\n");
}

 //Function to check order taken first time(Above the loop which is taking multiple orders)
void checkOrder(int order[100],char Garbage[5000]) {
    order[0] = '\0';
    printf("Enter Anything Mentioned in the Menu-List : ");
    scanf("%d",&order[0]);

if (order[0] == 1 || order[0] == 2 || order[0] == 3 || order[0] == 4)
{
    
}
else{
       checkOrder(order,Garbage);
}
}
//Function to check order taken in loop
void checkOrderForLoop(int order[100],char Garbage[5000],int i){
    order[i] = '\0';
    printf("Enter Anything Mentioned in the Menu-List : ");
    scanf("%d",&order[i]);

if (order[i] == 1 || order[i] == 2 || order[i] == 3 || order[i] == 4)
{
    
}
else{
       checkOrderForLoop(order,Garbage,i);
}
} 
