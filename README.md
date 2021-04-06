Dijkstra algoritm
```java
public class Dijkstra {

    private final int n;
    private final int[][] b;

    public Dijkstra(int n) {
        this.n = n;
        b = new int[n + 1][n + 1];

    }

    public void input(int i, int j, int w) {
        b[i][j] = w;
        b[j][i] = w;
    }

    public void D(int v) {
        int[] d = new int[n + 1];          //d: 노드까지 최단 거리 저장하는 변수
        boolean[] visit = new boolean[n + 1];


        for (int i = 1; i < n + 1; i++) {
            d[i] = Integer.MAX_VALUE;
        }

        d[v] = 0;  //시작노드 거리는 0
        visit[v] = true;


        for (int i = 1; i < n + 1; i++) { //시작노드와 연결되어있는 연결노드 d 갱신
            if (!visit[i] && b[v][i] != 0) {
                d[i] = b[v][i];
            }
        }

        for (int a = 0; a < n - 1; a++) {
            int small = Integer.MAX_VALUE;
            int min_index = -1;


            for (int i = 1; i < n + 1; i++) {  //최소인 d값 찾기
                if (!visit[i] && d[i] != Integer.MAX_VALUE) {
                    if (d[i] < small) {
                        small = d[i];
                        min_index = i;
                    }
                }
            }

            visit[min_index] = true;
            for (int i = 1; i < n + 1; i++) {
                if (!visit[i] && b[min_index][i] != 0) {
                    if (d[i] > d[min_index] + b[min_index][i]) {
                        d[i] = d[min_index] + b[min_index][i];
                    }
                }
            }

        }

        for (int i = 1; i < n + 1; i++) {  //결과 출력하기
            System.out.print(d[i] + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Dijkstra g;
        g = new Dijkstra(7);
        g.input(1, 2, 3);
        g.input(1, 4, 1);
        g.input(2, 3, 8);
        g.input(2, 4, 4);
        g.input(2, 5, 2);
        g.input(3, 6, 1);
        g.input(3, 7, 5);
        g.input(4, 3, 1);
        g.input(4, 7, 5);
        g.input(5, 3, 2);
        g.input(5, 6, 7);
        g.input(6, 7, 2);

        g.D(1);
    }
}
```
![KakaoTalk_20210406_223820316](https://user-images.githubusercontent.com/80372995/113720785-f2545b00-9729-11eb-819b-da29ffee3739.jpg)
![KakaoTalk_20210406_223820481](https://user-images.githubusercontent.com/80372995/113720791-f2ecf180-9729-11eb-92cf-a51d5d2d725f.jpg)
![KakaoTalk_20210406_223820640](https://user-images.githubusercontent.com/80372995/113720794-f3858800-9729-11eb-8f6c-29787a05c50f.jpg)
![KakaoTalk_20210406_223820879](https://user-images.githubusercontent.com/80372995/113720797-f3858800-9729-11eb-9df0-ac82e788b04a.jpg)



