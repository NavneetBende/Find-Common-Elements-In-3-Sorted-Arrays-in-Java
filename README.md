Common elements In three sorted arrays in Java
Here, in this page we will discuss the program to find the common elements in three sorted arrays in Java programming language. We are given with three arrays sorted in non-decreasing order, and we need to print all common elements in these arrays.

Input:

ar1[] = {1, 5, 5}
ar2[] = {3, 4, 5, 5, 10}
ar3[] = {5, 5, 10, 20}
Output:

5  5
find common elements In 3 sorted arrays in java
Let’s discuss the Brute force approach to find the common elements in the given three arrays. So, to find them we iterate over one array and for every i-th element we, check whether that i-th element is present in another two arrays or not if it is present then we will print that element otherwise check for another element.

Algorithm :
Define two flag variables isPresentInB and isPresentInC.
If BinarySearch (B, A[i]) returns True then set isPresentInB to 1. Otherwise set isPresentInB to 0.
If BinarySearch (C, A[i]) returns True then set isPresentInC to 1. Otherwise set isPresentInC to 0.
If both the flag variables isPresentInB and isPresentInC are set to 1, then we will add A[i] to the output array provided it is already not present in it. To check whether an element is already present in the output array we just need to ensure that either the output array is empty or the last element of the output array is not equal to A[I].
Return the output array.
find common elements In 3 sorted arrays in java
Code to find Common elements In three sorted arrays in Java
Run
class Main {
	// This function prints common elements in ar1
	void findCommon(int ar1[], int ar2[], int ar3[])
	{
		// Initialize starting indexes for ar1[], ar2[] and
		// ar3[]
		int i = 0, j = 0, k = 0;

		// Iterate through three arrays while all arrays
		// have elements
		while (i < ar1.length && j < ar2.length
			&& k < ar3.length) {
			// If x = y and y = z, print any of them and
			// move ahead in all arrays
			if (ar1[i] == ar2[j] && ar2[j] == ar3[k]) {
				System.out.print(ar1[i] + " ");
				i++;
				j++;
				k++;
			}

			// x < y
			else if (ar1[i] < ar2[j])
				i++;

			// y < z
			else if (ar2[j] < ar3[k])
				j++;

			// We reach here when x > y and z < y, i.e., z
			// is smallest
			else
				k++;
		}
	}

	// Driver code to test above
	public static void main(String args[])
	{
		Main ob = new Main();

		int ar1[] = { 1, 5, 10, 20, 40, 80 };
		int ar2[] = { 6, 7, 20, 80, 100 };
		int ar3[] = { 3, 4, 15, 20, 30, 70, 80, 120 };

		System.out.print("Common elements are ");
		ob.findCommon(ar1, ar2, ar3);
	}
}
