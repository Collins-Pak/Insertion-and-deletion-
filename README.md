# Insertion-and-deletion-
This is a program written in c ,, showing insertion and deletion elements 

#include <stdio.h>

#define MAX 100

void insert(int arr[], int *size, int elem, int pos) {
    if (*size >= MAX || pos > *size || pos < 0) return;
    for (int i = (*size)++; i > pos; i--) arr[i] = arr[i - 1];
    arr[pos] = elem;
}

void delete(int arr[], int *size, int pos) {
    if (*size == 0 || pos >= *size || pos < 0) return;
    for (int i = pos; i < (*size) - 1; i++) arr[i] = arr[i + 1];
    (*size)--;
}

void display(int arr[], int size) {
    for (int i = 0; i < size; i++) printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int arr[MAX], size = 0, choice, elem, pos;
    
    while (1) {
        printf("1. Insert  2. Delete  3. Display  4. Exit\nChoose: ");
        scanf("%d", &choice);

        if (choice == 1) {
            printf("Element & Position: ");
            scanf("%d %d", &elem, &pos);
            insert(arr, &size, elem, pos);
        } 
        else if (choice == 2) {
            printf("Position to delete: ");
            scanf("%d", &pos);
            delete(arr, &size, pos);
        } 
        else if (choice == 3) display(arr, size);
        else break;
    }
    return 0;
}