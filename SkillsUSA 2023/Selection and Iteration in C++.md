#SkillsUSA  
#### Selection and iteration are two fundamental concepts in programming that are used extensively in C++.

---

>Selection allows a program to make decisions based on certain conditions. In C++, selection is primarily implemented using the if/else and switch statements. The if statement allows the program to execute a block of code if a certain condition is true, and to execute a different block of code if the condition is false. For example:
```
int x = 5;
if (x > 0) {
    std::cout << "x is positive" << std::endl;
} else {
    std::cout << "x is non-positive" << std::endl;
}
```
In this example, the program will print "x is positive" because the condition x > 0 is true.

---

>The switch statement is another form of selection that allows the program to choose between multiple options based on the value of a single variable. For example:
```
int day = 2;
switch (day) {
    case 1:
        std::cout << "Monday" << std::endl;
        break;
    case 2:
        std::cout << "Tuesday" << std::endl;
        break;
    case 3:
        std::cout << "Wednesday" << std::endl;
        break;
    default:
        std::cout << "Invalid day" << std::endl;
}
```
In this example, the program will print "Tuesday" because the value of the variable day is 2.

---

>Iteration allows a program to repeat a block of code multiple times. In C++, iteration is primarily implemented using the for, while, and do-while loops. The for loop is used when the number of iterations is known in advance. For example:
```
for (int i = 0; i < 5; i++) {
    std::cout << i << std::endl;
}
```
In this example, the program will print the numbers 0 through 4, because the loop will iterate 5 times.

---

>The while and do-while loops are used when the number of iterations is not known in advance, and depends on some condition. The while loop checks the condition at the beginning of each iteration, while the do-while loop checks the condition at the end of each iteration. For example:
```
int i = 0;
while (i < 5) {
    std::cout << i << std::endl;
    i++;
}

int j = 0;
do {
    std::cout << j << std::endl;
    j++;
} while (j < 5);
```

---

In both examples, the program will print the numbers 0 through 4, because the loop will iterate 5 times. However, the do-while loop guarantees that the loop will execute at least once, even if the condition is false at the beginning.