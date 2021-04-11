# Hotel-Management-System

#include <stdio.h>

#include <string.h>

#include <conio.h>

#include <stdlib.h>

#include <ctype.h>

#include <windows.h>

void setcolor(int ForgC)

{

    WORD wColor;

    HANDLE hStdOut = GetStdHandle(STD_OUTPUT_HANDLE);

    CONSOLE_SCREEN_BUFFER_INFO csbi;

    if (GetConsoleScreenBufferInfo(hStdOut, &csbi))

    {

        wColor = (csbi.wAttributes & 0xB0) + (ForgC & 0x0B);

        //	SetConsoleTextAttributes(hStdOut,wColor);

        SetConsoleTextAttribute(hStdOut, wColor);
    }
}

void strt();

void hotelStaff();

void HSLOGIN();

void user();

void login();

void aflo();

void book();

void status();

void reg();

void add();

void disp();

void option();

void delete1();

void edit();

struct HM
{
    char name[100];
    char email[100];
    char id[100];
    char num[10];
    char stay[200];
    char nor[3];
} s;

int main()

{

    strt();

    getch();

    return 0;
}
void strt()

{

    // SetTextColor(1);

    int ch;

    system("COLOR 0C");

    printf("\n");
    printf(" ------------------------------------------------------------------------\n");
    printf("|                                                                        |\n");
    printf("|                                                                        |\n");
    printf("|  OOOOOO  OOOOOO OOOOOO OOOOOO OOOOOO OOOOOO O      O OOOOOOO  OOOOOO   |\n");
    printf("|  O       O    O O      O        O      O    O O    O O        O        |\n");
    printf("|  O  OOO  OOOOOO OOOOO  OOOOO    O      O    O  O   O O  OOOO  OOOOOO   |\n");
    printf("|  O    O  O  0   O      O        O      O    O   O  O O     0       0   |\n");
    printf("|  OOOOOO  O   O  OOOOOO OOOOOO   O    OOOOOO O    O O OOOOOO0  OOOOOO   |\n");
    printf("|                                                                        |\n");
    printf(" ------------------------------------------------------------------------\n");

    printf("\n\n***************************************\n\n");

    printf("\n\n=========Welcome to the system=========\n\n");

    printf("\n\n***************************************\n\n");

    printf("Enter your choice\n\n");

    printf("1]For Customer\n\n");

    printf("2]For Hotel Staff\n\n");

    printf("0]to exit\n");

    scanf("%d", &ch);

    switch (ch)

    {

    case 1:
        login();
        break;

    case 2:
        HSLOGIN();
        break;

        // case 3:
        //     reg();
        //     break;

    case 0:
        exit(0);
        break;

    default:

        printf("Invalid input\n");

        printf("Try Again!");

        break;
    }

    main();
}




void reg()
{
    FILE *fp1;

    char test;

    fp1 = fopen("registration.txt", "a+");

    if (fp1 == 0)

    {
        fp1 = fopen("registration.txt", "w+");

        system("cls");

        printf("Please hold on while we set your database in our computer!!");

        printf("\n Process completed press any key to continue!! ");

        getch();
    }
    while (1)

    {

        system("cls");

        printf("*************************************");

        printf("========REGISTRATION PORATAL=========");

        printf("*************************************");

        printf("\n Enter Customer Details:");

        printf("\n**************************\n");

        fflush(stdin);

        printf("Enter Name:\n");

        scanf("%s", s.name);

        printf("Enter Phone Number:\n");

        scanf("%s", s.num);

        printf("Enter Email:\n");

        scanf(" %s", s.email);

        printf("Enter the ID id:\n");

        scanf("%s", s.id);

        fwrite(&s, sizeof(s), 1, fp1);

        fflush(stdin);

        printf("\n Press esc key to exit,  any other key to add another customer detail:\n\n");

        test = getche();

        if (test == 27)

            break;
    }

    fclose(fp1);

    book();
}



void login()
{

    int a = 0, i = 0;

    char uname[10], c = ' ';

    char pword[10], code[10];

    char user[10] = "user";

    char pass[10] = "pass";

    do

    {

        system("cls");

        printf("\n\n*********************************\n\n");

        printf("\n\n=========LOGIN PORTAL============\n\n");

        printf("\n\n*********************************\n\n");

        printf("Status::CUSTOMER\n");

        printf("\nENTER USERNAME:-");

        scanf("%s", &uname);

        printf("\nENTER PASSWORD:-");

        while (i < 10)

        {

            pword[i] = getch();

            c = pword[i];

            if (c == 13)
                break;

            else

                printf("*");

            i++;
        }

        pword[i] = '\0';

        //char code=pword;
        i = 0;
        //scanf("%s",&pword);
        if (strcmp(uname, user) == 0 && strcmp(pword, pass) == 0)

        {
            printf("  \n\n\n       WELCOME !!!! LOGIN IS SUCCESSFUL\n\n");
            aflo();
        }

        else

        {
            printf("\n        SORRY !!!!  LOGIN IS UNSUCESSFUL\n\n");
            printf("\n        Enter any key to try again\n");
            a++;
            getch();
        }

    }

    while (a <= 2);

    if (a > 2)

    {

        printf("\nSorry you have entered the wrong username and password for four times!!!");

        getch();
    }

    system("cls");
}

void HSLOGIN()
{

    int a = 0, i = 0;

    char uname[10], c = ' ';

    char pword[10], code[10];

    char user[10] = "hsuser";

    char pass[10] = "hspass";

    do

    {

        system("cls");

        printf("\n\n*********************************\n\n");

        printf("\n\n=========LOGIN PORTAL============\n\n");

        printf("\n\n*********************************\n\n");

        printf("\nStatus::HOTEL STAFF\n");

        printf(" \nENTER USERNAME:-");

        scanf("%s", &uname);

        printf(" \nENTER PASSWORD:-");

        while (i < 10)

        {

            pword[i] = getch();

            c = pword[i];

            if (c == 13)
                break;

            else

                printf("*");

            i++;
        }

        pword[i] = '\0';

        //char code=pword;
        i = 0;
        //scanf("%s",&pword);
        if (strcmp(uname, user) == 0 && strcmp(pword, pass) == 0)

        {
            printf("  \n\n\n       WELCOME !!!! LOGIN IS SUCCESSFUL\n\n");
            hotelStaff();
        }

        else

        {
            printf("\n        SORRY !!!!  LOGIN IS UNSUCESSFUL\n\n");
            printf("\n        Enter any key to try again\n");
            a++;
            getch();
        }

    }

    while (a <= 2);

    if (a > 2)

    {

        printf("\nSorry you have entered the wrong username and password for four times!!!");

        getch();
    }

    system("cls");
}

void aflo()

{

    int c;

    printf("1]To register for booking a room\n\n");

    printf("2]To check the status of your booking\n\n");

    printf("0]To exit the system\n\n");

    scanf("%d", &c);

    switch (c)

    {
    case 1:
        reg();
        break;

    case 2:
        status();
        break;

    case 0:
        exit(0);
        break;

    default:
        break;
    }
}
void book()

{
    FILE *fp1;

    char name[100];

    char num[100];

    char id[100];

    char stay[1000];

    char nor[3];

    system("cls");

    printf("\n\n**************************************\n\n");

    printf("\n\n============BOOKING PORTAL============\n");

    printf("\n\n**************************************\n\n");

    printf("Enter the following details to book the rooms\n\n");

    char test;

    fp1 = fopen("status.txt", "a+");

    if (fp1 == 0)

    {
        fp1 = fopen("status.txt", "w+");

        system("cls");

        printf("Please hold on while we set your database in our computer!!");

        printf("\n Process completed press any key to continue!! ");

        getch();
    }
    while (1)

    {

        system("cls");

        printf("\n Enter Customer Details:");

        printf("\n**************************\n");

        fflush(stdin);

        printf("Enter Name:\n");

        scanf("%s", s.name);

        printf("Enter Phone Number:\n");

        scanf("%s", s.num);

        printf("Enter Email:\n");

        scanf(" %s", s.email);

        printf("Enter the ID id:\n");

        scanf("%s", s.id);

        printf("Enter the number of rooms you want to book: \n");

        scanf("%s",s.nor);

        printf("Enter the purpose of stay: \n");

        scanf("%s",s.stay);

        fwrite(&s, sizeof(s), 1, fp1);

        fflush(stdin);

        printf("\n Press esc key to exit,  any other key to add another customer detail:\n\n");

        test = getche();

        if (test == 27)

            break;
    }

    fclose(fp1);

    strt();
}

void hotelStaff()

{

    int ans;

    printf("Enter the choice you want to do\n");

    printf("1]To display the list of customers\n");

    printf("2]To add any customer detail\n");

    printf("3]To delete any customer detail\n");

    printf("4]To edit any customer detail\n");

    printf("0]To exit the system\n");

    scanf("%d", &ans);

    switch (ans)
    {
    case 1:
        disp();
        break;

    case 2:
        add();
        break;

    case 3:
        delete1();
        break;

    case 4:
        edit();
        break;

    case 0:
        exit(0);
        break;

    default:
        printf("Invalid Input\n");
        break;
    }
    strt();
}

void disp()
{
    FILE *f;
    int i;
    if ((f = fopen("status.txt", "r")) == NULL)
        exit(0);
    system("cls");

    printf("NAME\t ");

    printf("\tPHONENUMBER\t ");

    printf("\tEMAIL\t ");

    printf("\t\tID NUMBER \n");

    for (i = 0; i < 118; i++)
        printf("-");
    while (fread(&s, sizeof(s), 1, f) == 1)
    {
        /*
		printf("NAME:\t%s\n",,s.name);
	
		printf("PHONENUMBER:\t%s\n",s.phonenumber);

        printf("Email:%s",s.email);
		*/
        printf("\n%s \t\t%s   \t%s  \t%s  \n ", s.name, s.num, s.email,s.id);
    }
    printf("\n");
    for (i = 0; i < 118; i++)
        printf("-");

    fclose(f);
    printf("\n\nEnter any key to go back to main menu\n");
    getch();
    strt();
}

void user()

{

    int uinp;

    printf("Do you want to book rooms for your stay\n\n1 for yes\n\n0 for no\n\n");

    scanf("%d", &uinp);

    if (uinp == 1)

    {

        book();
    }

    else if (uinp == 0)

    {

        exit(0);
    }

    strt();
}

void option()
{
    int inp;

    printf("Do you want you add any data\n\n1 for yes\n\n0 for no\n\n");

    scanf("%d", &inp);

    if (inp == 1)

    {

        add();
    }

    else if (inp == 0)

    {

        exit(0);
    }

    strt();
}

void status()
{
    FILE *fp;

    char idn[100];

    int n;
    
    fp = fopen("status.txt", "r+");

    printf("Enter your ID number : ");

    scanf("%s", idn);

    if (strcmp(s.id,idn)==0)
    {
        printf("\nYour rooms have been succesfully booked\n");

        printf("Enter any key to continue\n");
        getch();
    }
    else
    {
        printf("\nSorry! you don't have a booking in the hotel\n");

        printf("Enter any key to continue\n");

        getch();
    }

    printf("Enter 1 to go back to the menu\n");

    printf("Enter 0 to exit the system\n");

    scanf("%d",&n);

    switch (n)
    {

    case 1:
        aflo();
        break;

    case 0:
        exit(0);
        break;

    default:
        printf("Invalid input\n");
        break;
    }
}

void add()
{
    FILE *fp1;

    char test;

    fp1 = fopen("status.txt", "a+");

    if (fp1 == 0)

    {
        fp1 = fopen("status.txt", "w+");

        system("cls");

        printf("Please hold on while we set your database in our computer!!");

        printf("\n Process completed press any key to continue!! ");

        getch();
    }
    while (1)

    {

        system("cls");

        printf("\n Enter Customer Details:");

        printf("\n**************************\n");

        fflush(stdin);

        printf("Enter Name:\n");

        scanf("%s", s.name);

        printf("Enter Phone Number:\n");

        scanf("%s", s.num);

        printf("Enter Email:\n");
        scanf(" %s", s.email);

        printf("Enter the ID number:\n");

        scanf("%s", s.id);

        printf("Enter the number of rooms you want to book\n");

        scanf("%d", s.nor);

        printf("Enter the purpose of your stay: ");

        scanf("%s", s.stay);

        fwrite(&s, sizeof(s), 1, fp1);

        fflush(stdin);

        printf("\n\nRoom is successfully booked!!");

        printf("\n Press esc key to exit,  any other key to add another customer detail:\n\n");

        test = getche();

        if (test == 27)

            break;
    }

    fclose(fp1);

    strt();
}

void delete1()
{
    FILE *f, *t;

    int i = 1;

    char id[20];

    if ((t = fopen("temp.txt", "w")) == NULL)

        exit(0);

    if ((f = fopen("status.txt", "r")) == NULL)

        exit(0);

    system("cls");

    printf("Enter the ID number of the hotel to be deleted from the database: \n");

    fflush(stdin);

    scanf("%s", id);

    while (fread(&s, sizeof(s), 1, f) == 1)

    {

        if (strcmp(s.id, id) == 0)

        {
            i = 0;
            continue;
        }

        else
        {
            fwrite(&s, sizeof(s), 1, t);
        }
    }

    if (i == 1)

    {

        printf("\n\n Records of Customer of this  ID number is not found!!");

        printf("\n\nEnter any key to go back to main menu\n");

        //remove("E:/file.txt");
        //rename("E:/temp.txt","E:/file.txt");
        getch();

        fclose(f);

        fclose(t);

        main();
    }

    fclose(f);

    fclose(t);

    remove("status.txt");

    rename("temp.txt", "status.txt");

    printf("\n\nThe Customer is successfully removed....\n\n");

    printf("Enter any key to go back to main menu\n");

    fclose(f);

    fclose(t);

    getch();

    strt();
}

void edit()
{
    FILE *f;

    int k = 1;

    char id[20];

    long int size = sizeof(s);

    if ((f = fopen("status.txt", "r+")) == NULL)

        exit(0);

    system("cls");

    printf("Enter ID number of the customer to edit:\n\n");

    scanf("%s", id);

    fflush(stdin);

    while (fread(&s, sizeof(s), 1, f) == 1)

    {

        if (strcmp(s.id, id) == 0)

        {

            k = 0;

            printf("\nEnter Name : \n");
            fflush(stdin);
            scanf("%s", &s.name);

            printf("\nEnter Phone number : \n");
            scanf("%f", &s.num);

            printf("\nEnter Email :");
            scanf("%s", &s.email);

            printf("\nEnter number of rooms booked : \n");
            scanf("%s",s.nor);

            printf("\nEnter the purpose of stay : \n");
            scanf("%s",s.stay);

            fseek(f, size, SEEK_CUR); 
            fwrite(&s, sizeof(s), 1, f);
            break;
        }
    }

    if (k == 1)
    {

        printf("\n\nTHE RECORD DOESN'T EXIST!!!!");
        
        fclose(f);
        getch();
    }
    else
    {
        fclose(f);
        printf("\n\n\t\tYOUR RECORD IS SUCCESSFULLY EDITED!!!");

        printf("Press any key to go back to menu\n");
        getch();
        strt();
    }
}
