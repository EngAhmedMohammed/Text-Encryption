#include<iostream>
#include<math.h>
#include<string.h>
#include<stdlib.h>
#include<cstdlib>
#include <ctime>

using namespace std;

long int p, q, n, t, flag, e[100], d[100], temp[100], j, m[100], en[100], i;
char msg[100];
int prime(long int);
void ce();
long int cd(long int);
void encrypt(int);
void decrypt(int);
int de_rand(int x)
{
 srand((unsigned) time(NULL));
 int random = 1 + (rand() % j-1);
 return random;
}
int prime(long int pr)
{
    int i;
    j = sqrt(pr);
    for (i = 2; i <= j; i++)
    {
        if (pr % i == 0)
            return 0;
    }
    return 1;
}
int main()
{
    cout << "ENTER FIRST PRIME NUMBER\n";
    cin >> p;
    flag = prime(p);
    if (flag == 0)
    {
        cout << "\nWRONG INPUT\n";
        exit(1);
    }
    cout << "\nENTER ANOTHER PRIME NUMBER\n";
    cin >> q;
    flag = prime(q);
    if (flag == 0 || p == q)
    {
        cout << "\nWRONG INPUT\n";
        exit(1);
    }
    cout << "\nENTER MESSAGE\n";
    fflush(stdin);
    string st1;
     cin.ignore();
    getline(cin, st1);
    int lst1;
    lst1 = st1.length();
    for(int h=0;h<=lst1;h++)
    msg[h]=st1[h];
    for (i = 0; msg[i] != '\0'; i++)
        m[i] = msg[i];
    n = p * q;
    t = (p - 1) * (q - 1);
    ce();
    cout<<"number of POSSIBLE VALUES OF e AND d  "<<j-1<<endl;
    int de=de_rand(j);
    cout<<"the choosen number  "<<de+1<<endl;
   //     cout << "\nPOSSIBLE VALUES OF e AND d ARE\n";

  //  for (i = 0; i < j - 1; i++)
      //  cout <<i+1<<")  "<< e[i] << "\t" << d[i] << "\n";
      cout<<"e = "<<e[de]<<"  d = "<<d[de]<<endl;
    encrypt(de);
    decrypt(de);
    return 0;
}
void ce()
{
    int k;
    k = 0;
    for (i = 2; i < t; i++)
    {
        if (t % i == 0)
            continue;
        flag = prime(i);
        if (flag == 1 && i != p && i != q)
        {
            e[k] = i;
            flag = cd(e[k]);
            if (flag > 0)
            {
                d[k] = flag;
                k++;
            }
            if (k == 99)
                break;
        }
    }
}
long int cd(long int x)
{
    long int k = 1;
    while (1)
    {
        k = k + t;
        if (k % x == 0)
            return (k / x);
    }
}
void encrypt(int de)
{
    long int pt, ct, key = e[de], k, len;
    i = 0;
    len = strlen(msg);
    while (i != len)
    {
        pt = m[i];
        pt = pt - 96;
        k = 1;
        for (j = 0; j < key; j++)
        {
            k = k * pt;
            k = k % n;
        }

        temp[i] = k;
        ct = k%26 + 97;
        en[i] = ct;
        i++;
    }
    en[i] = -1;
    cout << "\nTHE ENCRYPTED MESSAGE IS\n";
    for (i = 0; en[i] != -1; i++)
       if(96<en[i]&&en[i]<123){ printf("%c", en[i]);}
}
void decrypt(int de)
{
    long int pt, ct, key = d[de], k;
    i = 0;
    while (en[i] != -1)
    {
        ct = temp[i];
        k = 1;
        for (j = 0; j < key; j++)
        {
            k = k * ct;
            k = k % n;
        }
        pt = k + 96;
        m[i] = pt;
        i++;
    }
    m[i] = -1;
    cout << "\nTHE DECRYPTED MESSAGE IS\n";
    for (i = 0; m[i] != -1; i++)
        printf("%c", m[i]);
}
