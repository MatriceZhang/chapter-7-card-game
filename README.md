chapter-7-card-game
===================

//
//  main.cpp
//  chapter7
//
//  Created by zhangshiyu on 11/15/14.
//  Copyright (c) 2014 ZSY. All rights reserved.
//

#include <iostream>
#include <cstdlib>   //for srand(),rand()
#include <ctime>      //for time for srand()

using namespace std;

enum Suit{clubs,diamonds,hearts,spades};
//form 2 to 10 are integers withoutnames
const int jack=11;
const int queen=12;
const int king=13;
const int ace=14;

class card
{
private:
    int number;  //2 to 10 ,jack,queen,king,ace
    Suit suit;    //clubs...
public:
    card()        //constructor
    {}
    void set(int n,Suit s)  //set card
    {suit=s; number=n;}
    void display();    //display card
    
};


void card::display()
{
    if(number>=2&&number<=10)
        cout<<number;
    else
        switch (number) {
            case jack:
                cout<<"J";
                break;
            case queen:
                cout<<"Q";
                break;
            case king:
                cout<<"K";
                break;
            case ace:
                cout<<"A";
                break;
        
        }
    switch (suit) {
        case clubs:
            cout<<static_cast<char>(5);
            break;
        case diamonds:
            cout<<static_cast<char>(4);
            break;
            case hearts:
            cout<<static_cast<char>(3);
            break;
            case spades:
            cout<<static_cast<char>(6);
            break;
            
     
    }
}


int main()
{
    card deck[52];
    int j;
    
    
    cout<<endl;
    
    for(j=0;j<52;j++)
    {
        int num=(j%13)+2;  //cycles through 2 to 14,4 times
        Suit su=Suit(j/13);//cycle through 0 to3,13times
        deck[j].set(num, su);
    }
    
    cout<<"\nOrderd deck:\n";
    for(j=0;j<52;j++)
       {
        deck[j].display();
        cout<<"   ";
        if (!(j+1)%13) {
            cout<<endl;
        }
        
        srand(time(NULL));   //send random numbers with time
        for (j=0; j<52; j++) {
            int k=rand()%52;   //pick another card at random
            card temp=deck[j];
            deck[j]=deck[k];
            deck[k]=temp;
        }
        
        cout<<"\nShuffled deck:\n";
        for (j=0; j<52; j++) {
            deck[j].display();
            cout<<", ";
            if (!((j+1)%13))
                cout<<endl;
        }
           return 0;
       }
