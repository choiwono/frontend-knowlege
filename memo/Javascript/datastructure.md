# JavaScript로 데이터 구조 구현하기
--------

## Stack

```javascript

const stack = [];

stack.push(1);
stack.push(2);
stack.push(3);

// peek와 동일
stack[stack.length - 1]; 
stack.pop(); // 3
stack.pop(); // 2
stack.pop(); // 1

```

## Queue

```javascript

const queue = [];

queue.push(1);
queue.push(2);
queue.push(3);

queue.shift();
queue.shift();
queue.shift();

```

## LinkedList

```javascript

function Node(val) {
    this.val = val;
    this.next = null;
    this.prev = null;
}

let head = new Node(0);
let node1 = new Node(1);
let node2 = new Node(2);

head.next = node1;
node1.next = node2;
node1.prev = head;
node2.prev = node1;

```

## Map

```javascript

const map = {}
map['p1'] = 1;
map['p2'] = 2;

map['p1'];
map['p2'];

// or
const map = new Map();
map.set('p1', 1);
map.set('p2', 2);

map.get('p1');
map.get('p2');

```

## Set

```javascript

const set = new Set();
set.add(1);
set.add(2);

set.has(1);
set.has(2);
set.has(3);

```

## Tree

```javascript

const tree = [null, 5, 3, 8, 1, 4, 7, 9];

function Node(val) {
    this.val = val;
    this.left = left;
    this.right = right;
}

let root = new Node(5);
let left = new Node(3);
let right = new Node(8);

root.left = left;
root.right = right;

// 트리 순회 함수

function traversal(node) {
    if (node === null) return;

    traversal(node.left);
    traversal(node.right);
}

function traversal(node) {
    if (node === null) return;

    console.log('preorder', node.val);
    traversal(node.left);

    console.log('inorder', node.val);
    traversal(node.right);

    console.log('postorder', node.val);
}

```

