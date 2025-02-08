# Merge_Sort
O Merge Sort é um algoritmo de ordenação baseado na técnica Dividir para Conquistar. Ele divide a lista em partes menores até ter listas unitárias e depois as mescla em ordem. Sua complexidade é O(n log n) em todos os casos, tornando-o eficiente para grandes conjuntos de dados, mas exige espaço extra para as divisões.

import java.util.Arrays;
public class MergeSort {
    public static void mergeSort(int[] arr) {
        System.out.println("Dividindo: " + Arrays.toString(arr));
        System.out.println();
        if (arr.length <= 1) {
            return;
        }
        int meio = arr.length / 2;
        int[] left = Arrays.copyOfRange(arr, 0, meio);
        int[] right = Arrays.copyOfRange(arr, meio, arr.length); 
        mergeSort(left); 
        mergeSort(right); 
        merge(arr, left, right); 
        System.out.println("Após a fusão: " + Arrays.toString(arr));
        System.out.println();
    }
    private static void merge(int[] arr, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                arr[k++] = left[i++];
            } else {
                arr[k++] = right[j++];
            }
        }
        while (i < left.length) {
            arr[k++] = left[i++];
        }
        while (j < right.length) {
            arr[k++] = right[j++];
        }
    }
    public static void main(String[] args) {
        int[] arr = {38, 27, 43, 3, 9, 82, 10,56,48,59}; 
        System.out.println("Array antes da ordenação:");
        printArray(arr);
        System.out.println();
        mergeSort(arr); 
        System.out.println("\nArray após a ordenação:");
        printArray(arr);
        System.out.println();
    }
    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
