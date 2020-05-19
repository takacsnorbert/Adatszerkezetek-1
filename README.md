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
