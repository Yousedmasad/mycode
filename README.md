# mycode
#include <iostream>
#include <vector>
#include <list>
#include <string>
using namespace std;

struct Pair { 
    string key;
    int val;
};
int hashString(const string& s){
    return 0;
}

void insertIntoHashTable(vector<list<Pair>>& v, const string& key, int val) {
    
    int idx = hashString(key) % v.size();
    
    list<Pair>& l = v.at(idx);
    for(Pair& p : l) {
        if(p.key == key) {
            p.val = val;
            return;
        }
    }
    Pair newPair = {key, val};
    l.push_back(newPair);
}
int lookupInHashTable(vector<list<Pair>>& v, const string& key) {
int idx = hashString(key) % v.size();
    list<Pair>& l = v.at(idx);
    for(const Pair& p : l) {
        if(p.key == key) {
            return p.val;
        }
    }
    return -1;
}    


int main() {
   vector<list<Pair>> hashTable;
   hashTable.resize(5);
   
   insertIntoHashTable(hashTable, "Lawton", 8675309);
   insertIntoHashTable(hashTable, "Yousef", 8675310);
   insertIntoHashTable(hashTable, "mom", 8674309);

cout << lookupInHashTable(hashTable, "Lawton") << endl;
cout << lookupInHashTable(hashTable, "Yousef") << endl;
cout << lookupInHashTable(hashTable, "mom") << endl;
cout << lookupInHashTable(hashTable, "Peter") << endl;

    return 0;
}
