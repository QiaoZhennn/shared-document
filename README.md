# shared-document
#include <iostream>
#include <ctime>
#include <vector>
#include <string>
#include <unordered_set>
#include <set>
using namespace std;

int valid(const vector<string> &A) {
    for (int i = 0; i < 9; ++i) {
        unordered_set<char> row;
        unordered_set<char> col;
        unordered_set<char> cube;
        int cube_row_idx = i / 3 * 3;
        int cube_col_idx = i % 3 * 3;
        for (int j = 0; j < 9; ++j) {
            if (A[i][j] == '.')
                continue;
            if (row.find(A[i][j]) == row.end()) {
                char c = A[i][j];
                row.insert(c);
            } else
                return 0;
            if (col.find(A[j][i]) == col.end()) {
                col.insert(A[j][i]);
            } else
                return 0;
            if (cube.find(A[cube_row_idx + j/3][cube_col_idx + j%3]) == cube.end()) {
                cube.insert(A[cube_row_idx + j/3][cube_col_idx + j%3]);
            } else
                return 0;
        }
    }
    return 1;
}

int main(int argc, char** argv) {
    vector<string> a{"..5.....6", "....14...", ".........", ".....92..", "5....2...", ".......3.", "...54....", "3.....42.", "...27.6.." };
    int res = valid(a);
    int c = 1;
    c = 2;
    c = 3;
    std::cout<<c<<std::endl;
    std::cout << res << std::endl;
    set<char> b;
    b.insert('2');
    if (b.size() == 0) {
        cout<<"Empty"<<endl;
    }
    if (b.size() != 0) {
        cout<<"Not Empty: "+to_string(b.size())<<endl;
    }
    return 0;
}
