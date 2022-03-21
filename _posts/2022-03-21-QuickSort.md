
# 퀵 정렬
## 구현
```java
import java.util*;                                                                                                                
                                                                                                                                   
    //201902954한현진                                                                                                                 
    //퀵 정렬                                                                                                                         
    public class QuickSort {                                                                                                       
        private boolean isSomething(int start, int end) {                                                                          
            return start >= end;       //배열에 값이 한 개만 있을 때는 리턴                                                                      
        }                                                                                                                          
                                                                                                                                   
        public void quickSort(int[] arr, int start, int end) {                                                                     
            if (isSomething(start, end)) {return;}                                                                                 
                                                                                                                                   
            int tmp;                                                                                                               
            int pivot = start;  //첫번째 값을 피봇으로 한다                                                                                   
            int p = start + 1; //피봇 다음 값부터 오른쪽으로 이동하며 피봇보다 큰 값을 찾는다                                                                
            int q = end; //배열의 끝에서 부터 왼쪽으로 이동하며 피봇보다 작은 값을 찾는다                                                                     
            //p값과 q값을 찾았으면 p와 q를 교환                                                                                                
            //다시 p는 오른쪽으로 이동하며 피봇보다 큰 값을 찾고 q는 왼쪽으로 이동하며 피봇보다 작은 값을 찾는다                                                            
            //p의 인덱스가 q의 인덱스 보다 클 경우에는 피봇과 q값을 교환 => 피봇은 정렬됨                                                                       
            //정렬된 피봇을 기준으로 앞부분과 뒷부분을 분할해서 정렬합니다                                                                                    
            //피봇을 기준으로 앞부분과 뒷부분을 분할해가며 정렬 후, 정렬이 완료되면 합병하여 정렬을 완성합니다                                                               
                                                                                                                                   
                                                                                                                                   
            //                                                                                                                     
            while (p <= q) {                                                                                                       
                while (arr[p] <= arr[pivot] && p <= end) { p++; }//피봇보다 큰 값을 찾을 때까지 오른쪽으로 이동                                       
                while (arr[q] >= arr[pivot] && q > start) { q--; }//피봇보다 작은 값을 찾을 때까지 왼쪽으로 이동                                      
                                                                                                                                   
                if (p > q) { //p의 값이 q의 값 보다 클 때 피봇과 q값을 교환                                                                        
                    tmp = arr[q];                                                                                                  
                    arr[q] = arr[pivot];                                                                                           
                    arr[pivot] = tmp;                                                                                              
                } else {  //p의 값보다 q의 값이 더 크면 p와 q를 교환                                                                             
                    tmp = arr[q];                                                                                                  
                    arr[q] = arr[p];                                                                                               
                    arr[p] = tmp;                                                                                                  
                }                                                                                                                  
            }                                                                                                                      
            //정렬된 피봇의 앞부분과 뒷부분을 분할해서 다시 퀵 정렬을 수행한다                                                                                 
            quickSort(arr, start, q - 1);                                                                                          
            quickSort(arr, q + 1, end);                                                                                            
                                                                                                                                   
        }                                                                                                                          
                                                                                                                                   
                                                                                                                                   
        public static void main(String[] args) {                                                                                   
            Random r = new Random();                                                                                               
                                                                                                                                   
            int[] arr = new int[20];                                                                                               
            for (int i = 0; i < arr.length; i++) {                                                                                 
                arr[i] = r.nextInt(1000);                                                                                          
            }                                                                                                                      
            for (int k : arr) {                                                                                                    
                System.out.printf("%d ", k);                                                                                       
            }                                                                                                                      
            System.out.println();                                                                                                  
                                                                                                                                   
            QuickSort dac = new QuickSort();                                                                                       
            dac.quickSort(arr,0,arr.length-1);                                                                                     
                                                                                                                                   
                                                                                                                                   
            for (int j : arr) {                                                                                                    
                System.out.printf("%d ", j);                                                                                       
            }                                                                                                                      
            System.out.println();                                                                                                  
        }                                                                                                                          
    }                                                                                                                              
```
## 실행 결과

![image](https://user-images.githubusercontent.com/80517119/159249471-a5d8742f-6cc4-4dc0-b992-19e10e2e0519.png)