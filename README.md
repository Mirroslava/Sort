# Sort
Different types of sorting

#include <iostream>
#include <ctime>
using namespace std;
const int n = 10;
int arr[n];
int  number;
int por, perest;
void merge(int arr[] ,int l, int r);
void quickSort(int arr[], int l, int r);
int main() {
	//srand(time(NULL));
	cout << "Enter mas - " << endl;

	for (int i = 0; i < n; i++)
		cin >> arr[i];
	cout << "***MENU***" << endl;
	cout << "1. Sort zlytta" << endl;
	cout << "2. QuickSort " << endl;
	cout << "3. Exit" << endl;
	cout << "Enter numser" << endl;
	cin >> number;

	
	while (number != 3) {
		if (number >= 1 && number <= 3) {}
		else { cout << "Number must be from 1 to 2" << endl; }
		switch (number) {
		case 1:
			//int a = clock();
			cout << "Sorted mas " << endl;
			merge(arr,0, n - 1);

			for (int i = 0; i < n; i++)
				cout << arr[i] << " ";
			cout << endl;
			/*int b = clock();
			double t1 = ((double)b / CLOCKS_PER_SEC),
				t2 = ((double)a / CLOCKS_PER_SEC);
			cout << "Time -  " << t1 - t2 << endl;*/
			cout << "Porivnyana -  " << por << endl;
			cout << "Perestanovky -  " << perest << endl;
			break;
		case 2:
			cout << "Sorted mas " << endl;
			quickSort(arr, 0, n - 1);

			for (int i = 0; i < n; i++)
			{
				cout << arr[i] << " ";
			}

			cout << endl;
			cout << "Porivnyana -  " << por<< endl;
			cout << "Perestanovky -  " << perest << endl;
			break;
		}
				cout << "Enter number" << endl;
				cin >> number;
				
		
	}
	system("pause");
	return 0;
}
void merge(int arr[], int l, int r) {
	if (r == l)
		por++;
		return;
	if (r - l == 1) {
		por++;
		if (arr[r] < arr[l])
			por++;
			swap(arr[r], arr[l]);
			perest++;
		return;
	}
	int m = (r + l) / 2;
	merge(arr,l, m);
	merge(arr,m + 1, r);
	int buf[n];
	int xl = l;
	int xr = m + 1;
	int c = 0;
	while (r - l + 1 != c) {
		por++;
		if (xl > m) {
			por++;
			buf[c++] = arr[xr++];
		}
		else if (xr > r)
		{
			por++;
			buf[c++] = arr[xl++];
		}
		else if (arr[xl] > arr[xr]) {
			por++;
			buf[c++] = arr[xr++];
		}
		else { 
			por++;
			buf[c++] = arr[xl++]; 
		}

	}
	for (int i = 0; i < c; i++)
		arr[i + l] = buf[i];
}
void quickSort(int mas[], int s, int n)
{
	por = 0;
	perest = 0;
	int l = s;
	int r = n;

	int middle = mas[(l + r) / 2];

	while (l<r)
	{
		por++;
		while (mas[l] < middle)
		{
			l++;
			por++;
		}
		while (middle < mas[r])
		{
			r--;
			por++;
		}
		if (l <= r)
		{
			por++;
			swap(mas[l], mas[r]);
			perest++;
			l++;
			r--;
		}
	}

	if (s < r)
	{

		quickSort(mas, s, r);
		por++;
	}
	if (l < n)
	{

		quickSort(mas, l, n);
		por++;
	}
