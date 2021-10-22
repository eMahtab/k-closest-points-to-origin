# K closest points to origin
## https://leetcode.com/problems/k-closest-points-to-origin


# Implementation :
```java
class Solution {
    class Point {
        double distance;
        int index;
        Point(double distance, int index) {
            this.distance = distance; this.index = index;
        }
    }
    public int[][] kClosest(int[][] points, int K) {
       List<Point> list = new ArrayList<>(); 
       for(int i = 0; i < points.length; i++) {
           int[] point = points[i];
           double distance = Math.sqrt(point[0] * point[0] + point[1] * point[1]);
           list.add(new Point(distance, i));
       }
       Collections.sort(list, (p1, p2) -> Double.compare(p1.distance, p2.distance));
       int[][] result = new int[K][]; 
       for(int i = 0; i < K; i++) {
           result[i] = points[list.get(i).index];
       } 
        return result;
    }
}
```

## Note : The most important part was getting the comparator method right, Double.compare(p1.distance, p2.distance)
