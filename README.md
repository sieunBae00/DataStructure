# 1. LeetCode 225

```cpp

#include <iostream>

using namespace std;

#include <queue>

class MyStack {
public:
    queue<int> q;
    
    MyStack() {
    }
    
    void push(int x) {
        q.push(x);
        int s = q.size();

        for(int i=0; i<s-1; ++i){
            q.push(q.front());
            q.pop();
        }
    }
    
    int pop() {
        int v = q.front();
        q.pop();
        return v;
    }
    
    int top() {
        return q.front();
    }
    
    bool empty() {
        return q.empty();
    }
};
```


# 2. LeetCode 232

```cpp
#include<iostream>
using namespace std;
#include <stack>

class MyQueue {
    stack<int> s1;
    stack<int> s2;

public:
    MyQueue() {
        
    }
    
    void push(int x) {
        s1.push(x);
    }
    
    int pop() {
        while(s1.size()!=1){
            s2.push(s1.top());
            s1.pop();
        }
        
        int x = s1.top();
        s1.pop();

        while(s2.size()!=0){
            s1.push(s2.top());
            s2.pop();
        }

        return x;
    }
    
    int peek() {
        while(s1.size()!=1){
            s2.push(s1.top());
            s1.pop();
        }
        int x = s1.top();

        while(s2.size()!=0){
            s1.push(s2.top());
            s2.pop();
        }

        return x;
    }
    
    bool empty() {
        return s1.empty();
    }
};
```

# 3. Chapter 7

1.
```py
class ListQueue:
    def __init__(self):
        self.__queue = []

    def enqueue(self, x):
        self.__queue.insert(0, x)

    def dequeue(self):
        self.__queue.pop(len(self.__queue)-1)

    def front(self):
        return self.__queue[len(self.__queue)-1]

    def isEmpty(self)->bool:
        return len(self.__queue) == 0

    def dequeueAll(self):
        self.__queue.clear()

    def __str__(self):
        return str(self.__queue)
```

2.
```py

def checkSt(s):
    q = ListQueue()

    i = 0

    while(s[i] != '$'):
        q.enqueue(s[i])
        i += 1
    i += 1

    while(i <= len(s)-1):
        if(q.front() != s[i]):
            return False
        else:
            i += 1
            q.dequeue()
    return True
```

3.
```py

def sizecheck(self):
    return self.__queue.size()

for i in range(a.sizecheck()):
    b.enqueue(a.front())
```

4.
```py

#q1, q2 : 큐

def push(x):
    q1.push(x)

def pop():
    for i in range(q1.size()-1):
        q2.push(q1.peek())
        q1.pop()

    x = q1.peek()
    q1.pop()

    swap(q1, q2)

    return x
```


5.
```py

#s1, s2 : 스택

def enqueue(self, x): 
    s1.push(x)
    
def dequeue(self): 
    while(s1.size()!=1):
        s2.push(s1.top())
        s1.pop()
        
    int x = s1.top()
    s1.pop()

    while(s2.size()!=0):
        s1.push(s2.top())
        s2.pop()

    return x;
```

6.

enqueue()의 수행 시간 : O(1) (입력의 크기와 무관하게 일정)

dequeue()의 수행 시간 : O(1) (입력의 크기와 무관하게 일정)


7.

enqueue()의 수행 시간 : O(n) (맨 뒤에서 enqueue() 할 경우 n)

dequeue()의 수행 시간 : O(n) (맨 앞에서 dequeue() 할 경우 n)


8.
```py

def enqueue_rev(self, x):
    self.__queue.insert(0,x)

def dequeue_rev(self):
    self.__queue.pop()
```
를 추가

