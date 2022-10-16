# Prim Algorithm
## 20221016
<pre><code>
import java.util.ArrayList;
import java.util.List;
import java.util.PriorityQueue;
import java.util.Scanner;

public class Main {

    static class Edge implements Comparable<Edge> {
        int st, ed, cost;

        public Edge(int st, int ed, int cost) {
            this.st = st;
            this.ed = ed;
            this.cost = cost;
        }

        // 우선순위큐를 위해 기준을 정해준다
        @Override
        public int compareTo(Main.Edge o) {
            // return this.cost-o.cost;
            return Integer.compare(this.cost, o.cost);
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int V = sc.nextInt(); // 정점의 개수
        int E = sc.nextInt(); // 간선의 수

        // 인접리스트 초기화
        List<Edge>[] adjList = new ArrayList[V];
        for (int i = 0; i < V; i++) {
            adjList[i] = new ArrayList<>();
        }
        // 입력
        for (int i = 0; i < E; i++) {
            int st = sc.nextInt(); // 시작정점
            int ed = sc.nextInt(); // 도착정점
            int w = sc.nextInt(); // 가중치
            adjList[st].add(new Edge(st, ed, w));
            adjList[ed].add(new Edge(ed, st, w));
        }
        boolean[] visited = new boolean[V];
        PriorityQueue<Edge> pq = new PriorityQueue<>();

        visited[0] = true;
        // for (int i = 0; i < adjList[0].size(); i++) {
        // pq.add(adjList[0].get(i));

        // }
        pq.addAll(adjList[0]);

        int pick = 1; // 확보한 정점의 개수
        int ans = 0;

        while (pick != V) {
            Edge edge = pq.poll();
            if (visited[edge.ed])
                continue;
            ans += edge.cost;
            pq.addAll(adjList[edge.ed]);
            visited[edge.ed] = true;
            pick++;
        }
        System.out.println(ans);
    }
}
</code></pre>