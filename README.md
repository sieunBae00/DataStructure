# 1. LeetCode 225

'''cpp

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
