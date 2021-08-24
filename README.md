# Numbers-to-Words
#include <iostream>
#include <string>
using namespace std;

//delcare the class
class Numbers {
    
    // the variables of the class
private:
    int number;
    static string lessThan20[20];
    static string hundred;
    static string thousand;
    static string tens[8];

public:
    //the declaration of the constuctor
    Numbers(int num) {
        //make sure the value is in range
        if (num < 0 && num>9999) {
            cout << "ERROR! Number not in range. Please try again.\n";
            exit(0);
        }
        else
            number = num;
    }

    // this will print the numbers into words

    void print() {
        //if the number is greater than zero
        while (number > 0) {
            // print the thousands first and then remove it
            if (number / 1000 > 0) {
                cout << lessThan20[number / 1000] << " " << thousand << " ";
                number = number % 1000;
            }
            // next print the hundreds and then remove it
            else if (number / 100 > 0) {
                cout << " " << lessThan20[number / 100] << " " << hundred << " ";
                number = number % 100;
            }
            // next print the numbers if they are greater than equal to 20 or less than 100 then remove it
            else if (number >= 20) {
                cout << tens[(number / 10) - 2] << " ";
                number = number % 10;
            }
            // next print the numbers less than 20 and greater than or equal to 0
            else {
                cout << lessThan20[number];
                // the break will end the loop
                break;
            }
        }
    }
};

    //define the static variables
string Numbers::lessThan20[20] = { "zero", "one", "two", "three", "four",
                            "five", "six", "seven", "eight", "nine",
                            "ten", "eleven", "twelve", "thirteen", "fourteen",
                            "fifteen", "sixteen", "seventeen", "eighteen", "nineteen" };
string Numbers::hundred = "hundred";
string Numbers::thousand = "thousand";
string Numbers::tens[8] = { "twenty", "thirty", "forty", "fifty", "sixty",
                        "seventy", "eighty", "ninety" };

int main()
{
    // talk to the user
    int inputNumber;
    cout << "Enter a number between 0-9999: ";
    cin >> inputNumber;
    // this will initialize the number by using the constructor
    Numbers num(inputNumber);
    // this will use the object of numbers class using print() method
    num.print();

    return 0;
}
