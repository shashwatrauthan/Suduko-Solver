#include <stdio.h>
#include <stdlib.h>

// N is the size of the 2D matrix N*N
#define N 9

// function to print
void print(int arr[N][N])
{
	printf("\n RESULT:\n");
	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < N; j++)
		{
			printf("%d ",arr[i][j]);
		}
		printf("\n");
	}
}

// Checks whether it will be possible
int isSafe(int grid[N][N], int row, int col, int num)
{
	
	// Check if we find the same num in the similar row, we will return 0
	for (int x = 0; x <= 8; x++)
		if (grid[row][x] == num)
			return 0;

	// Check if we find the same num in the similar column, we will return 0
	for (int x = 0; x <= 8; x++)
		if (grid[x][col] == num)
			return 0;
	// Check if we find the same num in the particular 3*3 matrix, we will return 0
	int startRow = row - row % 3, 
				startCol = col - col % 3;

	for (int i = 0; i < 3; i++)
		for (int j = 0; j < 3; j++)
			if (grid[i + startRow][j + 
						startCol] == num)
				return 0;
	return 1;
}


int solveSuduko(int grid[N][N], int row, int col)
{
	
	if (row == N - 1 && col == N)
		return 1;

	if (col == N) 
	{
		row++;
		col = 0;
	}

	if (grid[row][col] > 0)
		return solveSuduko(grid, row, col + 1);

	for (int num = 1; num <= N; num++) 
	{
		
		if (isSafe(grid, row, col, num)==1) 
		{
			grid[row][col] = num;
			if (solveSuduko(grid, row, col + 1)==1)
				return 1;
		}
		grid[row][col] = 0;
	}
	return 0;
}

int main()
{
	// 0 means unassigned cells
	printf("Enter Suduko Elements, for unassigned cells enter 0:\n");
	int grid[N][N];
	for(int i=0;i<N;i++)
	{
		for(int j=0;j<N;j++)
		{
			scanf("%d",&grid[i][j]);
		}
	}

	if (solveSuduko(grid, 0, 0)==1)
		print(grid);
	else
		printf("No Solution Exists");

	return 0;
}
