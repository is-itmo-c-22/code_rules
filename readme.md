1) Не объявляйте переменные в одну строку, это выглядит некрасиво и ухудшает читаемость кода
Вот так делать плохо
```
int one = 1; int zero = 0;
```
Вот так делать очень плохо
```
int one = 1, zero = 2;
```
Надо вот так:
```
int one = 1;
int zero = 0;
```
2) Неправильное форматирование. Фигурные скобки
Открывающая фигурная скобка находится на той же строк
else на одной строке с закрывающей
Вот так правильно
```
if (true) {
    ...;
} else if (false) {
    ...;
} else {
    ...;
}

while (true) {
    ...;
}
```
3) Пробелы после `if`, `else`, `for`, `while` и перед `else`. Пробел перед `{` и после `}`
Вот так неправильно:
```
if(true){
    ...;
}else if(false){
    ...;
}
```
Вот так правильно:
```
if (true) {
    ...;
} else if (false) {
    ...;
}
```
4) Пробелы перед и после операторов
Всегда перед и после операторов ставится один пробел
Пример операторов - -=, +=, *=, |=, &=, ...(это не оператор), <, >=, ==, ..., <<, >>, &&, ||, ...
Вот так неправильно
```
for (size_t i=0; i<10; i++) {
    ...;
}
```
Вот так правильно
```
for (size_t i = 0; i < 10; i++) {
...;
}
```

После оператора `!` пробел не ставится
Вот так неправильно
```
if ( ! (10 > 20) ) {
    ...;
}
```
Вот так правильно
```
if (!(10 > 20)) {
...;
}
```
5) После ';', если это не конец строки, ставится пробел
Вот так неправильно
```
for (size_t i = 0;i < 10;i++) {
    ...;
}
```
Вот так правильно
```
for (size_t i = 0; i < 10; i++) {
...;
}
```
6) Если вы параметрисуете какой-то тип(Это когда вот так например std::vector<std::vector>, здесь параметризуем вектор интом), то перед `<` пробел не нужен
Перед и после параметра пробел не нужен
Неправильно
```
std::vector < std::string > vctr;
```
Правильно
```
std::vector<std::string> vctr;
```
7) Порядок инклудов
Инклуды (`#include ...`) должны быть отсортированы вот в таком порядке:
 * Сначала идет блок инклудов вашей программы
 * Затем идет блок инклудов библиотек не из стандартной библиотеки
 * Затем идет блок инклудов стандартной библиотека

В каждом блоке инклуды отсортированы в лексикографическом порядке (как в словаре)
Между блоками пустая строка
Инклуды файлов вашей программы долдны быть с двойными ковычками `#include "file.h"`
Инклуды из стандартной библиотеки должны быть с треугольными скобками `#include <iostream>`
После последнего блока инклудов пустая строка
Вот так неправильно:
```
#include <queue>
#include <bitset>
#include "number.h"

#include "a_file_in_my_project.h"
#include "b_common_lib_in_my_company.h"
#include "a_common_lib_in_my_company.h"
int main() {
    return 0;
}
```
Вот так правильно:
```
#include "a_file_in_my_project.h"
#include "number.h"

#include "a_common_lib_in_my_company.h"
#include "b_common_lib_in_my_company.h"

#include <queue>
#include <bitset>

int main() {
    return 0;
}
```
8) Перед return пустая строка, если до этого есть строка кода, которая находится на одном уровне(в примере станет понятно)
После return пустой строк нет
в `main` `return 0` можно опускать
Вот так неправильно
```
int main() {
   if (true) {

       return 0;
   }
   return 1;

}
```
Вот так правильно
```
int main() {
    if (true) {
        return 0;
    }

    return 1;
}
```
9) `using namespace`
Пока что вам так делать нельзя, если будет можно, то объявлю
Вот так неправильно
```
#include <string>

using namespace std;

int main() {
    string str = "HELLO";
}
```
Вот так правильно
```
#include <string>

int main() {
    std::string str = "HELLO";
}
```
10) Называйте переменные осмысленно. Названия переменных, функций, классов, структур должно отражать смысл этой переменно. Сокращения часто плохо
11) Не используйте библиотеки языка Си (они заканчиваются на .h). Используйте плюсовые аналоги, у них такой же название, только без `.h` в конце и с `c` в начале
Плохо
```
#include <math.h>
```
Хорошо
```
#include <cmath>
```
12) Между функциями делайте 1 пустую строку
13) В конце файла всегда должна быть ровно 1 пустая строка
14) Если вы передаете в функцию/метод объект(не примитив. Примитив - int, char, float, char* и тп) и в функции вы его не меняете, то передавайте его по константной ссылке
Можно почитать вот тут про const reference
https://stackoverflow.com/questions/2627166/what-is-the-difference-between-a-const-reference-and-normal-parameter
Плохо
```
void printString(std::string str) {
    std::cout << str << std::endl;
}
```
Хорошо
```
void printString(const std::string& str) {
    std::cout << str << std::endl;
}
```
15) & относится к типу, она должна быть справа от типа без пробела
Плохо
```
void printFunction(const std::string &str)
void printFunction(const std::string & str)
```
Хорошо
```
void printFunction(const std::string& str)
```
