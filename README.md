#include <stdio.h>
#include <stdbool.h>


bool knows(int a, int b) {
    
    int knows_matrix[4][4] = {
        {0, 1, 1, 1},  
        {0, 0, 1, 1},  
        {0, 0, 0, 1},  
        {0, 0, 0, 0} 
    };
    
    return knows_matrix[a][b] == 1;
}

int findCelebrity(int n) {
    int candidate = 0;

    for (int i = 1; i < n; i++) {
        if (knows(candidate, i)) {
            
            candidate = i;  // Update candidate to i
        }
    }

    
    for (int i = 0; i < n; i++) {
        if (i != candidate) {
            if (knows(candidate, i) || !knows(i, candidate)) {
                
                return -1;
            }
        }
    }

    return candidate;
}

void displayResult(int celebrity) {
    if (celebrity != -1) {
        printf("The celebrity is person %d.\n", celebrity);
    } else {
        printf("There is no celebrity.\n");
    }
}

int main() {
    int n;

    
    printf("Enter the number of people in the party: ");
    scanf("%d", &n);

  
    int celebrity = findCelebrity(n);

    
    displayResult(celebrity);

    return 0;
}
