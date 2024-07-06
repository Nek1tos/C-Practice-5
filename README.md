# C-Practice-5

#include <stdio.h>

int count_sequences(int n) {
    int dp[3][n + 1];
    int i, j; 
    for (i = 0; i <= 2; i++) {
        dp[i][0] = 1;
        dp[i][1] = 1;
    }
    dp[0][2] = 2;
    dp[1][2] = 1;
    dp[2][2] = 0;
    // обчислення
    for (j = 3; j <= n; j++) {
        dp[0][j] = (dp[0][j - 1] + dp[1][j - 1]) % 12345;
        dp[1][j] = (dp[0][j - 1] + dp[2][j - 1]) % 12345;
        dp[2][j] = dp[1][j - 1] % 12345;
    }
    return (dp[0][n] + dp[1][n]) % 12345;
}

int main() {
    int n;
    printf("Введіть довжину послідовності n: ");
    scanf("%d", &n);
    printf("Кількість шуканих послідованостей: %d\n", count_sequences(n));
    return 0;
}
