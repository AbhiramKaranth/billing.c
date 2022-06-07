#include<stdio.h>
#include<stdlib.h>



void main()
{
    

    printf("\n1.Create a new invoice :\n");
    printf("2.Check all the invoices:\n");
    int k;
    printf("what do u want to do?\n");
    scanf("%d",&k);


    if(k==1)
    {
    long long int m;
    char nm[100],ad[100];
    printf("\nenter the name:");
    scanf("\n%s",&nm);
    printf("enter the number:");
    scanf("%llu",&m);
    printf("\nenter the address:");
    scanf("\n%s",&ad);


    printf("Select the items purchased and the quantity");
    printf("\n1.Dal Makhni:             Rs:250");
    printf("\n2.Kadhai Paneer:          Rs:350");
    printf("\n3.Paneer Butter Masala:   Rs:300");
    printf("\n4.Crispy Chilli BabyCorn: Rs:180");
    printf("\n5.Honey Chilli Potato:    Rs:120");
    printf("\n6.Butter Naan:            Rs:35");
    printf("\n7.Kulcha:                 Rs:40");
    printf("\n8.Desserts:               Rs:100");
    
    printf("\nnumber of orders\n");
    int n,i,o1,o2,o3,sum,grandtotal;
    sum=0;
    i=0;
    scanf("%d",&n);

    FILE *fptr ;
    FILE *gptr;

    fptr =fopen("bjji.txt","w+");
    do{
        printf("order number and quantity:");
        scanf("%d %d",&o1,&o2);

        if(o1==1)
        {
            o3=o2*250;
            fprintf(fptr,"Dal Makhni         \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==2)
        {
            o3=o2*350;
            fprintf(fptr,"Kadhai Paneer        \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==3)
        {
            o3=o2*300;
            fprintf(fptr,"Paneer Butter Masala  \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==4)
        {
            o3=o2*180;
            fprintf(fptr,"Crispy Chilli BabyCorn\t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==5)
        {
            o3=o2*120;
            fprintf(fptr,"Honey Chilli Potato    \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==6)
        {
            o3=o2*35;
            fprintf(fptr,"Butter Naan            \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==7)
        {
            o3=o2*40;
            fprintf(fptr,"Kulcha                 \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==8)
        {
            o3=o2*100;
            fprintf(fptr,"Desserts               \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        i=i+1;
    }while(i<n);
    grandtotal= 0.18*sum +sum;

    fclose(fptr);

    printf("\n\n\n\n");
    printf("\t\t\t---TAJ EXOTICA---\t\t\t\n");
    printf("============================================================================\n");
    printf("Name:%s\t\t\t\tContact:%llu\t\t\t\t\n",nm,m);
    printf("address:%s\t\t\t\n",ad);
    printf("============================================================================\n");
    printf("ITEM\t\t\t\t\t\tQTY\t\t\tCOST\n");

    char c;
    fptr = fopen("bjji.txt","r");
    if (fptr == NULL)
    {
        printf("Cannot open file \n");
        exit(0);

    }
    c=fgetc(fptr);
    while (c!= EOF)
    {
        printf ("%c",c);
        c=fgetc(fptr);
    }

    fclose(fptr);
    printf("TOTAL:\t\t\t\t\t\t\t\t\tRs:%d",sum);
    printf("\n============================================================================\n");
    printf("\nGST@18%");
    printf("\nGrandTotal:\t\t\t\t\t\t\t\tRs:%d",grandtotal);
    
    
    printf("\n============================================================================\n");
    

    gptr=fopen("storage.txt","a+");
    
    fprintf(gptr,"\t\t\t---TAJ EXOTICA---\t\t\t\n");
    fprintf(gptr,"============================================================================\n");
    fprintf(gptr,"Name:%s\t\t\t\tContact:%llu\t\t\t\t\n",nm,m);
    fprintf(gptr,"address:%s\t\t\t\n",ad);
    fprintf(gptr,"============================================================================\n");
    fprintf(gptr,"ITEM\t\t\t\t\t\tQTY\t\t\tCOST\n");
    fclose(fptr);

    char ch;
    FILE *source, *target;
    char source_file[]="bjji.txt";
    char target_file[]="storage.txt";
    source = fopen(source_file, "r");
    if (source == NULL) {
       printf("Press any key to exit...\n");
       exit(EXIT_FAILURE);
    }
    target = fopen(target_file, "a");
    if (target == NULL) {
       fclose(source);
       printf("Press any key to exit...\n");
       exit(EXIT_FAILURE);
    }
    while ((ch = fgetc(source)) != EOF)
       fputc(ch, target);
    printf("File copied successfully.\n");
    fclose(source);
    fclose(target);
    
    gptr=fopen("storage.txt","a+");
    fprintf(gptr,"TOTAL:\t\t\t\t\t\t\t\t\t\tRs:%d",sum);
    fprintf(gptr,"\n============================================================================\n");
    fprintf(gptr,"\nGST@18");
    fprintf(gptr,"\nGrandTotal:\t\t\t\t\t\t\t\tRs:%d",grandtotal);
    fprintf(gptr,"\n============================================================================\n\n\n\n");
    fclose(fptr);
    }

    if(k==2){
        FILE *kptr;

        char g;
        kptr = fopen("storage.txt","r");
        if (kptr == NULL)
        {
            printf("Cannot open file \n");
            exit(0);

        }
        g=fgetc(kptr);
        while (g!= EOF)
        {
            printf ("%c",g);
            g=fgetc(kptr);
        }

        fclose(kptr);

    }

    
}

    









