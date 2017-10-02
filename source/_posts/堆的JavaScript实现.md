---
title: 堆的JavaScript实现
date: 2017-10-02 17:20:29
tags: [JavaScript,数据结构]
---
## 堆的逻辑定义 
n 个元素序列 {k<sub>1</sub>,k<sub>2</sub>...k<sub>i</sub>...k<sub>n</sub>}, 当且仅当满足下列关系时称之为堆：

(k<sub>i</sub> <= k<sub>2i</sub>,k<sub>i</sub> <= k<sub>2i+1</sub>) 或者 (k<sub>i</sub> >= k<sub>2i</sub>,k<sub>i</sub> >= k<sub>2i+1</sub>), (i = 1,2,3,4...n/2)

## 堆的典型实现
堆的一种典型实现是完全二叉树，因为是完全二叉树，所以可以用数组来表示这棵树，而不用链表，第i个数组元素的双亲节点是第(i-1)/2个数组元素，孩子节点是第(i+1)\*2-1和第(i+1)\*2个数组元素。
## JavaScript的实现

定义Heap类，有build, insert, delete和print四个方法，分别新建一个空堆，向堆中插入一个元素，从顶部取出一个元素，和打印堆中的所有元素；有一个size属性，表示了当前堆中的元素数量。

```javascript
class Heap {
    build() {
        this.data=[];
        this.size=0;
    }
    insert(x){
        this.data[this.data.length]=x;
        let cNum=this.data.length-1, pNum=parseInt(cNum/2);
        while(cNum>0) {
            if(this.data[cNum]>this.data[pNum]) {
                [this.data[cNum], this.data[pNum]] = [this.data[pNum], this.data[cNum]];
            } else {
                break;
            }
            cNum=pNum;
            pNum=parseInt(pNum/2);
        }
        this.size++;
        return this;
    }
    delete(){
        let result=this.data[0];
        if(this.data.length==1){
            this.size--;
            this.data.length=0;
            return result;
        }
        this.data[0]=this.data.pop();
        let pNum=0, lcNum, rcNum, cNum;
        while(pNum*2+1<this.data.length){
            lcNum = (pNum + 1) * 2 - 1;
            rcNum = (pNum + 1) * 2;
            if(this.data[lcNum]<this.data[rcNum]){
                cNum=rcNum;
            }
            else {
                cNum=lcNum;
            }
            if(this.data[pNum]<this.data[cNum]){
                [this.data[pNum], this.data[cNum]] = [this.data[cNum], this.data[pNum]];
            }
            else {
                break;
            }
            pNum=cNum;
        }
        this.size--;
        return result;
    }
    print() {
        console.log(this.data);
    }
}
```

测试代码：
```javascript
let h1=new Heap();
h1.build();
h1.print();
h1.insert(1);
h1.insert(13);
h1.insert(12);
h1.insert(122);
h1.insert(1221);
h1.insert(112);
h1.insert(121);
h1.insert(341);
h1.insert(12);
h1.insert(16);
h1.print();
while(h1.size>0){
    console.log(h1.delete());
}
console.log(h1)
```

测试结果：
```
[]
[ 8888888, 1221, 341, 122, 16, 112, 12, 121, 1, 12, 13 ]
8888888
1221
341
122
121
112
16
13
12
12
1
Heap { data: [], size: 0 }
```