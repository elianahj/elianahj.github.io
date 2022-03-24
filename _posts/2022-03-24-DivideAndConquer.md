# BOJ 2630 색종이 만들기

![image](https://user-images.githubusercontent.com/80517119/159916461-29925446-ebd4-4600-a487-96435d6706a7.png)
![image](https://user-images.githubusercontent.com/80517119/159916626-a499aa94-2ce3-43ad-ba82-1fc322e6e1ff.png)

## 분할정복
* 입력 n = 8일 때 8x8 색종이 생성 
* 색종이의 전체 숫자가 모두 같은 숫자인지 확인 
* 색종이 전체가 같은 숫자가 될 때까지 색종이를 4등분으로 분할함
* 색종이 전체가 같은 숫자가 되면 색종이의 크기만큼 해당 색의 개수를 증가시킴
## 구현

```java
import java.util.*;

public class DivideandConquer {
    static int white, blue = 0;
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int paper[][] = new int[n][n];

        for (int i=0; i<n; i++) {
            for (int j=0; j<n; j++) {
                paper[i][j] = sc.nextInt();
            }
        }//nxn 색종이 생성
        divide_paper(paper, n, 0,0);
        System.out.println(white);
        System.out.println(blue);


    }

    public static void divide_paper(int paper[][], int n, int a, int b){ //색종이 분할
        boolean check=true;
        for (int i=a; i<a+n; i++) {
            for (int j=b; j<b+n; j++) {
                if(paper[a][b] != paper[i][j]){ //시작점 (a,b)에서부터 가로,세로 n만큼의 색종이가 같은 숫자로 이루어져있지 않는지 확인
                    check = false;
                }
            }
        }
        if(!check){ //색종이 전체의 숫자가 같지 않으면 :  n->n/2 4개로 분할
            divide_paper(paper,n/2, a,b);
            divide_paper(paper,n/2, a+n/2,b);
            divide_paper(paper,n/2, a,b+n/2);
            divide_paper(paper,n/2, a+n/2,b+n/2);

        }
        else{ //색종이 전체의 숫자가 같으면 : 색종이 크기만큼 해당 색의 개수를 증가시킴
            if(paper[a][b] ==0){//0이면 흰색 개수 증가
                white++;
            }else blue++;//1이면 파란색 개수를 증가시킨다
        }

    }
}
```