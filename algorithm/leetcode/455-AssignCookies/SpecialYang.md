**分发饼干**
https://leetcode.com/problems/assign-cookies/
---
### 思路一
说实话，我看的是英文版，第一次竟然没读懂题意了，打扰了！  
后来看了翻译，才明白题意：现在有一堆孩子，每个孩子的胃口不一样，有一堆饼干，饼干的大小也不一。我们的目标是把这些饼干尽可能多的分配给这些小朋友，求出最多满足多少个小朋友。
1. 只要饼干的尺寸大于等于孩子胃口，才可以满足
2. 一个饼干只能分给一个小朋友，一个小朋友只能吃一个饼干


典型的**贪心**做法，我们只需把最接近孩子胃口的饼干分配给对应的孩子即可，这样我们就可以把更大的饼干分给胃口更大的孩子。即优先使用最满足孩子胃口的饼干分配。

我们可以对孩子和饼干分配从小到大排序，然后遍历饼干，判断饼干与当前孩子大小关系，若满足，则分配给孩子，换下一个孩子和下一个饼干；若不满足，换下一个饼干与当前的孩子比较。
```java
    /**
     * 优先把尺寸接近孩子胃口的饼干分发
     *
     * 局部最优
     * @param g
     * @param s
     * @return
     */
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int child = 0, size = 0;
        while (child < g.length && size < s.length) {
            if (g[child] <= s[size++]) {
                child++;
            }
        }
        return child;
    }
```