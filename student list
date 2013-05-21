#include "stdio.h"
#include "conio.h"
#include "string.h"
#include "windows.h"

/*Defines gotoxy() for ANSI C compilers.*/
void gotoxy(short x, short y) {
COORD pos = {x, y};
SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
}

void choose (char []);
void first_use (void);
int find_empty (void);
void stu_list (void);
void stu_add (void);
void stu_remove (void);
void stu_grade (void);
void stu_equ (int);
void stu_edit (void);;
void stu_copy (void);
void stu_search (void);
void danger_data (void);
int no_data_found (void);
void save_exit (void);
void load (void);
void user_pass (void);
void change_pass(void);

struct student_list {
        char firstname[20];
        char lastname[20];
        char fathername[20];
        char telphone[14];
        char email[50];
        char stu_num[8];
        char ID[11];
        int lesson;
        float score[24];
        float equ;
        char birthday[11];
}student[100];

struct grading_list {
    char firstname[20];
    char lastname[20];
    char stu_num[8];
    float equ;
}student_grade[100];

FILE *save;
FILE *up;

int main ()
{
    char ch[2];
    user_pass();
    first_use();
    load();
    while (1) {
        system("cls");
        printf("\n\n                                  STUDENT LIST");
        printf("\n                          by Saeed Motedaveli (8916123)");
        printf("\n\n             ------------------------------------------------------");
        printf("\n            |                           |                          |");
        printf("\n            |          1. List          |      2. Add Student      |");
        printf("\n            |                           |                          |");
        printf("\n            |------------------------------------------------------|");
        printf("\n            |                           |                          |");
        printf("\n            |        3. Edit Info       |     4. Remove Student    |");
        printf("\n            |                           |                          |");
        printf("\n            |------------------------------------------------------|");
        printf("\n            |                                                      |");
        printf("\n            |        5. Sort Student by \"grade point average\"      |");
        printf("\n            |                                                      |");
        printf("\n            |------------------------------------------------------|");
        printf("\n            |                           |                          |");
        printf("\n            |         6. Search         |      7. Save and Exit    |");
        printf("\n            |                           |                          |");
        printf("\n             ------------------------------------------------------");
        printf("\n\n                                your choice: ");
        scanf("%s",ch);
        system("cls");
        choose(ch);
    }
    return 0;
}




/* ************************************************************************************************************* choose menu:           */

void choose (char ch[])
{
    switch (ch[0])
        {
            case '1': { printf("                         ******************************");
                        printf("\n                         *       List Of Student      *");
                        printf("\n                         ******************************");    stu_list();     break; }

            case '2': { printf("                         ******************************");
                        printf("\n                         *         Add Student        *");
                        printf("\n                         ******************************");    stu_add();      break; }

            case '3': { printf("                         ******************************");
                        printf("\n                         *      Edit Student Info     *");
                        printf("\n                         ******************************");    stu_edit();     break; }

            case '4': { printf("                         ******************************");
                        printf("\n                         *       Remove Student       *");
                        printf("\n                         ******************************");    stu_remove();   break; }

            case '5': { printf("                         ******************************");
                        printf("\n                         *     Grade Point Average    *");
                        printf("\n                         ******************************");    stu_grade();    break; }

            case '6': { printf("                         ******************************");
                        printf("\n                         *     Search Student Info    *");
                        printf("\n                         ******************************");    stu_search();   break; }

            case '7': save_exit();

            case '8': { printf("                       **********************************");
                        printf("\n                       *   Change Username & Password   *");
                        printf("\n                       **********************************");    change_pass(); break; }

            default: {
                danger_data();
                printf("\n\n                            Wrong! Please try egain!");
                getch();
                }}
}




/* ********************************************************************************** first_use: zero name & lastname of all user:           */
void first_use (void)
{
    int i;
    for (i=0;i<100;i++)
    {
        student[i].firstname[0]='\0';
        student_grade[i].firstname[0]='\0';
        student[i].lastname[0]='\0';
        student_grade[i].lastname[0]='\0';
    }
}




/* *************************************************************************************** print list of student:           */

void stu_list (void)
{
    int i,k=1,n=5,r;
    r=no_data_found();
    if (r==0)
    {
        danger_data();
        printf("\n\n                                     No Data!");
        printf("\n\n                       you can add student from main menu.");
        getch();
    }

    printf("\n\n");
    if (r==1) {
        printf("--------------------------------------------------------------------------------\n");
        for (i=0;i<100;i++)
        {
            if (student[i].firstname[0]!='\0' || student[i].lastname[0]!='\0')
                {
                    gotoxy(1,n);
                    printf("%d. %s, %s",k,student[i].lastname,student[i].firstname);
                    gotoxy(15,n+2);
                    printf("Student Num.: %s",student[i].stu_num);
                    gotoxy(45,n+2);
                    printf("ID: %s",student[i].ID);
                    gotoxy(15,n+3);
                    printf("Birth Day: %s",student[i].birthday);
                    gotoxy(45,n+3);
                    printf("Tel: %s",student[i].telphone);
                    gotoxy(15,n+4);
                    printf("Email: %s",student[i].email);
                    gotoxy(15,n+5);
                    printf("Fader Name: %s",student[i].fathername);
                    gotoxy(45,n+5);
                    printf("GPA: %0.2f",student[i].equ);
                    printf("\n--------------------------------------------------------------------------------");
                    k++;
                    n=n+7;
                }

        }
        printf("Press Eny key to exit from List!");
        getch();
    }

}




/* ******************************************************************************************************** equal of each student:           */
void stu_equ (int i)
{
    int j;
    float sum=0,eql;
for (j=0;j<student[i].lesson;j++)
{
    sum+=student[i].score[j];
    eql=sum/student[i].lesson;
    student[i].equ=eql;
}
}




/* ******************************************************************************************* find empty list for add student:           */

int find_empty (void)
{
    int i=0,n;

    for (i=0;i<100 && (student[i].firstname[0]!='\0' || student[i].lastname[0]!='\0');++i);
    n=i;
    return n;
}




/* ************************************************************************************************** Add student to list:           */
void stu_add (void)
{
    int n,i,j=0;
    char p[2];
    n=find_empty();
    if (n<=99) {
        printf("\nEnter Name: ");
        gets(student[n].firstname);
        gets(student[n].firstname);

        printf("\nEnter Last Name: ");
        gets(student[n].lastname);

        printf("\nEnter Stu. Num (7digit): ");
        scanf("%s",student[n].stu_num);


        printf("\nEnter ID: ");
        scanf("%s",student[n].ID);

        printf("\nEnter Birth Day (yyyy/mm/dd): ");
        scanf("%s",student[n].birthday);

        printf("\nEnter Father Name: ");
        gets(student[n].fathername);
        gets(student[n].fathername);

        printf("\nEnter Tel Number: ");
        scanf("%s",student[n].telphone);

        printf("\nEnter E-Mail: ");
        scanf("%s",student[n].email);

        equ:
        printf("\nchoose one of the below options:\n\t1. equal of last term\n\t2. score of last term\n ");
        scanf("%s",p);
        if (p[0]=='1')
        {
            printf("equal of last term: ");
            scanf("%f",&student[n].equ);
        }
        else if (p[0]=='2')
        {
            printf("\nEnter Num. of Lesson (max=24): ");
            scanf("%d",&student[n].lesson);

            printf("\nEnter Score of Lessons:");
            for (i=0;i<(student[n].lesson);i++)
            {
                printf("\nLesson %d:",i+1);
                scanf("%f",&student[n].score[i]);
            }
            stu_equ(n);
            }
        else
        {
            printf("\nWrong input, Try again!\n");
            goto equ;
        }

    }

     if (n==99)
        {
            printf("\nNo Empty Line, Please remove some student");
            getch();
        }
}




/* *************************************************************************************************8*********** Remove student:           */
void stu_remove (void)
{
    int n=10,i,j,r,k;
    r=no_data_found();
    if (r==1) {
        printf("\n\n--------------------------------------------------------------------------------");
        printf("\n\t\t\t\tStudent List\n");
        printf("\n--------------------------------------------------------------------------------");
        for (i=0;i<100;i++)
            {
                if (student[i].firstname[0]!='\0' || student[i].lastname[0]!='\0')
                    {
                        gotoxy(1,n);
                        printf("%d. %s, %s",i,student[i].lastname,student[i].firstname);
                        gotoxy(25,n);
                        printf("Student Num.: %s",student[i].stu_num);
                        gotoxy(0,n+2);
                        printf("--------------------------------------------------------------------------------");
                        n=n+4;
                    }
            }

        printf("\nEnter student that you want to remove: ");
        scanf("%d",&j);
        if ((j>=0 && j<100)&& (student[j].firstname[0]!='\0' || student[j].lastname[0]!='\0')) {
        for (k=0;k<20;k++)
            student[j].firstname[k]='\0';
        for (k=0;k<20;k++)
            student[j].lastname[k]='\0';
        for (k=0;k<20;k++)
            student[j].fathername[k]='\0';
        for (k=0;k<14;k++)
            student[j].telphone[k]='\0';
        for (k=0;k<50;k++)
            student[j].email[k]='\0';
        for (k=0;k<8;k++)
            student[j].stu_num[k]='\0';
        for (k=0;k<11;k++)
            student[j].ID[k]='\0';
        for (k=0;k<11;k++)
            student[j].birthday[k]='\0';
        student[j].equ=0;

        printf("\n\n                       Done! Enter Eny Key to continue!");
        }
        else
            printf("\n\n                   Wrong, Please Enter Eny Key to continue!");
    }

    else
    {
        danger_data();
        printf("\n\n                                     No Data!");

    }
    getch();
}



/* ***************************************************************************************************** student Info Edit:           */
void stu_edit(void)
{
    int i,j=10,n,r;
    char cse[2];
    r=no_data_found();
    if (r==0) {
        danger_data();
        printf("\n\n                                     No Data!");
        }

    if (r==1) {
        printf("\n\n--------------------------------------------------------------------------------");
        printf("\n\t\t\t\tStudent List\n");
        printf("\n--------------------------------------------------------------------------------");
        for (i=0;i<100;i++)
            {
                if (student[i].firstname[0]!='\0' || student[i].lastname[0]!='\0')
                    {
                        gotoxy(1,j);
                        printf("%d. %s, %s",i,student[i].lastname,student[i].firstname);
                        gotoxy(25,j);
                        printf("Student Num.: %s",student[i].stu_num);
                        gotoxy(0,j+2);
                        printf("--------------------------------------------------------------------------------");
                        j=j+4;
                    }
            }
        printf("\nNo. of studedent that you want Edit info: ");
        scanf("%d",&n);

        if ((n>=0 && n<100)&& (student[n].firstname[0]!='\0' || student[n].lastname[0]!='\0')) {
            printf("\nEdit options:\n\t1. First name\n\t2. Last name\n\t3. Student No.\n\t4. ID\n\t5. Birth Day");
            printf("\n\t6. Father name\n\t7. Tel Number\n\t8. E-mail\n\t9. Equal of last term\n\nEnter Edit Options:");
            scanf("%s",&cse);
            choose:
            switch (cse[0])
            {
                case '1': printf("\nNEW: ");  student[n].firstname[0]='\0';        gets(student[n].firstname); gets(student[n].firstname);           break;
                case '2': printf("\nNEW: ");  student[n].lastname[0]='\0';         gets(student[n].lastname); gets(student[n].lastname);           break;
                case '3': printf("\nNEW: ");  student[n].stu_num[0]='\0';          scanf("%s",student[n].stu_num);       break;
                case '4': printf("\nNEW: ");  student[n].ID[0]='\0';               scanf("%s",student[n].ID);            break;
                case '5': printf("\nNEW: ");  student[n].birthday[0]='\0';         scanf("%s",student[n].birthday);      break;
                case '6': printf("\nNEW: ");  student[n].fathername[0]='\0';       gets(student[n].fathername); gets(student[n].fathername);         break;
                case '7': printf("\nNEW: ");  student[n].telphone[0]='\0';         scanf("%s",student[n].telphone);      break;
                case '8': printf("\nNEW: ");  student[n].email[0]='\0';            scanf("%s",student[n].email);         break;
                case '9': printf("\nNEW: ");  scanf("%f",&student[n].equ);         break;
                default:
                    {
                        printf("\n\n\t\t\tWrong,Please try egain!");
                        goto choose;
                    }
            }
            printf("\n\n                       Done! Enter Eny Key to continue!");
        }
        else
            printf("\n\n                   Wrong, Please Enter Eny Key to continue!");
        }
    getch();
}




/* ********************************************************************************************************* copy student_list to grading_list: */
void stu_copy(void)
{
    int i,j,k,n=16,l=1;

    for (i=0;i<100;i++)
    {
        strcpy(student_grade[i].firstname,student[i].firstname);
        strcpy(student_grade[i].lastname,student[i].lastname);
        strcpy(student_grade[i].stu_num,student[i].stu_num);
        student_grade[i].equ=student[i].equ;
    }
}




/* *********************************************************************************************************** Grading student:           */
void stu_grade (void)
{
    int i,j,k,n=10,l=1,r;
    r=no_data_found();
    if (r==0) {
        danger_data();
        printf("\n\n                                     No Data!");
        }

    if (r==1) {
    struct temp {
    char firstname[20];
    char lastname[20];
    char stu_num[8];
    float equ;
    }temp;

    stu_copy();
    for (i=99;i>0;i--)
        for (j=0;j<i;j++)
        if (student_grade[j].equ<student_grade[j+1].equ)
        {
            strcpy(temp.firstname,student_grade[j].firstname);
            strcpy(temp.lastname,student_grade[j].lastname);
            strcpy(temp.stu_num,student_grade[j].stu_num);
            temp.equ=student_grade[j].equ;
            student_grade[j]=student_grade[j+1];
            strcpy(student_grade[j+1].firstname,temp.firstname);
            strcpy(student_grade[j+1].lastname,temp.lastname);
            strcpy(student_grade[j+1].stu_num,temp.stu_num);
            student_grade[j+1].equ=temp.equ;
        }

    printf("\n\n--------------------------------------------------------------------------------");
    printf("\n\t\t\t\tStudent List\n");
    printf("\n--------------------------------------------------------------------------------");
    for (i=0;i<100;i++)
        {
            if (student_grade[i].firstname[0]!='\0' || student_grade[i].lastname[0]!='\0')
                {
                    gotoxy(1,n);
                    printf("%d. %s, %s",l,student_grade[i].lastname,student_grade[i].firstname);
                    gotoxy(25,n);
                    printf("Student Num.: %s",student_grade[i].stu_num);
                    gotoxy(25,n+2);
                    printf("Equal.: %0.2f",student_grade[i].equ);
                    gotoxy(0,n+4);
                    printf("--------------------------------------------------------------------------------");
                    n=n+6;
                    l++;
                }
        }
        printf("\n\nPress Eny Key to Exit!");
    }
        getch();

}




/* *********************************************************************************************************************** student info search: */
void stu_search(void)
{
    char student_search[20];
    int i,j=0,n=6,k=1,r;
    r=no_data_found();
    if (r==0) {
        danger_data();
        printf("\n\n                                     No Data!");
        }
    if (r==1) {
        printf("\nsaerch: ");
        scanf("%s",student_search);
        for (i=0;i<100;i++)
            {
            if (student[i].firstname[0]!='\0' || student[i].lastname[0]!='\0') {
            if (strcmp(student[i].firstname,student_search)==0)
            {
                j=1;
                gotoxy(1,n);
                printf("%d. %s, %s",k,student[i].lastname,student[i].firstname);
                gotoxy(25,n);
                printf("Student Num.: %s",student[i].stu_num);
                gotoxy(55,n);
                printf("ID: %s",student[i].ID);
                gotoxy(25,n+2);
                printf("Birth Day: %s",student[i].birthday);
                gotoxy(55,n+2);
                printf("Tel: %s",student[i].telphone);
                gotoxy(25,n+4);
                printf("Email: %s",student[i].email);
                gotoxy(25,n+6);
                printf("Father Name: ",student[i].fathername);
                gotoxy(55,n+6);
                printf("Equal: %0.2f",student[i].equ);
                n=n+11;
                k++;
            }
            else if (strcmp(student[i].lastname,student_search)==0)
            {
                j=1;
                gotoxy(1,n);
                printf("%d. %s, %s",k,student[i].lastname,student[i].firstname);
                gotoxy(25,n);
                printf("Student Num.: %s",student[i].stu_num);
                gotoxy(55,n);
                printf("ID: %s",student[i].ID);
                gotoxy(25,n+2);
                printf("Birth Day: %s",student[i].birthday);
                gotoxy(55,n+2);
                printf("Tel: %s",student[i].telphone);
                gotoxy(25,n+4);
                printf("Email: %s",student[i].email);
                gotoxy(25,n+6);
                printf("Equal: %0.2f",student[i].equ);
                n=n+11;
                k++;
            }
            else if (strcmp(student[i].stu_num,student_search)==0)
            {
                j=1;
                gotoxy(1,n);
                printf("%d. %s, %s",k,student[i].lastname,student[i].firstname);
                gotoxy(25,n);
                printf("Student Num.: %s",student[i].stu_num);
                gotoxy(55,n);
                printf("ID: %s",student[i].ID);
                gotoxy(25,n+2);
                printf("Birth Day: %s",student[i].birthday);
                gotoxy(55,n+2);
                printf("Tel: %s",student[i].telphone);
                gotoxy(25,n+4);
                printf("Email: %s",student[i].email);
                gotoxy(25,n+6);
                printf("Equal: %0.2f",student[i].equ);
                n=n+11;
                k++;
            }}}
    if (j==0) {
        printf("\n                                     ,..-..,\n                                  ,-`       `',");
        printf("\n                                .`    ,.-.,,   `,\n                               /   /``      `.   ,");
        printf("\n                               '  /           \\  \\\n                              |  /             ,  |");
        printf("\n                              |  |             |  |\n                              |  \\             '  |");
        printf("\n                               \\  \\            /  /\n                                \\  `.       ,'   ` ");
        printf("\n                                 .   `''-''`   ,` \n                                 /          _.`");
        printf("\n                                /    /''-''`\n                               /    /");
        printf("\n                              /    /\n                             /    /");
        printf("\n                            /    /\n                           |    /");
        printf("\n                            ',,/     Not found!");
    }}
    getch();
}




/* ************************************************************************************************************************** Danger print: */

void danger_data(void)
{
    printf("\n\n                               .----------------. ");
    printf("\n                              | .--------------. |");
    printf("\n                              | |      _       | |");
    printf("\n                              | |     | |      | |");
    printf("\n                              | |     | |      | |");
    printf("\n                              | |     | |      | |");
    printf("\n                              | |     |_|      | |");
    printf("\n                              | |      _       | |");
    printf("\n                              | |     (_)      | |");
    printf("\n                              | '--------------' |");
    printf("\n                               '----------------' ");
}

/* **************************************************************************************************************************** No data: */

int no_data_found (void)
{
    int i=0,j;
    for (j=0;j<100;j++) {
        if (student[j].firstname[0]!='\0' || student[j].lastname[0]!='\0')
            return 1;
        else
            i++;
    }
    if (i==100)
        return 0;
}

/* ********************************************************************  Save Data:*/
void save_exit (void)
{
    int i;
    save = fopen("stu_save.txt","w");
    if (!save)
    {
        printf("Cant Open File");
        getch();
        exit(1);
    }
    for (i=0;i<100;i++)
    {
        if (student[i].firstname || student[i].lastname)
            fwrite(&student[i],sizeof(struct student_list),1,save);
    }
    exit(0);
}

/* ************************************************ Load Data: */

void load(void)
{
    int i;
    save=fopen("stu_save.txt","r");
    if(!save)
        return;
    for (i=0;i<100;i++)
        fread(&student[i],sizeof(struct student_list),1,save);
}

/* **************************************************** Username & Password: */

void user_pass (void)
{
    int i;
    char user[11],user1[11],pass[11],pass1[11];
    up = fopen("up.bin","rb");
    if(!up)
    {
        for (i=0;i<11;i++)
            user[i]='\0';
        for (i=0;i<11;i++)
            pass[i]='\0';
        printf("\n\n                 First use: Please enter username and password:");
        printf("\n\n\n\n\t\t\t      Username: ");
        scanf("%s",user);
        for (i=0;i<10;i++)
            if (!user[i])
                user[i]='@';
        user[10]='\0';
        printf("\n\n\t\t\t      Password: ");
        scanf("%s",pass);
            for (i=0;i<10;i++)
                if (!pass[i])
                    pass[i]='@';
        pass[10]='\0';
        up = fopen("up.bin","wb");
        fputs(user,up);
        fputs(pass,up);
        fclose(up);
        return;
    }
    wrong:
    fgets(user1,11,up);
    fgets(pass1,11,up);
    for (i=0;i<11;i++)
        if (user1[i]=='@')
        user1[i]='\0';
    for (i=0;i<11;i++)
        if (pass1[i]=='@')
        pass1[i]='\0';
    printf("\n\n\n\n\t\t\tPlease Enter Username and Password:");
    printf("\n\n        For changing Username & Password please enter \"8\" in main menu!");
    printf("\n\n\n\n\t\t\t      Username: ");
    scanf("%s",user);
    printf("\n\n\t\t\t      Password: ");
    scanf("%s",pass);
    if ((strcmp(user,user1)==0) && (strcmp(pass,pass1)==0))
    {
        fclose(up);
        return;
    }

    else
    {
        system("cls");
        danger_data();
        printf("\n\n\t\t     Wrong Username or Password, Try again!");
        getch();
        system("cls");
        goto wrong;
    }
}

void change_pass (void)
{
    int i;
    char ch[2],user[11],user1[11],pass[11],pass1[11];
    up = fopen("up.bin","rb");
    fgets(user1,11,up);
    fgets(pass1,11,up);
    printf("\n\n\t\t\t\t1. Change Username\n\n\t\t\t\t2. Change Password\n\n\t\t\t\t  Your choice: ");
    scanf("%s",ch);
    if (ch[0]=='1')
    {
        for (i=0;i<10;i++)
            if (user1[i]=='@')
                user1[i]='\0';
        printf("\n\n\t\t\t  Current Username: ");
        scanf("%s",user);
        if (strcmp(user1,user)!=0)
            {
                system("cls");
                danger_data();
                printf("\n\n\t\t\t     Curent Username wrong!");
                getch();
                return;
            }
        for (i=0;i<11;i++)
            user1[i]='\0';
        printf("\n\n\t\t\t  New Username: ");
        scanf("%s",user1);
        for (i=0;i<10;i++)
            if (!user1[i])
                user1[i]='@';
        user1[10]='\0';
        up = fopen("up.bin","wb");
        fputs(user1,up);
        fputs(pass1,up);
        fclose(up);
        printf("\n\n\t\t\t\t      Done!");
        getch();
        return;
    }

    if (ch[0]=='2')
    {
        for (i=0;i<10;i++)
            if (pass1[i]=='@')
                pass1[i]='\0';
        printf("\n\n\t\t\t  Current Password: ");
        scanf("%s",pass);
        if (strcmp(pass1,pass)!=0)
            {
                system("cls");
                danger_data();
                printf("\n\n\t\t\t     Curent Password wrong!");
                getch();
                return;
            }
        for (i=0;i<11;i++)
            pass1[i]='\0';
        printf("\n\n\t\t\t  New Password: ");
        scanf("%s",pass1);
        for (i=0;i<10;i++)
            if (!pass1[i])
                pass1[i]='@';
        pass1[10]='\0';
        up = fopen("up.bin","wb");
        fputs(user1,up);
        fputs(pass1,up);
        fclose(up);
        printf("\n\n\t\t\t\t      Done!");
        getch();
        return;
    }
}
