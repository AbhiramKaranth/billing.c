#include<stdio.h>
#include<stdlib.h>
//to do : accept name n stuff have inherent costs //also to change the values

struct account {
    int phn;
    char name[100];
    char adr[200];
    float total;


}details;

void main()
{
    printf("\n1.Create a new invoice :\n");
    printf("2.Check all the invoices:\n");
    int k;
    scanf("%d",&k);


    if(k==1)
    {
    printf("Select the items purchased and the quantity");
    printf("\n1.Mensinkaayi bonda:      Rs:20");
    printf("\n2.Aloo bajji:             Rs:20");
    printf("\n3.eerulli bajji:          Rs:15");
    printf("\n4.capsicum bajji:         Rs:15");
    printf("\n5.tea:                    Rs:05");
    printf("\n6.coffee:                 Rs:05");
    printf("\n7.kashaya:                Rs:10");
    printf("\n8.extra chutney:          Rs:02");
    
    printf("\nnumber of orders\n");
    int n,i,o1,o2,o3,sum;
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
            o3=o2*20;
            fprintf(fptr,"Mensinkaayi bonda\t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==2)
        {
            o3=o2*20;
            fprintf(fptr,"Aloo bajji       \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==3)
        {
            o3=o2*15;
            fprintf(fptr,"eerulli bajji    \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==4)
        {
            o3=o2*15;
            fprintf(fptr,"capsicum bajji   \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==5)
        {
            o3=o2*5;
            fprintf(fptr,"Tea              \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==6)
        {
            o3=o2*5;
            fprintf(fptr,"Coffee           \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==7)
        {
            o3=o2*10;
            fprintf(fptr,"Kashaya          \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        if(o1==8)
        {
            o3=o2*2;
            fprintf(fptr,"Extra chutney    \t\t\t\t%d\t\t\tRs:%d\n",o2,o3);
            sum=sum+o3;
        }

        i=i+1;
    }while(i<n);

    fclose(fptr);

    printf("\n\n\n\n");
    printf("\t\t\t---BARGOD BAJJI CENTRE---\t\t\t\n");
    printf("============================================================================\n");
    printf("Name:\t\t\t\tContact:\t\t\t\t\n");
    printf("address:\t\t\t\n");
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
    

    gptr=fopen("storage.txt","a+");
    
    fprintf(gptr,"\t\t\t---BARGOD BAJJI CENTRE---\t\t\t\n");
    fprintf(gptr,"============================================================================\n");
    fprintf(gptr,"Name:\t\t\t\tContact:\t\t\t\t\n");
    fprintf(gptr,"address:\t\t\t\n");
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

    









