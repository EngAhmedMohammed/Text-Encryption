#include<iostream>
#include<math.h>
#include<string>
#include<cstring>

using namespace std;

string msg;
int d, l;
int ss = 0;
float** encrypt;
float** decrypt;
float** mes;
float a[3][3], b[3][3], c[3][3];
void encryption(); //encrypts the message
void decryption(); //decrypts the message
void getKeyMessage(); //gets key and message from user
void inverse(); //finds inverse of key matrix
float det(float m[3][3]);

int main()
{
    getKeyMessage();
    encrypt = new float* [3];
    decrypt = new float* [3];
    mes = new float* [3];
    for (int h = 0; h < 3; h++)
    {
        encrypt[h] = new float[d];
        decrypt[h] = new float[d];
        mes[h] = new float[d];
    }
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < d; j++)
        {
            encrypt[i][j] = 0;
            decrypt[i][j] = 0;
            mes[i][j] = msg[ss] - 96;
            if (mes[i][j] == -64)
            {
                mes[i][j] = 0;
            }
            ss++;
        }
    encryption();
    decryption();
}

void encryption()
{
    int i, j, k = 0;
    for (i = 0; i < 3; i++)
        for (j = 0; j < d; j++)
            for (k = 0; k < 3; k++)
                encrypt[i][j] += a[i][k] * mes[k][j];
    cout << "\nEncrypted message is: ";
    for (i = 0; i < 3; i++)
        for (j = 0; j < d; j++)
        {
            if (((char)round((fmod(encrypt[i][j], 27) + 96)) != '`'))
                cout << (char)round((fmod(encrypt[i][j], 27) + 96));
        }
}

void decryption()
{
    int i, j, k = 0;
    inverse();
    for (i = 0; i < 3; i++)
        for (j = 0; j < d; j++)
            for (k = 0; k < 3; k++)
                decrypt[i][j] += encrypt[k][j] * b[i][k];
    cout << "\n\nDecrypted message is: ";
    for (i = 0; i < 3; i++)
        for (j = 0; j < d; j++)
        {
            if ((char)(round(fmod(decrypt[i][j], 27) + 96) == '`'))
                cout << " ";
            else
                cout << (char)round((fmod(decrypt[i][j], 27) + 96));
        }
    cout << "\n";
}

void getKeyMessage()
{
    int i, j;
    cout << "Enter an invertible matrix with size 3x3:\n";
    for (i = 0; i < 3; i++)
    {
        for (j = 0; j < 3; j++)
        {
            cin >> a[i][j];
            c[i][j] = a[i][j];
        }
    }
    cout << "det = " << det(a) << endl;
    while (det(a) == 0)
    {
        cout << "\nEnter an invertible matrix\n";
        for (i = 0; i < 3; i++)
        {
            for (j = 0; j < 3; j++)
            {
                cin >> a[i][j];
                c[i][j] = a[i][j];
            }
        }
        cout << "det = " << det(a) << endl;
    }
    cout << "\nEnter your message: ";
    cin.ignore();
    getline(cin, msg);
    l = msg.length();
    if (l % 3 == 1)
    {
        msg += "``";
    }
    if (l % 3 == 2)
    {
        msg += "`";
    }
    if (l % 3 == 0)
        d = l / 3;
    else
        d = (l / 3) + 1;
}

void inverse()
{
    int i, j, k;
    float p, q;
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
        {
            if (i == j)
                b[i][j] = 1;
            else
                b[i][j] = 0;
        }
    for (k = 0; k < 3; k++)
    {
        for (i = 0; i < 3; i++)
        {
            p = c[i][k];
            q = c[k][k];
            for (j = 0; j < 3; j++)
            {
                if (i != k)
                {
                    c[i][j] = c[i][j] * q - p * c[k][j];
                    b[i][j] = b[i][j] * q - p * b[k][j];
                }
            }
        }
    }
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            b[i][j] = b[i][j] / c[i][i];
}

float det(float m[3][3])
{
    float d = (m[0][0] * (m[1][1] * m[2][2] - m[2][1] * m[1][2])
        - m[0][1] * (m[1][0] * m[2][2] - m[2][0] * m[1][2])
        + m[0][2] * (m[1][0] * m[2][1] - m[2][0] * m[1][1]));
    return d;
}
