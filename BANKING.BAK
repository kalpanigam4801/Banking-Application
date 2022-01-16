#include<iostream.h>
#include<fstream.h>
#include<process.h>
#include<string.h>
#include<stdlib.h>
#include<stdio.h>
#include<ctype.h>
#include<conio.h>
#include<dos.h>
#include<iomanip.h>
#include<graphics.h>
//The menu class displays the menu
class Menus
{
 public:
  void showmenu(void);
 private:
  void closemenu();
  void end();
};
//The class displays all the Customer Account related functions
class dispRecords
{
 public:
  void addDetails(int,char name[30],char address[60],float);
  void displayCustomers(void);
  void deleteAccount(int);
  void updateBalance(int, float);
  void updateConsumer(void);
  int lastAccount(void);
  int accountExists(int);
  char *getName(int);
  char *getAddress(int);
  float getBalance(int);
  int getRecord(int);
  void display(int);
  void displayList(void);
  int AccountNumber;
  char name[50], address[60];
  float intBalance;
};
//The class has all the transaction related methods
class accountTransactions
{
 public:
  void new_account(void);
  void closeAccount(void);
  void display_account(void);
  void transaction(void);
  void addDetails(int, int, int, int, char, char typeTransaction[15], float, float, float);
  void deleteAccount(int);
  int dateDiffer(int, int, int, int, int, int);
  float getInterest(int, float);
  void display(int);
  void showAccount(int);
  int AccountNumber;//variable for account number
  char trantype[10];//variable of cheque or cash input or output
  int dday, mmonth, yyear;//transaction date
  char transactions;//type of transaction - deposit or withdrawal of amount
  float intInterest,intAmount,intBalance;
  static float calcInterest;
  void showInterest(void);//added
};
void Menus ::showmenu(void)
{
 int n;
 char ch;
 do
 {
  clrscr();
  textcolor(LIGHTRED);
  gotoxy(30,2);cprintf("BANKING APPLICATION");
  textcolor(YELLOW);
  gotoxy(26,6);cprintf("1. Open an Account");
  gotoxy(26,8);cprintf("2. View an Account");
  gotoxy(26,10);cprintf("3. Show all Accounts");
  gotoxy(26,12);cprintf("4. Make a Transaction");
  gotoxy(26,14);cprintf("5. Calculate Interest");
  gotoxy(26,16);cprintf("6. Close an Account");
  gotoxy(26,18);cprintf("7. Exit");
  textcolor(GREEN);
  gotoxy(26,22);cprintf("Enter your Choice:");
  cin>>n;
  textcolor(WHITE);
  clrscr();
  if(n>7)
  {
   cout<<"\n Invalid Choice";
   goto x;
  }
  switch(n)
 {
  case 1:
   accountTransactions objAT;
   objAT.new_account();
   clrscr();
   break;
  case 2:
   objAT.display_account();
   clrscr();
   break;
  case 3:
   dispRecords newRec;
   newRec.displayCustomers();
   clrscr();
   break;
  case 4:
   objAT.transaction();
   clrscr();
   break;
  case 5:
   objAT.showInterest();
   clrscr();
   break;
  case 6:
   closemenu();
   clrscr();
   break;
  case 7:
   end();
   exit(0);
   break;
  }
 x:cout<<"\n\n\a Back To Main Menu(y/n)?";
 cin>>ch;
 }while(ch=='y' || ch=='Y');
 if(ch=='n'|| ch=='N')
  end();
 getch();
}
//closemenu() method displays the Closing of the Account of the Customer in the Application
void Menus::closemenu(void)
{
 char choice;
 while(1)
 {
  clrscr();
  cout<<"           ----Close Menu---- \n";
  cout<<"          *********************** \n";
  cout<<"          1:Close/Delete an Account \n";
  cout<<"          0:Exit from this menu \n\n";
  cout<<"          Enter your Choice:  ";
  choice=getche();
  if(choice=='1')
  {
   getch();
   accountTransactions at;
   at.closeAccount();
   break;
  }
  else if(choice=='0')
  {
   cout<<" \n      Go Back to the Previous Menu.  \n";
   getch();
   break;
  }
 }
}
void Menus::end()
{
 int gdriver = DETECT, gmode, errorcode;
 initgraph(&gdriver, &gmode, "c:\\tc\\bgi");
 errorcode = graphresult();
 if(errorcode != grOk)  /* an error occurred */
 {
  printf("Graphics error: %s\n", grapherrormsg(errorcode));
  printf("Press any key to halt:");
  getch();
  exit(1);             /* return with error code */
 }
 fflush(stdin);
 setfillstyle(1,BLUE);
 rectangle(2,1,660,660);
 bar(2,1,660,660);
 setcolor(YELLOW);
 setlinestyle(1,0,3);
 settextstyle(1,0,8);
 settextjustify(LEFT_TEXT,TOP_TEXT);
 line(10,110,380,110);
 outtextxy(10,20,"C");
 settextstyle(4,0,8);
 outtextxy(47,20,"reated By:-");
 settextstyle(1,0,6);
 settextjustify(LEFT_TEXT,CENTER_TEXT);
 setcolor(YELLOW);
 settextstyle(1,0,4);
 outtextxy(90,170,"KALPA NIGAM ACHARYA");
 sleep(5);
 clrscr();
 getch();
}
//lastAccount() method returns the last Account Number from the newrecords.dat file.
int dispRecords::lastAccount(void)
{
 fstream filename ;
 filename.open("RECORDS.DAT", ios::in);
 filename.seekg(0, ios::beg);
 int count = 0;
 while(filename.read((char*)this,sizeof(dispRecords)))
 {
  count=AccountNumber;
 }
 filename.close();
 return count;
}
//getRecord() method returns the record no. from the newrecords.dat file when a banking staff enters the Account Number
int dispRecords::getRecord(int retrieve_AccNo)
{
 fstream filename;
 filename.open("RECORDS.DAT",ios::in);
 filename.seekg(0,ios::beg);
 int count=0;
 while(filename.read((char*)this,sizeof(dispRecords)))
 {
  count++;
  if(retrieve_AccNo==AccountNumber)
   break;
  //Keep on counting the record till the Account is found and exit from the newrecords.dat file.
 }
 filename.close();
 return count;
}
//display() method displays all the details of the amount no. from the newrecords.dat file
void dispRecords::display(int retrieve_AccNo)
{
 int record ;
 record = getRecord(retrieve_AccNo) ;
 fstream filename ;
 filename.open("RECORDS.DAT", ios::in);
 filename.seekg(0,ios::end);
 int location;
 location=(record)*sizeof(dispRecords);
 filename.seekp(location);
 while (filename.read((char*)this,sizeof(dispRecords)))
 {
  if (retrieve_AccNo==AccountNumber)
  {
   cout<<"\n      ACCOUNT NO.  :  " <<AccountNumber;
   cout<<"\n      Name  :  "<<name;
   cout<<"\n      Address  :  "<<address ;
   cout<<"\n      Balance  :  "<<intBalance ;
   break;
  }
 }
 filename.close() ;
}
//getName() method retruns the Account Holder's Name from the newrecords.dat file
char *dispRecords::getName(int retrieve_AccNo)
{
 fstream filename;
 filename.open("RECORDS.DAT", ios::in);
 filename.seekg(0,ios::beg);
 char retrieve_CustName[30];
 while (filename.read((char*) this , sizeof(dispRecords)))
 {
  if(AccountNumber==retrieve_AccNo)
  {
   strcpy(retrieve_CustName,name);
  }
 }
 filename.close();
 return retrieve_CustName;
}
//getAddress() method retruns the Address of the Account Holder from the newreacord.dat file
char *dispRecords:: getAddress(int retrieve_AccNo)
{
 fstream filename;
 filename.open("RECORDS.DAT",ios::in);
 filename.seekg(0,ios::beg);
 char retrieve_Address[60];
 while(filename.read((char*)this,sizeof(dispRecords)))
 {
  if(AccountNumber==retrieve_AccNo)
  {
   strcpy(retrieve_Address,address);
  }
 }
 filename.close();
 return retrieve_Address;
}
float dispRecords::getBalance(int retrieve_AccNo)
{
 fstream filename;
 filename.open("RECORDS.DAT",ios::in);
 filename.seekg(0,ios::beg);
 float iBalance;
 while(filename.read((char*)this,sizeof(dispRecords)))
 {
  if(AccountNumber==retrieve_AccNo)
  {
   iBalance=intBalance;
  }
 }
 filename.close();
 return iBalance;
}
int dispRecords::accountExists(int retrieve_AccNo)
{
 fstream filename;
 filename.open("RECORDS.DAT",ios::in);
 filename.seekg(0,ios::beg);
 int count=0;
 while(filename.read((char*)this,sizeof(dispRecords)))
 {
  if(AccountNumber==retrieve_AccNo)
  {
   count=1;
   break;
  }
 }
 filename.close();
 return count;
}
void dispRecords::displayList()
{
 cout<<"\n";
 int day1,month1,year1;
 struct date dateval;
 getdate(&dateval);
 day1=dateval.da_day;
 month1=dateval.da_mon;
 year1=dateval.da_year;
 cout<<"\nDate:"<<day1<<"/"<<month1<<"/"<<year1<<"\n";
 cout<<setw(80)<<"_____________________\n";
 cout<<setw(23)<<"ACCOUNT NO.";
 cout<<setw(23)<<"NAME OF PERSON:";
 cout<<setw(23)<<"BALANCE\n";
 cout<<setw(80)<<"______________________\n";
}
void dispRecords::displayCustomers(void)
{
 clrscr();
 int len1;
 int row=8,check;
 fstream filename;
 FILE*pFile;
 pFile=fopen("RECORDS.DAT","r");
 if(pFile==NULL)
 {
  cout<<"\n No Account exists.";
  cout<<"\n Go back to the previous menu.\n";
  getch();
  return;
 }
 else
 {
  displayList();
  filename.open("RECORDS.DAT",ios::in);
  filename.seekg(0,ios::beg);
  while(filename.read((char*)this,sizeof(dispRecords)))
  {
   check=0;
   cout.fill(' ');
   cout<<setw(20);
   cout.setf(ios::right,ios::adjustfield);
   cout<<AccountNumber;
   cout.fill(' ');
   cout<<setw(25);
   cout.setf(ios::right,ios::adjustfield);
   cout<<name;
   cout<<setw(23);
   cout.setf(ios::right,ios::adjustfield);
   cout<<intBalance<<"\n";
   row++;
   if(row==23)
   {
    check=1;
    row=8;
    cout<<"\n\n Continue the application...\n";
    getch();
    clrscr();
    displayList();
   }
  }
 }
 filename.close();
 if(!check)
 {
  cout<<"\n\n   Continue the application...\n";
  getch();
 }
}
void dispRecords::addDetails(int retrieve_AccNo,char retrieve_CustName[30],char retrieve_Address[60],float iBalance)
{
 AccountNumber=retrieve_AccNo;
 strcpy(name,retrieve_CustName);
 strcpy(address,retrieve_Address);
 intBalance=iBalance;
 fstream filename;
 filename.open("RECORDS.DAT",ios::out|ios::app);
 filename.write((char*)this,sizeof(dispRecords));
 filename.close();
}
void dispRecords::deleteAccount(int retrieve_AccNo)
{
 fstream filename;
 filename.open("RECORDS.DAT",ios::in);
 fstream temp;
 temp.open("calculations.txt",ios::out);
 filename.seekg(0,ios::beg);
 while(!filename.eof())
 {
  filename.read((char*)this,sizeof(dispRecords));
  if(filename.eof())
   break;
  if(AccountNumber!=retrieve_AccNo)
   temp.write((char*)this,sizeof(dispRecords));
 }
 filename.close();
 temp.close();
 filename.open("RECORDS.DAT",ios::out);
 temp.open("calculations.txt",ios::in);
 temp.seekg(0,ios::beg);
 while(!temp.eof())
 {
  temp.read((char*)this,sizeof(dispRecords));
  if(temp.eof())
   break;
  filename.write((char*)this,sizeof(dispRecords));
 }
 filename.close();
 temp.close();
}
void dispRecords::updateBalance(int retrieve_AccNo,float iBalance)
{
 int record;
 record=getRecord(retrieve_AccNo);
 fstream filename;
 filename.open("RECORDS.DAT",ios::out|ios::ate);
 intBalance=iBalance;
 int location;
 location=(record-1)*sizeof(dispRecords);
 filename.seekp(location);
 filename.write((char*)this,sizeof(dispRecords));
 filename.close();
}
void accountTransactions::addDetails(int retrieve_AccNo,int day1,int month1,int year1,char t_tran,char typeTransaction[10],float interest_accrued,float t_amount,float iBalance)
{
 fstream filename;
 filename.open("transactions.dat",ios::app);
 AccountNumber=retrieve_AccNo;
 dday=day1;
 mmonth=month1;
 yyear=year1;
 transactions=t_tran;
 strcpy(trantype,typeTransaction);
 intInterest=interest_accrued;
 intAmount=t_amount;
 intBalance=iBalance;
 filename.write((char*)this,sizeof(accountTransactions));
 filename.close();
}
void accountTransactions::deleteAccount(int retrieve_AccNo)
{
 fstream filename;
 filename.open("transactions.dat",ios::in);
 fstream temp;
 temp.open("calculations.txt",ios::out);
 filename.seekg(0,ios::beg);
 while(!filename.eof())
 {
  filename.read((char*)this,sizeof(accountTransactions));
  if(filename.eof())
   break;
  if(AccountNumber!=retrieve_AccNo)
   temp.write((char*)this,sizeof(accountTransactions));
 }
 filename.close();
 temp.close();
 filename.open("transactions.dat",ios::out);
 temp.open("calculations.txt",ios::in);
 temp.seekg(0,ios::beg);
 while(!temp.eof())
 {
  temp.read((char*)this,sizeof(accountTransactions));
  if(temp.eof())
   break;
  filename.write((char*)this,sizeof(accountTransactions));
 }
 filename.close();
 temp.close();
}
void accountTransactions::new_account(void)
{
 char choice;
 int i,check;
 clrscr();
 dispRecords newRec;
 cout<<"Press 0 to go back to previous menu.\n";
 cout<<"\n";
 cout<<" Open a New Bank Account-\n";
 cout<<"*************************\n";
 int day1,month1,year1;
 struct date dateval;
 getdate(&dateval);
 day1=dateval.da_day;
 month1=dateval.da_mon;
 year1=dateval.da_year;
 int retrieve_AccNo;
 retrieve_AccNo=newRec.lastAccount();
 retrieve_AccNo++;
 if(retrieve_AccNo==1)
 {
  newRec.addDetails(retrieve_AccNo,"Ravi","Delhi",1.1);
  newRec.deleteAccount(retrieve_AccNo);
  addDetails(retrieve_AccNo,1,1,1997,'D',"default value",1.1,1.1,1.1);
  deleteAccount(retrieve_AccNo);
 }
 char retrieve_CustName[30],tran_acc[10],retrieve_Address[60];
 float t_bal,iBalance;
 cout<<"Date:"<<day1<<"/"<<month1<<"/"<<year1<<endl;
 cout<<"Account no.#"<<retrieve_AccNo;
 do
 {
  cout<<"\n\n Enter the Name of the Account Holder:";
  check=1;
  gets(retrieve_CustName);
  if(retrieve_CustName[0]=='0')
  {
   cout<<"\n\t Invalid Customer Name.";
   getch();
   return;
  }
  strupr(retrieve_CustName);
  if(strlen(retrieve_CustName)==0||strlen(retrieve_CustName)>30)
  {
   check=0;
   cout<<"\t\n Customer Name is either blank or its length is greater than 30 characters.\n";
   getch();
  }
}while (!check);
 char FName[30];
 int day,month,year;
 unsigned long PhNo;
 cout<<" Enter Date of Birth: "<<endl;
 cout<<" Enter Day: ";
 cin>>day;
 cout<<" Enter Month: ";
 cin>>month;
 cout<<" Enter Year: ";
 cin>>year;
 if(day/10==0 && month/10==0)
  cout<<" Date of Birth: "<<"0"<<day<<"/"<<"0"<<month<<"/"<<year<<endl;
 else if(day/10==0)
  cout<<" Date of Birth: "<<"0"<<day<<"/"<<month<<"/"<<year<<endl;
 else if(month/10==0)
  cout<<" Date of Birth: "<<day<<"/"<<"0"<<month<<"/"<<year<<endl;
 else
  cout<<" Date of Birth: "<<day<<"/"<<month<<"/"<<year<<endl;
 cout<<" Enter Father's Name: ";
 gets(FName);
 cout<<" Enter Phone Number: ";
 cin>>PhNo;
 do
 {
  cout<<"\n Enter the Account Holder's Address:";
  check=1;
  gets(retrieve_Address);
  if(retrieve_Address[0]=='0')
  {
   cout<<"\n\t Invalid Customer Address.";
   getch();
   return;
  }
  strupr(retrieve_Address);
  if(strlen(retrieve_Address)<1||strlen(retrieve_Address)>60)
  {
   check=0;
   cout<<"\t\n Customer Address is either blank or its length is greater than 60 characters.\n";
   getch();
  }
}while (!check);
 do
 {
  char chr_VerifyingPerson[30];
  cout<<"\n Enter the Name of Verifying Person :";
  check=1;
  gets(chr_VerifyingPerson);
  if(chr_VerifyingPerson[0]=='0')
  {
   cout<<"\n\t Invalid Verifying Person Name";
   getch();
   return;
  }
  strupr(chr_VerifyingPerson);
  if(strlen(chr_VerifyingPerson)<1||strlen(chr_VerifyingPerson)>30)
  {
   check=0;
   cout<<"\t\n The Verifying Person's Name is either blank or its length is greater than 30 characters.\n";
   getch();
  }
}while(!check);
 do
 {
  cout<<"\n Enter the Deposit Amount:Rs.";
  check=1;
  gets(tran_acc);
  t_bal=atof(tran_acc);
  iBalance=t_bal;
  if(strlen(tran_acc)<1)
  {
   cout<<"\n Invalid Transaction value";
   getch();
   return;
  }
  if(iBalance<1000)
  {
   check=0;
   cout<<"\n\t The Minimum Deposit Amount should be Rs.1000. Please try again.\n";
   getch();
  }
}while(!check);
 do
 {
  cout<<"\n Do you want to save the record (y/n)?";
  choice=getche();
  choice=toupper(choice);
}while(choice!='N'&&choice!='Y');
 if(choice=='N'||choice=='n')
 {
  cout<<"\n The Customer Account is not created";
  getch();
  return;
 }
 float t_amount, interest_accured ;
 t_amount=iBalance;
 interest_accured=0.0;
 char t_tran, typeTransaction[10] ;
 t_tran='D';
 strcpy(typeTransaction," ");
 newRec.addDetails(retrieve_AccNo, retrieve_CustName, retrieve_Address, iBalance);
 addDetails(retrieve_AccNo, day1, month1, year1, t_tran, typeTransaction, interest_accured, t_amount, iBalance);
 cout<<"\n\n The New Account is successfully created";
 getch();
}
//ShowAccount() method formats the display of the records from (the transactions.dat) file for a particular account(choice2).
void accountTransactions::showAccount(int retrieve_AccNo)
{
 cout<<"\n";
 int day1, month1, year1;
 struct date dateval;
 getdate(&dateval);
 day1=dateval.da_day;
 month1=dateval.da_mon;
 year1=dateval.da_year;
 cout<<"Date: "<<day1<<"/"<<month1<<"/"<<year1<<"\n";
 cout<<"Account no."<<retrieve_AccNo;
 dispRecords newRec;
 char retrieve_CustName[30];
 strcpy(retrieve_CustName,newRec.getName(retrieve_AccNo));
 char retrieve_Address[60];
 strcpy(retrieve_Address,newRec.getAddress(retrieve_AccNo));
 cout<<setw(25)<<"\n Account Holder's Name:"<<retrieve_CustName;
 cout<<"\n Address:"<<retrieve_Address<<"\n";
 cout<<setw(80)<<"\n________________________________________\n";
 cout<<setw(10)<<"Dated";
 cout<<setw(12)<<"Details";
 cout<<setw(12)<<"Deposited";
 cout<<setw(15)<<"Withdrawn";
 cout<<setw(12)<<"      ";
 cout<<setw(10)<<"Balance";
 cout<<setw(80)<<"\n__________________________________________\n";
}
//display_account() method displays records from the transactions.dat file
void accountTransactions::display_account(void)
{
 clrscr();
 int tran_acc,retrieve_AccNo;
 dispRecords obj2;
 cout<<"  Press 0 to go back to previous menu.\n";
 cout<<"  Enter Account No. you want to view:";
 cin>>tran_acc;
 retrieve_AccNo=tran_acc;
 if(retrieve_AccNo==0)
 {
  cout<<"\n You have pressed 0 to exit.\n";
  getch();
  return;
 }
 clrscr();
 dispRecords newRec;
 accountTransactions aa;
 int row=8, check;
 fstream filename;
 FILE *pFile;
 pFile=fopen("RECORDS.DAT","r");
 if(pFile==NULL)
 {
  cout<<"\n No such Account Exists. Please Create a New Account.\n";
  getch();
  return;
 }
 else if(!newRec.accountExists(retrieve_AccNo))
 {
  cout<<"\n\t Account does not exist.\n";
  getch();
  return;
 }
 else
 {
  showAccount(retrieve_AccNo);
  filename.open("transactions.dat",ios::in);
  while(filename.read((char*) this,sizeof(accountTransactions)))
  {
   if(AccountNumber==retrieve_AccNo)
   {
    check=0;
    cout<<setw(3)<<dday<<"/"<<mmonth<<"/"<<yyear;
    cout<<setw(10)<<trantype;
    if(transactions=='D')
    {
     cout.setf(ios::right,ios::adjustfield);
     cout<<setw(15);
     cout<<intAmount;
     cout<<setw(20);
     cout<<" ";
    }
    else
    {
     cout.setf(ios::right,ios::adjustfield);
     cout<<setw(25);
     cout<<intAmount;
     cout<<setw(10);
     cout<<" ";
    }
    cout<<setw(15);
    cout.setf(ios::right,ios::adjustfield);
    cout<<intBalance<<"\n";
    row++;
    if(row==23)
    {
     check=1;
     row=8;
     cout<<"\n\n Continue with the application.\n";
     getch();
     clrscr();
     showAccount(retrieve_AccNo);
    }
   }
  }
 }
 filename.close();
 if(!check)
 {
  cout<<"\n\n Press any key to continue with the application. \n";
  getch();
 }
}
int accountTransactions::dateDiffer(int day1,int month1,int year1,int day2,int month2,int year2)
{
 static int monthArr[]={31,28,31,30,31,31,30,31,30,31};
 int days =0;
 while (day1!=day2||month1!=month2||year1!=year2)
 {
  days++;
  day1++;
  if(day1>monthArr[month1-1])
  {
   day1=1;
   month1++;
  }
  if(month1>12)
  {
   month1=1;
   year1++;
  }
 }
 return days;
}
float accountTransactions::getInterest(int retrieve_AccNo,float iBalance)
{
 fstream filename;
 filename.open("transactions.dat", ios::in);
 dispRecords newRec;
 filename.seekg(0,ios::beg);
 while (filename.read((char*) this, sizeof(accountTransactions)))
 {
  if(AccountNumber==retrieve_AccNo)
  {
   iBalance=newRec.getBalance(retrieve_AccNo);
   break;
  }
 }
 float interest_accrued,Rate;
 int No_of_months;
 cout<<"\n Enter Rate of Interest (in %):";
 cin>>Rate;
 cout<<"\n Enter the Number of Months: ";
 cin>>No_of_months;
 interest_accrued=((iBalance*Rate*No_of_months)/1200);
 filename.close();
 return interest_accrued;
}
void accountTransactions::showInterest(void)
{
 clrscr();
 int tran_acc,retrieve_AccNo,check;
 cout<<strupr("\n Important Information:Interest should be generated only \n once in a Year.\n\n\t If you have already generated interest for an Account,\n\t please ignore that Account.\n\t Thank you.\n");
 cout<<"\n Press 0 to go back to previous menu.\n";
 cout<<"\n To view the transaction of the Account,please enter it: ";
 cin>>tran_acc;
 retrieve_AccNo=tran_acc;
 if(retrieve_AccNo==0)
  return;
 clrscr();
 dispRecords newRec;
 if(!newRec.accountExists(retrieve_AccNo))
 {
  cout<<"\t\n Account does not exist.\n";
  getch();
  return;
 }
 cout<<"           Press 0 to go back to previous menu.\n";
 cout<<"                                               \n";
 cout<<"\n         Enter the Account no.to generate interest-   \n";
 cout<<" ******************************************************** \n";
 int day1,month1,year1;
 struct date dateval;
 getdate(&dateval);
 day1=dateval.da_day;
 month1=dateval.da_mon;
 year1=dateval.da_year;
 cout<<"           Date: "<<day1<<"/"<<month1<<"/"<<year1<<"\n";
 cout<<"           Account no. "<<retrieve_AccNo<<"\n";
 char retrieve_CustName[30];
 char retrieve_Address[60];
 float iBalance;
 strcpy(retrieve_CustName,newRec.getName(retrieve_AccNo));
 strcpy(retrieve_Address,newRec.getAddress(retrieve_AccNo));
 iBalance=newRec.getBalance(retrieve_AccNo);
 cout<<"\n           Customer Name:    "<<retrieve_CustName;
 cout<<"\n           Customer Address:    "<<retrieve_Address;
 cout<<"\n           Bank Balance:    "<<iBalance;
 float interest_accrued;
 interest_accrued=getInterest(retrieve_AccNo,iBalance);
 cout<<"\n\tInterest generated:Rs."<<interest_accrued;
 getch();
 iBalance=iBalance+interest_accrued;
 dispRecords obj2;
 obj2.updateBalance(retrieve_AccNo,iBalance);
 addDetails(retrieve_AccNo,day1,month1,year1,'D',"Interest",interest_accrued,interest_accrued,iBalance);
}
void accountTransactions::transaction(void)
{
 clrscr();
 int tran_acc,retrieve_AccNo,check;
 cout<<"           Press 0 to go back to previous menu.\n";
 cout<<"           To view the transaction of the Account,enter it: ";
 cin>>tran_acc;
 retrieve_AccNo=tran_acc;
 if(retrieve_AccNo==0)
  return;
 clrscr();
 dispRecords newRec;
 if(!newRec.accountExists(retrieve_AccNo))
 {
  cout<<"\t\n      Account does not exist.\n";
  getch();
  return;
 }
 cout<<"           Press 0 to go back to previous menu.\n";
 cout<<"                                                         \n";
 cout<<"\n         Make correct entry for the Transaction below-    \n";
 cout<<" **********************************************\n";
 int day1,month1,year1;
 struct date dateval;
 getdate(&dateval);
 day1=dateval.da_day;
 month1=dateval.da_mon;
 year1=dateval.da_year;
 cout<<"           Date: "<<day1<<"/"<<month1<<"/"<<year1<<endl;
 cout<<"           Account No. "<<retrieve_AccNo<<"\n";
 char retrieve_CustName[30];
 char retrieve_Address[60];
 float iBalance;
 float interest_accrued=0.0;
 strcpy(retrieve_CustName,newRec.getName(retrieve_AccNo));
 strcpy(retrieve_Address,newRec.getAddress(retrieve_AccNo));
 iBalance=newRec.getBalance(retrieve_AccNo);
 cout<<"\n           Customer Name:    "<<retrieve_CustName;
 cout<<"\n           Customer Address:    "<<retrieve_Address;
 cout<<"\n           Bank Balance:    "<<iBalance;
 char tranDetails,typeTransaction[10],tm[10];
 float t_amount,t_amt;
 do
 {
  cout<<"\n        Enter D for Deposit or W for Withdrawal of Amount: ";
  tranDetails=getche();
  if(tranDetails=='0')
  {
   cout<<"\n\n     You have pressed 0 to Exit.";
   getch();
   return;
  }
 tranDetails=toupper(tranDetails);
 } while(tranDetails!='W' && tranDetails!='D');
 do
 {
  cout<<"\n        The Transaction type is either Cash or Cheque..\n";
  check=1;
  cout<<"          (Cash/Cheque): ";
  gets(typeTransaction);
  strupr(typeTransaction);
  if(typeTransaction[0]=='0')
  {
   cout<<"\n\n     You have pressed 0 to Exit.";
   getch();
   return;
  }
  if(strlen(typeTransaction)<1||(strcmpi(typeTransaction,"CASH") && strcmpi(typeTransaction,"CHEQUE")))
  {
   check=0;
   cout<<"\n       The Transaction is invalid. Enter either CASH or CHEQUE. \n";
   getch();
  }
 }while(!check);
 do
 {
  cout<<"\n        Enter the Transaction Amount:    \n";
  check=1;
  cout<<"          Amount:Rs. ";
  gets(tm);
  t_amt=atof(tm);
  t_amount=t_amt;
  if(t_amount<1||(tranDetails=='W' && t_amount>iBalance))
  {
   check=0;
   cout<<"\n       Either Amount is not a numeric value or\n it is blank or\n you are trying to withdraw amount more than in the Account..... \n";
   getch();
  }
 }while(!check);
 char choice;
 do
 {
  cout<<"\n        Save the changes made in the transaction details? (y/n): ";
  choice=getche();
  choice=toupper(choice);
 }while(choice!='N' && choice!='Y');
 if(choice=='N' || choice=='n')
 {
  cout<<"\n        The Transaction is not saved. \n";
  getch();
  return;
 }
 if(tranDetails=='D')
 {
  cout<<"\n        The Amount is Deposited in the Bank.\n";
  getch();
  iBalance=iBalance+t_amount;
 }
 else
 {
  cout<<"\n        The Amount is Withdrawn  from the Bank.\n";
  getch();
  iBalance=iBalance-t_amount;
 }
 newRec.updateBalance(retrieve_AccNo,iBalance);
 addDetails(retrieve_AccNo,day1,month1,year1,tranDetails,typeTransaction,interest_accrued,t_amount,iBalance);
}
void accountTransactions::closeAccount(void)
{
 clrscr();
 char t_acc[10];
 int tran_acc,retrieve_AccNo;
 cout<<"           Press 0 to go back to previous menu.\n";
 cout<<"           Enter the Account you want to close: ";
 gets(t_acc);
 tran_acc=atoi(t_acc);
 retrieve_AccNo=tran_acc;
 clrscr();
 dispRecords newRec;
 if(!newRec.accountExists(retrieve_AccNo))
 {
  cout<<"\t\n      You have entered an invalid Account or it does not exist.\n";
  cout<<"          Please Try Again.\n";
  getch();
  return;
 }
 cout<<"\n           Press 0 to go back to previous menu.\n";
 cout<<"\n           Closing this Account.\n";
 cout<<"**************************************\n\n";
 int day1,month1,year1;
 struct date dateval;
 getdate(&dateval);
 day1=dateval.da_day;
 month1=dateval.da_mon;
 year1=dateval.da_year;
 cout<<"             Date: "<<day1<<"/"<<month1<<"/"<<year1<<endl;
 char choice;
 newRec.display(retrieve_AccNo);

 do
 {
  cout<<"\n          Are you sure you want to close this Account? (y/n): ";
  choice=getche();
  choice=toupper(choice);
 } while(choice!='N' && choice!='Y');

 if(choice=='N' || choice=='n')
 {
  cout<<"\n          The Account is not closed.\n";
  getch();
  return;
 }
 newRec.deleteAccount(retrieve_AccNo);
 deleteAccount(retrieve_AccNo);
 cout<<"\t\n\n       Record Deleted Successfully.\n";
 getch();
}
int login(void)
{
 char username[9],ch;
 char username1[]="banking";
 int i=0;
 char a,b[9],pass[]="davburla";
 cout<<"\n\n";
 textcolor(LIGHTRED);
 gotoxy(30,6);cprintf("BANKING APPLICATION");
 textcolor(YELLOW);
 gotoxy(26,6);cprintf("Login to the Banking Application");
 gotoxy(20,8);cprintf("**********************************************");
 gotoxy(26,12);cprintf("Enter Username: ");
 gets(username);
 gotoxy(26,14);cprintf("Enter Password: ");
 fflush(stdin);
 do
 {
  ch=getch();
  if(isalnum(ch))
  {
   b[i]=ch;
   cout<<"*";
   i++;
  }
  else
   if(ch=='\r')
    b[i]='\0';
   else if(ch=='\b')
   {
    i--;
    cout<<"\b\b";
   }
  } while(ch!='\r');
 b[i]='\0';
 fflush(stdin);
 if((strcmp(b,pass)==0) && (strcmp(username1,username)==0))
 {
  cout<<"\n\n\t      You have entered successfully\n\n";
  return(1);
 }
 else
 {
  gotoxy(26,16);cprintf("Incorrect Username or Password.");
  cout<<"\n";
  return(0);
 }
}
void main()
{
 clrscr();
 int val,ch;
 a: val=login();
 if(val==0)
 {
  gotoxy(26,18);cprintf("Want to try again?");
  gotoxy(26,20);cprintf("1.Try Again");
  gotoxy(26,22);cprintf("2.Exit");
  cout<<endl;
  gotoxy(26,24);cprintf("Enter your choice: ");
  cin>>ch;
  if(ch==1)
  {
   clrscr();
   goto a;
  }
  else
  {
   exit(0);
  }
 }
 Menus obj1;
 obj1.showmenu();
}















