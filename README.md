
// C program to implement
// the above approach
#include <conio.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include<windows.h>
 
// Declaring all the functions

void checkbalance(char*);

void transfermoney(void);

void display(char*);

void person(char*);

void login(void);

void loginsu(void);

void account(void);

void accountcreated(void);

void afterlogin(void);

void logout(void);
 
// Declaring gotoxy
// function for setting
// cursor position

void gotoxy(int x, int y)
{

    COORD c;

    c.X = x;

    c.Y = y;
 

    SetConsoleCursorPosition(

        GetStdHandle(STD_OUTPUT_HANDLE), c);
}
 
// Creating a structure to store
// data of the user

struct pass {

    char username[50];

    int date, month, year;

    char pnumber[15];

    char adharnum[20];

    char fname[20];

    char lname[20];

    char fathname[20];

    char mothname[20];

    char address[50];

    char typeaccount[20];
};
 
// Structure to keep track
// of amount transfer

struct money {

    char usernameto[50];

    char userpersonfrom[50];

    long int money1;
};
 

struct userpass {

    char password[50];
};
 
// Driver Code

int main()
{

    int i, a, b, choice;

    int passwordlength;
 

    gotoxy(20, 3);
 

    // Creating a Main

    // menu for the user

    printf("WELCOME TO BANK ACCOUNT SYSTEM\n\n");

    gotoxy(18, 5);
 

    printf("**********************************");

    gotoxy(25, 7);
 

    printf("DEVELOPER-Naman kumar");
 

    gotoxy(20, 10);

    printf("1.... CREATE A BANK ACCOUNT");
 

    gotoxy(20, 12);

    printf("2.... ALREADY A USER? SIGN IN");

    gotoxy(20, 14);
    printf("3.... EXIT\n\n");
 

    printf("\n\nENTER YOUR CHOICE..");
 

    scanf("%d", &choice);
 

    switch (choice) {

    case 1:

        system("cls");

        printf("\n\n USERNAME 50 CHARACTERS MAX!!");

        printf("\n\n PASSWORD 50 CHARACTERS MAX!!");

        account();

        break;
 

    case 2:

        login();

        break;
 

    case 3:

        exit(0);

        break;
 

        getch();

    }
}
 
// Function to create accounts
// of users

void account(void)
{

    char password[20];

    int passwordlength, i, seek = 0;

    char ch;

    FILE *fp, *fu;

    struct pass u1;

    struct userpass p1;
 

    struct userpass u2;
 

    // Opening file to

    // write data of a user

    fp = fopen("username.txt", "ab");
 

    // Inputs

    system("cls");

    printf("\n\n!!!!!CREATE ACCOUNT!!!!!");
 

    printf("\n\nFIRST NAME..");

    scanf("%s", &u1.fname);
 

    printf("\n\n\nLAST NAME..");

    scanf("%s", &u1.lname);
 

    printf("\n\nFATHER's NAME..");

    scanf("%s", &u1.fathname);
 

    printf("\n\nMOTHER's NAME..");

    scanf("%s", &u1.mothname);
 

    printf("\n\nADDRESS..");

    scanf("%s", &u1.address);
 

    printf("\n\nACCOUNT TYPE");

    scanf("%s", &u1.typeaccount);
 

    printf("\n\nDATE OF BIRTH..");

    printf("\nDATE-");

    scanf("%d", &u1.date);

    printf("\nMONTH-");

    scanf("%d", &u1.month);

    printf("\nYEAR-");

    scanf("%d", &u1.year);
 

    printf("\n\nADHAR NUMBER");

    scanf("%s", u1.adharnum);
 

    printf("\n\nPHONE NUMBER");

    scanf("%s", u1.pnumber);
 

    printf("\n\nUSERNAME.. ");

    scanf("%s", &u1.username);
 

    printf("\n\nPASSWORD..");
 

    // Taking password in the form of

    // stars
        printf(" ACCOUNT LOGIN ");

    gotoxy(7, 5);

    printf("***********************************************"

           "********************************");
 

    gotoxy(35, 10);

    printf("==== LOG IN ====");
 

    // Take input

    gotoxy(35, 12);

    printf("USERNAME.. ");

    scanf("%s", &username);
 

    gotoxy(35, 14);

    printf("PASSWORD..");
 

    // Input the password

    for (i = 0; i < 50; i++) {

        ch = getch();

        if (ch != 13) {

            password[i] = ch;

            ch = '*';

            printf("%c", ch);

        }
 

        else

            break;

    }
 

    // Checking if username

    // exists in the file or not

    while (fread(&u1, sizeof(u1),

                 1, fp)) {

        if (strcmp(username,

                   u1.username)

            == 0) {

            loginsu();

            display(username);

        }

    }
 

    // Closing the file

    fclose(fp);
}
 
// Redirect after
// successful login

            printf("MOBILE NUMBER..%s",

                   u1.pnumber);
 

            gotoxy(55, 20);

            printf("DATE OF BIRTH.. %d-%d-%d",

                   u1.date, u1.month, u1.year);
 

            gotoxy(55, 22);

            printf("ADDRESS..%s", u1.address);
 

            gotoxy(55, 24);

            printf("ACCOUNT TYPE..%s",

                   u1.typeaccount);

        }

    }
 

    fclose(fp);
 

    gotoxy(0, 6);
 

    // Menu to perform different

    // actions by user

    printf(" HOME ");

    gotoxy(0, 7);

    printf("******");

    gotoxy(0, 9);

    printf(" 1....CHECK BALANCE");

    gotoxy(0, 11);

    printf(" 2....TRANSFER MONEY");

    gotoxy(0, 13);

    printf(" 3....LOG OUT\n\n");

    gotoxy(0, 15);

    printf(" 4....EXIT\n\n");
 

    printf(" ENTER YOUR CHOICES..");

    scanf("%d", &choice);
 

    switch (choice) {

    case 1:

        checkbalance(username1);

        break;
 

    case 2:

        transfermoney();

        break;
 

    case 3:

        logout();

        login();

        break;
 

    case 4:

        exit(0);

        break;

    }
}
 
// Function to transfer
// money from one user to
// another

void transfermoney(void)
{

    int i, j;

    FILE *fm, *fp;

    struct pass u1;

    struct money m1;

    char usernamet[20];

    char usernamep[20];

    system("cls");
 

    // Opening file in read mode to

    // read user's username

    fp = fopen("username.txt", "rb");
 

    // Creating a another file

    // to write amount along with

    // username to which amount

    // is going to be transferred

    fm = fopen("mon.txt", "ab");
 

    gotoxy(33, 4);
        system("cls");

    FILE* fm;

    struct money m1;

    char ch;

    int i = 1, summoney = 0;
 

    // Opening amount file record

    fm = fopen("mon.txt", "rb");
 

    int k = 5, l = 10;

    int m = 30, n = 10;

    int u = 60, v = 10;
 

    gotoxy(30, 2);

    printf("==== BALANCE DASHBOARD ====");

    gotoxy(30, 3);

    printf("***************************");

    gotoxy(k, l);

    printf("S no.");

    gotoxy(m, n);

    printf("TRANSACTION ID");

    gotoxy(u, v);

    printf("AMOUNT");
 

    // Reading username to

    // fetch the correct record

    while (fread(&m1, sizeof(m1),

                 1, fm)) {

        if (strcmp(username2,

                   m1.usernameto)

            == 0) {

            gotoxy(k, ++l);

            printf("%d", i);

            i++;

            gotoxy(m, ++n);

            printf("%s", m1.userpersonfrom);
 

            gotoxy(u, ++v);

            printf("%d", m1.money1);

            // Adding and

            // finding total money

            summoney = summoney + m1.money1;

        }

    }
 

    gotoxy(80, 10);

    printf("TOTAL AMOUNT");
 

    gotoxy(80, 12);

    printf("%d", summoney);
 

    getch();
 

    // Closing file after

    // reading it

    fclose(fm);

    display(username2);
}
 
// Logout function to bring
// user to the login screen

void logout(void)
{

    int i, j;

    system("cls");

    printf("please wait, logging out");
 

    for (i = 0; i < 10; i++) {

        for (j = 0; j < 25000000; j++) {

            i++;

            i--;

        }

        printf(".");

    }
 

    gotoxy(30, 10);

    printf("Sign out successfully..\n");
 

    gotoxy(0, 20);

    printf("press any key to continue..");
 

    getch();
}
Bank.c
Displaying Bank.c.
