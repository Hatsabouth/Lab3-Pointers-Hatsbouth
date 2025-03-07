# Lab3-Pointers-Hatsbouth

#ifndef LAB3_H // Include guard to prevent multiple inclusions
#define LAB3_H

#include <fstream>
#include <iostream>
#include <cstdlib>
#include <string>
#include <vector>

using namespace std;

vector <int> arr = {10,20,30,40,50};
vector <string> names = {"John", "David","Larry", "James"};


//Taking pointer arrays of names,size,and filename
void print(string* names, int size, string filename) {
    ofstream outFile(filename);
    if (!outFile.is_open()) {
        cout << "Can not open file " << filename << endl;
        return;
    }

    for (int i = 0; i < size; ++i) {
        outFile << names[i] << endl;
    }

    outFile.close();
    cout << "Data written to " << filename << endl;
}

//Taking pointer arrays of string, capacity, and filename
int load(string* names, int capacity, string filename) {
    ifstream inFile(filename);
    if (!inFile.is_open()) {
        cout << " Can not open file " << filename << endl;
        return 0;
    }

    int count = 0;
    string line;
    while (getline(inFile, line) && count < capacity) {
        names[count] = line;
        count++;
    }

    inFile.close();
    cout << "Loaded " << count << " names from " << filename << endl;
    return count;
}


//Taking Pointer of string names and size
//Implmenting a bubble sort 
//Using swap function to switch positions
void sort_ptr(string* names, int size) {
    for (int i = 0; i < size - 1; ++i) {
        for (int j = 0; j < size - i - 1; ++j) {
            if (names[j] > names[j + 1]) {
                swap(&names[j], &names[j + 1]);
            }
        }
    }
}

void swap(string* a, string* b){

    string temp = *a;
    *a = *b;
    *b = temp;
}

#endif

