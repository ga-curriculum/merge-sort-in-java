<h1>
  <span class="headline">Merge Sort in Java</span>
  <span class="subhead">Merge Sort Implementation</span>
</h1>

**Learning objective:** By the end of this lesson, you'll be able to code a merge sort algorithm in Java.

## Merge sort demo
For this demo, lets consider an example of how a merge sort could help a book store to sort books based on prices.

```java
public class MergeSort {

    // Function to sort an array using merge sort
    public static void mergeSort(int[] array, int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            // Divide the array into two halves
            mergeSort(array, left, mid);
            mergeSort(array, mid + 1, right);

            // Merge the sorted halves
            merge(array, left, mid, right);
        }
    }

    // Function to merge two sorted halves
    private static void merge(int[] array, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] leftArray = new int[n1];
        int[] rightArray = new int[n2];

        // Copy data to temporary arrays
        System.arraycopy(array, left, leftArray, 0, n1);
        System.arraycopy(array, mid + 1, rightArray, 0, n2);

        int i = 0, j = 0, k = left;

        // Merge the temporary arrays
        while (i < n1 && j < n2) {
            if (leftArray[i] <= rightArray[j]) {
                array[k++] = leftArray[i++];
            } else {
                array[k++] = rightArray[j++];
            }
        }

        // Copy remaining elements
        while (i < n1) {
            array[k++] = leftArray[i++];
        }
        while (j < n2) {
            array[k++] = rightArray[j++];
        }
    }

    // Driver code to test the MergeSort algorithm
    public static void main(String[] args) {
        int[] bookPrices = {45, 10, 75, 30, 60};

        System.out.println("Original Array:");
        for (int price : bookPrices) {
            System.out.print(price + " ");
        }

        mergeSort(bookPrices, 0, bookPrices.length - 1);

        System.out.println("\n\nSorted Array:");
        for (int price : bookPrices) {
            System.out.print(price + " ");
        }
    }
}
```