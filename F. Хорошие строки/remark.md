Примечательно, что решение этой задачи практически аналогично решению задачи о ПСП: https://www.geeksforgeeks.org/check-for-balanced-parentheses-in-an-expression/ 
\
Задача. Дана последовательность из трёх видов пар скобок: ( и ), [ и ], { и }. 
Правильная скобочная последовательность (ПСП) определяется так:  
•	Пустая строка является правильной скобочной последовательностью  
•	Если s — ПСП, то (s), [s] и {s} — тоже ПСП  
•	Если s и t — ПСП, то их конкатенация — тоже ПСП  
Определить, является ли заданная строка ПСП.
\
\
Решение:
```objectivec
#include<iostream>
#include<stack>

using namespace std;

bool areBracketsBalanced(const string& expr) {
    stack<char> temp;

    for (int i = 0; i < expr.length(); i++) { // for(const char c : expr) {
    
        if (!temp.empty() && (
            (temp.top() == '(' && expr[i] == ')') || 
            (temp.top() == '{' && expr[i] == '}') || 
            (temp.top() == '[' && expr[i] == ']')
                            )
            ) {
            temp.pop();
        }
        else {
            temp.push(expr[i]);
        }
    }

    return ((temp.empty()) ? true: false);
}

int main() {
    string expr = "[[(])";

    if (areBracketsBalanced(expr)){
        cout << "Balanced";
    } 
    else {
        cout << "Not Balanced";
    }

    return 0;
}
```
\
Также на основе решения "Хорошие строки" можно легко решить такую задачу: Удалить соседение символы из строки, которые в ascii отстают меньше, чем на x
