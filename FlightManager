mport java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class FlightManager {

    public static void main(String[] args) {
    	
        Scanner dyg = new Scanner(System.in);
        
        int cityCount = dyg.nextInt();
        int roadCount = dyg.nextInt();
        int loadTime = dyg.nextInt();
        int flightTime = dyg.nextInt();
        
        manage(cityCount,roadCount,loadTime,flightTime,dyg);
    }


    public static void manage(int cCount,int rCount,int lTime, int fTime,Scanner dyg){
        int[][] adjList = new int[cCount][rCount];
        boolean[] visited = new boolean[cCount];
        int[] path;
        int[] distance = new int[cCount];
        int[] parent = new int[cCount];
        int[] roadPerCity = new int[cCount];
        int c1,c2,start,target,current,newest,time = 0;
        for (int i = 0; i < rCount; i++) {
            c1 = dyg.nextInt()-1;
            c2 = dyg.nextInt()-1;
            adjList[c1][roadPerCity[c1]] = c2;
            adjList[c2][roadPerCity[c2]] = c1;
            roadPerCity[c2] =  roadPerCity[c2] + 1;
            roadPerCity[c1] = roadPerCity[c1] + 1;
        }
          /*for (int i = 0; i < cCount; i++) {
            for (int j = 0; j < rCount; j++) {
                if(j < roadPerCity[i])
                    System.out.print(adjList[i][j] + " ");
            }
            System.out.println();
        }*/
        start = dyg.nextInt()-1;
        target = dyg.nextInt()-1;
        Queue<Integer> queue = new LinkedList<>();
        queue.add(start);
        parent[start] = -1;
        distance[start] = 1;
        time = 0;
        
        while(!queue.isEmpty()){
            current = queue.poll();
            if(current == target){
                path = new int[distance[target]];
                System.out.println(path.length);
                for (int i = path.length-1; i >=0 ; i--) {
                    path[i] = current;
                    current = parent[current];
                }
                for (int i = 0; i < path.length; i++) {
                    System.out.print(path[i]+1 + " ");
                }
                for (int i = 0; i < path.length-1; i++) {
                    if ((time / lTime) % 2 == 1) {
                        time = (time / lTime + 1) * lTime;
                    }
                    time = time + fTime;
                }
                System.out.println();
                System.out.println(time);
            }
            
            for (int i = 0; i < roadPerCity[current]; i++) {
                newest = adjList[current][i];
                if(!visited[newest]){
                    queue.add(newest);
                    distance[newest] = distance[current]+1;
                    parent[newest] = current;
                    visited[newest] = true;
                    
                }
            }
        }
    }
}
