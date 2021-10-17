对于进程而言，关闭进程的策略最好的情况是最近最少使用。

leetCode 146. LRU 缓存机制 https://leetcode-cn.com/problems/lru-cache/

#### 淘汰LRU缓存的核心原理
对于一个有序Cache表，只有get和put操作。
cache表队尾是最新使用元素，队头是最近最少使用元素

get操作
1、获取该元素（元素不存在返回-1）
2、需要把get的那个键值对置为cache表中最新的

put操作
1、更新该元素
2、需要把put的那个键值对置为cache表中最新的
3、如果容量超过预设容量，就把最久未使用键值对删除

#### 
```
 LinkedHashMap<>访问以后置尾的代码
        void afterNodeAccess(Node<K,V> e) { // move node to last
            LinkedHashMap.Entry<K,V> last;
            if (accessOrder && (last = tail) != e) {
                LinkedHashMap.Entry<K,V> p =
                        (LinkedHashMap.Entry<K,V>)e, b = p.before, a = p.after;
                p.after = null;
                if (b == null)
                    head = a;
                else
                    b.after = a;
                if (a != null)
                    a.before = b;
                else
                    last = b;
                if (last == null)
                    head = p;
                else {
                    p.before = last;
                    last.after = p;
                }
                tail = p;
                ++modCount;
            }
        }
```

缓存LRU解法代码:
```java
class LRUCache {
private int capacity;
private LinkedHashMap<Integer,Integer> cache;
    public LRUCache(int capacity) {
        cache=new LinkedHashMap<Integer,Integer>(capacity,0.75F,true);
        this.capacity=capacity;
    }
    public int get(int key) {
        makeRecently(key);
        return cache.getOrDefault(key,-1);
    }
    public void put(int key, int value) {
        if(cache.containsKey(key)){
            cache.put(key,value);
            makeRecently(key);
        }else{
            cache.put(key,value);
        }
        if(cache.size()>capacity){
            int firstElement=cache.keySet().iterator().next();
            cache.remove(firstElement);
        }
    }
    public void makeRecently(int key){
        int val =cache.getOrDefault(key,-1);
        if(val!=-1){
            cache.remove(key);
            cache.put(key,val);
        }
    }
}

```
#### 双向链表+HashMap的实现方式





