#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>

#define MAX_EXPR_LENGTH 100
#define MAX_SIZE 50

typedef struct {
    char op;
    double value;
    bool isValue;
} Token;
int precedence(char op) {
    if (op == '+' || op == '-')
        return 1;
    if (op == '*' || op == '/')
        return 2;
    return 0;
}

typedef struct {
    char expression[MAX_EXPR_LENGTH];
    Token tokens[MAX_EXPR_LENGTH];
    int tokenCount;
} Expression;

void tokenize(Expression *exp) {
    char *token = strtok(exp->expression, " ");
    while (token != NULL) {
        if (token[0] == '+' || token[0] == '-' || token[0] == '*' || token[0] == '/') {
            exp->tokens[exp->tokenCount].op = token[0];
            exp->tokens[exp->tokenCount].isValue = false;
        } else {
            exp->tokens[exp->tokenCount].value = atof(token);
            exp->tokens[exp->tokenCount].isValue = true;
        }
        exp->tokenCount++;
        token = strtok(NULL, " ");
    }
    char stack[MAX_SIZE];
    int top;
} Stack;

void initialize(Stack *s) 
{
    s->top = -1;
}

void eliminateCommonSubexpressions(Expression *exp) {
    for (int i = 0; i < exp->tokenCount; i++) {
        if (exp->tokens[i].isValue) {
            for (int j = i + 2; j < exp->tokenCount; j += 2) {
                if (exp->tokens[j].isValue && exp->tokens[j - 2].isValue) {
                    double result = 0.0;
                    switch (exp->tokens[j - 1].op) {
                        case '+':
                            result = exp->tokens[j - 2].value + exp->tokens[j].value;
                            break;
                        case '-':
                            result = exp->tokens[j - 2].value - exp->tokens[j].value;
                            break;
                        case '*':
                            result = exp->tokens[j - 2].value * exp->tokens[j].value;
                            break;
                        case '/':
                            result = exp->tokens[j - 2].value / exp->tokens[j].value;
                            break;
                    }
                    exp->tokens[j].isValue = true;
                    exp->tokens[j].value = result;
                    memmove(&exp->tokens[j - 2], &exp->tokens[j + 1], (exp->tokenCount - j - 1) * sizeof(Token));
                    exp->tokenCount -= 2;
                    j -= 2;
                }
            }
        }
    }
void push(Stack *s, char c) {
    s->stack[++s->top] = c;
}

char pop(Stack *s) {
    return s->stack[s->top--];
}

int isOperator(char c) {
    return (c == '+' || c == '-' || c == '*' || c == '/');
}

void printExpression(Expression *exp) {
    for (int i = 0; i < exp->tokenCount; i++) {
        if (exp->tokens[i].isValue) {
            printf("%lf", exp->tokens[i].value);
void printParsingTable() {
    printf("Operator Precedence Parsing Table:\n");
    printf("|   | + | - | * | / | ( | ) | $\n");
    printf("|---|---|---|---|---|---|---|---|\n");
    printf("| + | > | > | < | < | < | > | > |\n");
    printf("| - | > | > | < | < | < | > | > |\n");
    printf("| * | > | > | > | > | < | > | > |\n");
    printf("| / | > | > | > | > | < | > | > |\n");
    printf("| ( | < | < | < | < | < | = |   |\n");
    printf("| ) | > | > | > | > |   | > | > |\n");
    printf("| $ | < | < | < | < | < |   | = |\n");
    printf("|---|---|---|---|---|---|---|---|\n");
}

void operatorPrecedenceParser(char *expression) {
    Stack operatorStack;
    initialize(&operatorStack);

    printf("Parsing Steps:\n");
    printf("|   Stack   |   Input   |  Action  |\n");
    printf("|-----------|-----------|----------|\n");

    int i = 0;
    while (expression[i] != '\0') {
        // Print current state of stack and input
        printf("| %-9s | %-9s |", operatorStack.stack, expression + i);

        if (expression[i] == '(') {
            push(&operatorStack, expression[i]);
            printf(" Shift    |\n");
        } else if (expression[i] == ')') {
            while (operatorStack.stack[operatorStack.top] != '(') {
                printf(" Reduce   |\n");
                pop(&operatorStack);
            }
            pop(&operatorStack); // Pop '(' from stack
            printf(" Reduce   |\n");
        } else if (isOperator(expression[i])) {
            while (operatorStack.top >= 0 && precedence(expression[i]) <= precedence(operatorStack.stack[operatorStack.top])) {
                printf(" Reduce   |\n");
                pop(&operatorStack);
            }
            push(&operatorStack, expression[i]);
            printf(" Shift    |\n");
        } else {
            printf(" %c ", exp->tokens[i].op);
            printf("          |\n");
        }
        i++;
    }
    printf("\n");

    while (operatorStack.top >= 0) {
        printf("| %-9s | %-9s | Reduce   |\n", operatorStack.stack, "");
        pop(&operatorStack);
    }
    printf("|-----------|-----------|----------|\n");
}

int main() {
    Expression exp;
    printf("Enter an arithmetic expression with spaces between each token: ");
    fgets(exp.expression, MAX_EXPR_LENGTH, stdin);
    exp.tokenCount = 0;
    char expression[MAX_SIZE];
    printf("Enter an infix expression: ");
    scanf("%s", expression);

    tokenize(&exp);
    printf("Original expression: ");
    printExpression(&exp);

    eliminateCommonSubexpressions(&exp);
    printf("Expression after eliminating common subexpressions: ");
    printExpression(&exp);
    printf("\n");
    printParsingTable();
    printf("\n");
    operatorPrecedenceParser(expression);

    return 0;
}
