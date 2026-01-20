``` JAVA
import java.util.*;
class node{

    char ch;
    int freq;
    node left , right;

    node(char ch, int freq){
        this.ch = ch;
        this.freq = freq;
    }
}

class huffman{
    public static void print(node root,String s){
        if (root.left == null && root.right == null){
            System.out.println(root.ch + ": " + s);
            return;
        }
        print(root.left,s + "0");
        print(root.right, s+ "1");
    }

    static void main(String[] args) {

        String text = " huffman coding";
        Map < Character,Integer > freq = new HashMap<>();

        for(char c : text. toCharArray()) {
            freq.put(c, freq.getOrDefault(c, 0) + 1);
        }

        PriorityQueue<node> pq = new PriorityQueue<>(Comparator.comparingInt(a ->  a.freq));

        for(var e : freq.entrySet()){
            pq.add(new node(e.getKey(),e.getValue()));
        }

        while (pq.size() > 1){
            node l = pq.poll();
            node r = pq.poll();
            node parent = new node('-',l.freq + r.freq);
            parent.left = l;
            parent.right = r;
            pq.add(parent);
        }
        print(pq.peek()," ");
    }
}
```