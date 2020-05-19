# Adatszerkezetek-1
#MAIN.c

#include <stdio.h>
#include <stdlib.h>
#include "egersajt.h"

int main()
{
    /*egersajt* E1 = Create(); /// Letre hozom az elso palyat!
    E1 = Beolvas(E1,"be.txt"); /// Beolvasom az elso palyat
    printf("\n");
    Rajzol(E1); ///Kezdodik a jatek.*/

    egersajt* E1, *E2, *E3; ///Deklaralom es letrehozok 3 egersajt strukt tipusu valtozot, ami szukseges lesz a 3 szinthez

        ///A bementei allomanyokban megvan adva a palya merete, a lepesek maximalis szama,
        ///a sajtok szama, a palya maga, az eger X Y koordinatai es a sajt/sajtok X Y koordinatai

    E1 = Create(); E1 = Beolvas(E1, "be.txt");
    E2 = Create(); E2 = Beolvas(E2, "be2.txt"); ///itt beolvasom a 3 kulonbozo palyat
    E3 = Create(); E3 = Beolvas(E3, "be3.txt");


    int p,b=0; ///A jatekmenet folytonositasahoz szukseges valtozok
    char k;  ///Enter vagy Esc billentyuk lenyomasahoiz szukseges

    printf("Eger-Sajtos jatek\nJuttasd el az egeret a sajthoz!");
    printf("\n  Jatekmenet:\n   W, A, S, D billentyuket hasznalva, leptetni lehet az egeret.\n");
    printf("Minden szintnel megvan adva az eger lepeseinek a maximalis szama.\n");

    printf("Nyomj egy 'Enter' billentyuzetet a tovabblepeshez!");
                if(_getch())
                    system("cls");

    printf("Ket kulonbozo nehezsegi fok kozul lehet valasztani:\n   Konnyu fokozat 1-es billentyu!\n    Nehez fokozat 2-es billentyu!\n                 Sok sikert!!\n");
    int f = 0;
    scanf("%d",&f);
    if(f == 1){  ///Itt dontom el, hogy konnyu vagy nehez fokozatot valasztott a felhasznalo
        while(k != 27){
            printf("Opciok:\n   Nyomd meg a 0-ast, ha vegig szeretned jatszani az osszes szintet!\n");
            printf("        VIGYAZAT!!  Ha elakadsz egy szintnel, elorol kezded\n");
            printf("    Nyomd meg az 1-est, ha csak az elso szintet szeretned vegigjatszani\n");
            printf("    Nyomd meg az 2-est, ha csak a masodik szintet szeretned vegigvinni\n");
            printf("    Nyomd meg az 3-est, ha csak a harmadik szintet szeretned vegigjatszani\n");


            scanf("%d", &p);
            system("cls");
            int n;
            switch(p){

            case 0:
                n=0;

                while(n < 3){ /// Addig ismetli, amig a felhasznalo nem vegzi el mind a 3 palyat vegig

                    Rajzol(E1,&b);
                    E1 = Beolvas(E1,"be.txt");
                    if(b == 0){}
                    else{
                        n++;
                        printf("\n  Kovetkezik a masodik szint!!\n  Nyomj egy 'Enter'-t!\n");
                        if(_getch())
                            system("cls");
                        Rajzol(E2,&b);
                        E2 = Beolvas(E2,"be2.txt");
                        if(b == 1){
                            n++;
                            printf("\n\n  Kovetkezik a harmadik szint!!\n   Nyomj egy 'Enter'-t!\n");
                            if(_getch())
                                system("cls");
                            Rajzol(E3, &b);
                            E3 = Beolvas(E3,"be3.txt");

                            if(b == 1){
                                n++;
                                printf("\n      Megcsinaltad! Gratulalok!!\n    ENTER a tovabblepeshez    !!!");
                                if(_getch()){
                                    system("cls");
                                    break;
                                }
                            }
                        }
                    }
                    printf("\n  Felbe akarod hagyni?\n  Nyomj egy 'Esc' gombot!\n   Maskulonben 'Enter' -t!\n\n");
                    if(_getch() == 27)
                        break;
                    else
                        system("cls");

                }
                break;
            case 1:
                Rajzol(E1,&b);
                E1 = Beolvas(E1,"be3.txt");
                break;

            case 2:
                Rajzol(E2,&b);
                E2 = Beolvas(E2,"be3.txt");
                break;

            case 3:
                Rajzol(E3,&b);
                E3 = Beolvas(E3,"be3.txt");
                break;


            }

            printf("\n\n    Ha meguntad a jatekot, nyomj egy 'Esc' gombot!\n    Maskulonben 'Entert'!\n");
            k = _getch();
        }
    }
    else{   ///Itt kezdodik a nehezebb fokozat, ami lenyegeben a programsorozat ugyan az, egy fuggveny valtoztatasaval
        while(k != 27){
            printf("Opciok:\n   Nyomd meg a 0-ast, ha vegig szeretned jatszani az osszes szintet!\n");
            printf("    VIGYAZAT!!  Ha elakadsz egy szintnel, elorol kezded\n");
            printf("    Nyomd meg az 1-est, ha csak az elso szintet szeretned vegigjatszani\n");
            printf("    Nyomd meg az 2-est, ha csak a masodik szintet szeretned vegigvinni\n");
            printf("    Nyomd meg az 3-est, ha csak a harmadik szintet szeretned vegigjatszani\n");


            scanf("%d", &p);
            system("cls");
            int n;
            switch(p){

            case 0:
                n=0;
                while(n < 3){

                    n = 0;
                    RajzolNehez(E1,&b);
                    E1 = Beolvas(E1,"be.txt");
                    if(b == 0){}
                    else{
                        n++;
                        printf("\n  Kovetkezik a masodik szint!!\n  Nyomj egy 'Enter'-t!\n");
                        if(_getch())
                            system("cls");

                        RajzolNehez(E2,&b);
                        E2 = Beolvas(E2,"be2.txt");
                        if(b == 1){
                            n++;
                            printf("\n  Kovetkezik a harmadik szint!!\n     Nyomj egy 'Enter'-t!\n");
                            if(_getch())
                                system("cls");
                            RajzolNehez(E3, &b);
                            E3 = Beolvas(E3,"be3.txt");
                            if(b == 1){
                                n++;
                                printf("    Megcsinaltad! Gratulalok!!\n\n    ENTER a tovabblepeshez !!!");
                                if(_getch()){
                                    system("cls");
                                    break;
                                }
                            }
                        }
                    }
                printf("\n  Felbe akarod hagyni?\n  Nyomj egy 'Esc' gombot!\n   Maskulonben 'Enter' -t!");
                if(_getch() == 27) break;
                }


                break;
            case 1:

                RajzolNehez(E1,&b);
                E1 = Beolvas(E1,"be.txt");
                break;

            case 2:

                RajzolNehez(E2,&b);
                E2 = Beolvas(E2,"be.txt");
                break;
            case 3:

                RajzolNehez(E3,&b);
                E3 = Beolvas(E3,"be.txt");
                break;


            }

            printf("\n\n    Ha meguntad a jatekot, nyomj egy 'Esc' gombot!\n    Maskulonben 'Entert'!\n");
            k = _getch();
        }
    }




    return 0;
}

///header.h

#ifndef EGERSAJT_H_INCLUDED
#define EGERSAJT_H_INCLUDED

#include <stdio.h>

typedef struct egersajt{

    int n, m, lepesek,sajtok;
    int Ex, Ey;
    int *Sx, *Sy;
    int** a;

}egersajt;

egersajt* Create();
egersajt* Beolvas(egersajt*,char*);
void Rajzol(egersajt*, int *);
void RajzolNehez(egersajt*, int *);


#endif // EGERSAJT_H_INCLUDED



///source.c


#include "egersajt.h"

egersajt* Create(){

    egersajt* tmp = (egersajt*)calloc(1,sizeof(egersajt));
    return tmp;

}

egersajt* Beolvas(egersajt* ES , char* be){


    FILE* fin = fopen(be , "rt" );
    if(!fin)
        printf("Hiba a beolvasasnal");
///

    fscanf(fin ,"%d %d %d %d" , &ES->n , &ES->m , &ES->lepesek, &ES->sajtok);
    //printf("%d %d",ES->n , ES->m );
    ES->a = (int**)calloc(ES->n,sizeof(int*));
    ES->Sx = (int*)calloc(ES->sajtok,sizeof(int));
    ES->Sy = (int*)calloc(ES->sajtok,sizeof(int));

    for (int i=0 ; i<ES->n ; ++i)
        ES->a[i] = (int*) calloc (ES->m , sizeof(int));

    for(int i=0 ; i<ES->n ; ++i){
        for(int j=0 ; j<ES->m ; ++j)
            fscanf(fin , "%d" , &ES->a[i][j]);
    }
///

    fscanf(fin , "%d %d" , &ES->Ex, &ES->Ey);

    for(int i = 0 ; i < ES->sajtok ; i++)
        fscanf(fin , "%d %d" , &ES->Sx[i], &ES->Sy[i]);

    fclose(fin);
    return ES;
}


void RajzolNehez(egersajt* es, int* d){
    char h, b = '-';
    int tmpEx = es->Ex, tmpEy = es->Ey, bol;
    int tmp = es->lepesek;
    for(int i=es->Ex-5 ; i<=es->Ex+5 ; i++){
        for(int j=es->Ey-5 ; j<=es->Ey+5 ; j++){
            if(i < es->n && j < es->m && i >= 0 && j >= 0){
               if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                    printf("E ");
                    continue;
                    }
///
               for(int k=0 ; k < es->sajtok ; k++){
               if((es->Sx[k]-1) == i && (es->Sy[k]-1) == j){
                    printf("S ");
                    bol=1;
               }
               }
               if(bol){
                    bol=0;
                    continue;
               }
               if(es->a[i][j] == 1){
                    //printf("%d  " , es->a[i][j]);

                    if(i == 0 || i == es->n-1) printf("--");
                    else{
                        if(j == 0 || j == es->m-1) printf("| ");
                        else printf("+ ");
                    }

                    }
                if(es->a[i][j] != 1 && es->a[i][j] != 'S'){printf("  ");}

        }
        }
        printf("\n");

    }

    printf("\n\n     Lepesek szama:%d" , --tmp);

    int sum=0;
    int *tmpSx = es->Sx, *tmpSy = es->Sy;

    for(int k=0 ; ; k++){
        for(int l=0 ; l<es->sajtok ; l++)
            if(es->Ex == tmpSx[l] && es->Ey == tmpSy[l]){
                sum++;  ///printf("\nAz eger jol lakott!"); *d = 1; return;}
                tmpSx[l] = -1; tmpSy[l] = -1;
                ///es->a[tmpSx[l]][tmpSy[l]] = "  ";
            }
    if(sum == es->sajtok){
        printf("\nAz eger jol lakott!");
        *d = 1;
        return;
    }

        h = getch();
        system("cls");
        switch(h){
        case 'w' : es->Ex-- ; break;
        case 's' : es->Ex++ ; break;
        case 'a' : es->Ey-- ; break;
        case 'd' : es->Ey++ ; break;
        }
    if(es->a[es->Ex-1][es->Ey-1]!=1){
     for(int i=es->Ex-5 ; i<=es->Ex+5 ; i++){
        for(int j=es->Ey-5 ; j<=es->Ey+5 ; j++){
            if(i < es->n && j < es->m && i >= 0 && j >= 0){
               if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                    printf("E ");
                    continue;
                    }
               for(int k=0 ; k < es->sajtok ; k++){
               if((tmpSx[k]-1) == i && (tmpSy[k]-1) == j){
                printf("S ");
                    bol=1;
               }
               }
               if(bol){
                bol=0;
                continue;
               }
               if(es->a[i][j] == 1){
                    //printf("%d  " , es->a[i][j]);

                    if(i == 0 || i == es->n-1) printf("--");
                    else{
                        if(j == 0 || j == es->m-1) printf("| ");
                        else printf("+ ");
                    }

                    }
                if(es->a[i][j] != 1 && es->a[i][j] != 'S'){printf("  ");}

        }
           }
           printf("\n");
        }
        printf("\n\n     Lepesek szama:%d" , --tmp);

        //es->lepesek--;
        if(tmp == 0 && sum!=es->sajtok){     ///! (es->Ex == es->Sx && es->Ey == es->Sy)){

            printf("\nLejart a lepesek szama!");
            *d = 0;
            return;
        }

      }
      else{
        switch(h){
            case 'w' : es->Ex++ ; break;
            case 's' : es->Ex-- ; break;
            case 'a' : es->Ey++ ; break;
            case 'd' : es->Ey-- ; break;
      }
      for(int i=es->Ex-5 ; i<=es->Ex+5 ; i++){
        for(int j=es->Ey-5 ; j<=es->Ey+5 ; j++){
            if(i < es->n && j < es->m && i >= 0 && j >= 0){
               if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                    printf("E ");
                    continue;
                    }
               for(int k=0 ; k < es->sajtok ; k++){
               if((tmpSx[k]-1) == i && (tmpSy[k]-1) == j){
                printf("S ");
                    bol=1;
               }
               }
               if(bol){
                bol=0;
                continue;
               }
               if(es->a[i][j] == 1){
                    //printf("%d  " , es->a[i][j]);

                    if(i == 0 || i == es->n-1) printf("--");
                    else{
                        if(j == 0 || j == es->m-1) printf("| ");
                        else printf("+ ");
                    }

                    }
                if(es->a[i][j] != 1 && es->a[i][j] != 'S'){printf("  ");}

        }
           }
        printf("\n");
    }
    printf("\n\n     Lepesek szama:%d" , tmp);
    }
    }
system("cls");
es->Ex = tmpEx;
es->Ey = tmpEy;
es->Sx = tmpSx;
es->Sy = tmpSy;
}


void Rajzol(egersajt* es, int* d){
    char h, b = '-';
    int tmpEx = es->Ex, tmpEy = es->Ey,bol;
    int tmp = es->lepesek;
    for(int i=0 ; i<=es->n-1 ; i++){
        for(int j=0 ; j<=es->m-1 ; j++){
           if(i < es->n && j < es->m && i >= 0 && j >= 0){
               if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                    printf("E ");
                    continue;
                    }
///
               for(int k=0 ; k < es->sajtok ; k++){
               if((es->Sx[k]-1) == i && (es->Sy[k]-1) == j){
                    printf("S ");
                    bol=1;
               }
               }
               if(bol){
                    bol=0;
                    continue;
               }
               if(es->a[i][j] == 1){
                    //printf("%d  " , es->a[i][j]);

                    if(i == 0 || i == es->n-1) printf("--");
                    else{
                        if(j == 0 || j == es->m-1) printf("| ");
                        else printf("+ ");
                    }

                    }
                if(es->a[i][j] != 1 && es->a[i][j] != 'S'){printf("  ");}

            }
        }
        printf("\n");

    }

    printf("\n\n     Lepesek szama:%d" , --tmp);

    int *tmpSx = es->Sx, *tmpSy = es->Sy, sum = 0;

    for(int k=0 ; ; k++){

        for(int l=0 ; l<es->sajtok ; l++)
            if(es->Ex == tmpSx[l] && es->Ey == tmpSy[l]){
                sum++;  ///printf("\nAz eger jol lakott!"); *d = 1; return;}
                tmpSx[l] = -1; tmpSy[l] = -1;
                ///es->a[tmpSx[l]][tmpSy[l]] = "  ";
            }

        if(sum == es->sajtok){
            printf("\nAz eger jol lakott!");
            *d = 1;
            return;
        }

        h = getch();
        system("cls");
        switch(h){
        case 'w' : es->Ex-- ; break;
        case 's' : es->Ex++ ; break;
        case 'a' : es->Ey-- ; break;
        case 'd' : es->Ey++ ; break;
        }
    if(es->a[es->Ex-1][es->Ey-1]!=1){
     for(int i=0 ; i<=es->n-1 ; i++){
        for(int j=0 ; j<=es->m-1 ; j++){
           if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                printf("E ");
                continue;
           }
           for(int k=0 ; k < es->sajtok ; k++){
               if((tmpSx[k]-1) == i && (tmpSy[k]-1) == j){
                printf("S ");
                    bol=1;
               }
               }

            if(bol){
                bol = 0;
                continue;
            }

           if(es->a[i][j] == 1){
                ///printf("%d  " , es->a[i][j]);

                if(i == 0 || i == es->n-1) printf("--");
                    else{
                        if(j == 0 || j == es->m-1) printf("| ");
                        else printf("+ ");
                    }

                }

            else {printf("  ");}
           }
           printf("\n");
        }
        printf("\n\n     Lepesek szama:%d" , --tmp);

        //es->lepesek--;
        if(tmp == 0 &! (es->Ex == es->Sx && es->Ey == es->Sy)){

            printf("\nLejart a lepesek szama!");
            *d = 0;
            return 0;
        }

      }
      else{
        switch(h){
            case 'w' : es->Ex++ ; break;
            case 's' : es->Ex-- ; break;
            case 'a' : es->Ey++ ; break;
            case 'd' : es->Ey-- ; break;
      }
      for(int i=0 ; i<=es->n-1 ; i++){
        for(int j=0 ; j<=es->m-1 ; j++){
           if(i < es->n && j < es->m && i >= 0 && j >= 0){
               if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                    printf("E ");
                    continue;
                    }
               for(int k=0 ; k < es->sajtok ; k++){
               if((tmpSx[k]-1) == i && (tmpSy[k]-1) == j){
                printf("S ");
                    bol=1;
               }
               }
               if(bol){
                bol=0;
                continue;
               }
               if(es->a[i][j] == 1){
                    //printf("%d  " , es->a[i][j]);

                    if(i == 0 || i == es->n-1) printf("--");
                    else{
                        if(j == 0 || j == es->m-1) printf("| ");
                        else printf("+ ");
                    }

                    }
                if(es->a[i][j] != 1 && es->a[i][j] != 'S'){printf("  ");}

        }
           }
        printf("\n");
    }
    printf("\n\n     Lepesek szama:%d" , tmp);
    }
    }
system("cls");
es->Ex = tmpEx;
es->Ey = tmpEy;
es->Sx = tmpSx;
es->Sy = tmpSy;
}

/*void Rajzol(egersajt* es){
    char h, b = '-';
    for(int i=1 ; i<es->n-1 ; i++){
        for(int j=1 ; j<es->m-1 ; j++){
           if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                printf("E  ");
                continue;
                }
           if((es->Sx-1) == i && (es->Sy-1) == j){
            printf("S  ");
                continue;
           }
           if(es->a[i][j] == 1){printf("%d  " , es->a[i][j]);}
            else {printf("   ");}
           }printf("\n");
    }

    for(int k=0 ; ; k++){

            if(es->Ex == es->Sx && es->Ey == es->Sy){printf("Az eger jol lakott!"); break;}

        h = getch();
        system("cls");
        switch(h){
        case 'w' : es->Ex-- ; break;
        case 's' : es->Ex++ ; break;
        case 'a' : es->Ey-- ; break;
        case 'd' : es->Ey++ ; break;
        }
    if(es->a[es->Ex-1][es->Ey-1]!=1){
     for(int i=1 ; i<es->n-1 ; i++){
        for(int j=1 ; j<es->m-1 ; j++){
           if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                printf("E  ");
                continue;
           }
           if((es->Sx-1) == i && (es->Sy-1) == j){
            printf("S  ");
                continue;
           }
           if(es->a[i][j] == 1){printf("%d  " , es->a[i][j]);}
            else {printf("   ");}
           }printf("\n");
        }
        for(int v=0 ; v < 120 ; v++){printf("%c" , b);}
        printf("\n\n");
      }
      else{switch(h){
        case 'w' : es->Ex++ ; break;
        case 's' : es->Ex-- ; break;
        case 'a' : es->Ey++ ; break;
        case 'd' : es->Ey-- ; break;
      }
      for(int i=1 ; i<es->n-1 ; i++){
        for(int j=1 ; j<es->m-1 ; j++){
           if((es->Ex-1) == i && (es->Ey-1) == j && es->a[es->Ex-1][es->Ey-1]!=1){
                printf("E  ");
                continue;
                }
           if((es->Sx-1) == i && (es->Sy-1) == j){
            printf("S  ");
                continue;
           }
           if(es->a[i][j] == 1){printf("%d  " , es->a[i][j]);}
            else {printf("   ");}
           }printf("\n");
    }
    }
    }

}*/
