# Leetcode
[USEFUL STL C++](#useful-stl-c) <br>
- [Vector](#vector) <br>
- [Queue](#queue) <br>
- [Priority Queue](#priority-queue) <br>
- [Stack](#stack) <br>
- [Set](#set) <br>
- [Unordered Set](#unordered-set) <br>
- [Map](#map) <br>
- [Unordered map](#unordered-map) <br>
- [List](#list) <br><br>


[Algorithm](#algorithm) <br>
- [最大公因數/最小公倍數算法(使用輾轉相除法)](#最大公因數gcd-輾轉相除法)<br>
- [排列組合類似題目](#排列組合類似題目使用遞迴算出每個結果) <br>
- [重複排列演算法](#重複排列演算法8--35) <br>
- [Combination列出所有可能](#combination列出所有可能candidates裡面-所有組成x數字的組合) <br>
- [Binary Search 應用](#binary-search-應用) <br>
- [BFS Search Algorithm](#bfs-search-algorithm-需要有一個queue存input近來的數字順序) <br>
- [Transpose Matrix Algorithm(NxN)](#transpose-matrix-algorithmnxn) <br>
- [Dynamic Programming](#dynamic-programming) <br>
- [需要判斷是否可以到終點，使用由結果往前推的概念](#需要判斷是否可以到終點用暴力法判斷結果會超時這時可以使用由結果往前推的概念55-jump-game-是其中一個應用) <br>
- [Stock及最大Profit問題](#stock以及最大收益的問題309-best-time-to-buy-and-sell-stock-with-cooldown) <br>
- [List相關用法](#list-all-subsets-refer-to-78-subsets) <br>
- [linkedlist-相關algorithms](#linkedlist-相關algorithms) <br>
- [Tree Concepts](#tree) <br>
- [Traversal In Binary Tree](#traversal-in-binary-tree以及algorithms) <br>
- [圖論](#圖論)<br>
- [Dictionary Tree](#dictionary-tree) <br>
- [Sort](#sort) <br>

# USEFUL STL C++

## Vector：
### Initial:
Vector\<type\> a;<br>
vector\<int\> number = {10, 20, 30};<br>

### Useful Function:
a.push_back()：add element<br>
a.pop_back(): remove the last element<br>
a.size(): vector長度<br>
a.begin(): iliterator 指標指到第一個元素<br>
a.end(): illiterator 指標指到最後一個元素<br>
a.front(): 回傳第一個元素<br>
a.empty(): 是否回空直<br>
a.swap(b): a, b array對調<br>
a.insert(it, num): 插入值<br>
a.erase(it.begin() + i): 刪掉第幾個元素<br>
sort(tmp.begin(), tmp.end());<br>
greater\<int\>() / less\<int\>()<br>
nth_element(nums.begin(), nums.begin() + n, nums.end()): 找出第n大的數，time complexity: O(n) 好用!!!!! <br>
(找到之後nums[n]就會是第n大的數!)

## Queue:
### Initial:
queue\<type\> myqueue;<br>

### Useful Function:
a.back(): 回傳最後一個element<br>
a.front(): 回傳第一個element<br>
a.push(): 放到queue的最後<br>
a.pop(): 拿出第一個element<br>
a.empty(): 是否回空直<br>
a.size()<br>

## Priority Queue:
`functions跟Queue一樣，差別差再越前面的一定越大`<br>
priority_queue< int,vector\<int\>,greater\<int\>()\>：這樣宣告則是越小的越前面<br>
***雖然vector中greater是最大的排最前面，但是其實queue在電腦中存的資料結構的方式"應該"也像array的方式， <br>
所以pop的話也是從最尾端取出，跟我們印象中的queue學到的樣子有點不太一樣，所以greater的話也是從大排到小，pop就一樣變成最小的最優先取出了!!要特別注意!*** <br>
a.top(): 回傳最前面的element但不取出<br>

 
## Stack
### Initial:
stack\<type\> mystack;<br>

### Useful Function:
a.top(): 回傳最上面的element但不取出<br>
a.push(): 放到stack最上面<br>
a.pop(): 移除最上面的element<br>
a.size()<br>
a.empty()<br>

## Set
### Initial:
set\<type\> myset -> `以紅黑樹implement，裡面的數都是有序的`<br>

### Useful Function:
a.insert(a): 把a放進集合<br>
a.erase(a): 把a移出<br>
a.count(a): 看a有沒有在裡面<br>

## Unordered Set
### Initial:
unordered_set\<type\> myset -> `使用hash table實踐，search速度幾乎是O(1)，但空間利用大`<br>

### Useful Function:
a.insert(a): 把a放進集合<br>
a.erase(a): 把a移出<br>
a.count(a): 看a有沒有在裡面<br>

## Map
### Initial:
map\<type1, type2\> mymap

### Useful Function:
a\[index\]: 得到對應的值, EX: my_map['a'] = b -> assign<br>
a.insert(pair<type1, type2>(value1, value2)) : 塞入一個pair<br>
a.count(a): 看a有沒有在裡面<br>
a..clear(): 刪除map整個element<br>
a.erase(key / it): 刪除鍵值對

## Unordered map
### Initial:
unordered_map\<type\> mymap -> `使用hash table實踐，search速度幾乎是O(1)，但空間利用大`<br>

### Useful Function:
a[idx]: 得到對應的值, EX: my_map['a'] = b -> assign<br>
a.insert(pair<type1, type2>(value1, value2)) : 塞入一個pair<br>
a.count(b): 看b有沒有在裡面<br>
a.clear(): 刪除map整個element<br>
a.erase(key / it): 刪除鍵值對<br>

## List:
### Initial:
list <Type> listT; <br>
list <Type*> listTP; <br>
 
int myints[] = {75,23,65,42,13};
list<int> mylist (myints, myints+5);

### Useful Function:
listT.push_back (b);	// 將 b 複製丟到 listT 後面 <br>
listT.push_front (f)	// 將 f 複製丟到 listT 前面 <br>
mylist.push_front (200) // Insert element at beginning <br>
mylist.pop_front(); // Delete first element <br>
mylist.push_back(myint); // Add element at the end <br>
mylist.pop_back(); // Delete last element <br>
mylist.insert(it,10); // 在itor前面insert 10， itor指的目標不會變 <br>
mylist.erase(it1); // delete itor所指的值 <br>
first.swap(second); // first 跟 second 互換 <br>
mylist1.splice (it, mylist2) // mylist2拼接到mylist1 <br>
```cpp
// set some initial values:
  for (int i=1; i<=4; ++i)
     mylist1.push_back(i);      // mylist1: 1 2 3 4

  for (int i=1; i<=3; ++i)
     mylist2.push_back(i*10);   // mylist2: 10 20 30

  it = mylist1.begin();
  ++it;                         // points to 2

  mylist1.splice (it, mylist2); // mylist1: 1 10 20 30 2 3 4
                                // mylist2 (empty)
                                // "it" still points to 2 (the 5th element)
                                          
  mylist2.splice (mylist2.begin(),mylist1, it);
                                // mylist1: 1 10 20 30 3 4
                                // mylist2: 2
                                // "it" is now invalid.
```


# Algorithm
## 最大公因數(GCD 輾轉相除法)
```cpp
int gcd(int x, int y){
        return y == 0 ? x : gcd(y , x % y);
    }
```
## 最小公倍數( x * y / gcd(x,y) )
```cpp
int lcm(int x, int y){
 return (x * y) / gcd(x, y);
}
```

## 排列組合類似題目：使用遞迴算出每個結果：
起始點：get_sequence(res, {}, nums);<br>
函數：<br>
```cpp
void get_sequence(vector<vector<int>> &res, vector<int> sub_array, vector<int> nums)
    {
        if(nums.empty())
        {
            res.push_back(sub_array); // 最終的結果放到res裡面
            return;
        }
        else
        {
            
            for(int i = 0; i < nums.size(); i++)
            {
                vector<int> tmp = sub_array;
                vector<int> tmp2 = nums;
                tmp.push_back(nums[i]);
                tmp2.erase(tmp2.begin() + i);
                get_sequence(res, tmp, tmp2); // 遞迴算出每個結果
            }
        }
    }
```

## 重複排列演算法(8! / 3!5!)
m 為大值，n為小值<br>
res需要使用long long int 以防overflow<br>
(8!) / (3!5!) => (8\*7\*6) / (1\*2\*3)，所以loop只需要算小值的次數就好<br>
```cpp
    int permut_wo_repeat(int m, int n){
         
        if(m == 0 || n == 0)
            return 1;
        
        long long res = 1;
        for(int i = 1; i <= n; i++)
        {
            res *= m - i + 1;
            res /= i;
        }    
        return (int)res;
    }
```

## Combination列出所有可能(candidates裡面 所有組成X數字的組合)
```cpp
void find_prob(vector<vector<int>>& res,  vector<int>& tmp, vector<int>& candidates, int target){  
          
        if(target == 0) // 表示combination是valid的  
        {  
            res.push_back(tmp);// 放數組到set裡  
            return;  
        }  
          
          
        for(auto i = 0; i < candidates.size() && target > 0; i++)   
        // 每次用loop找candidates裡面的數字，如果 <= target表是這個數字可以當作target的combination  
        {  
            if(candidates[i] <= target)  
            {  
                vector<int> tmp2 = tmp; // 用來存原本還沒放入這數字的array  
                tmp.push_back(candidates[i]); // 把新的數字放進去  
                find_prob(res,  tmp, candidates, target - candidates[i]); // 放入新數字之後再找下一個combination element => target - candidates[i]  
                tmp = tmp2; // 找完之後要把原本array放回來再找下一個element，EX: 2,"2" 找完 要找 2,"3".....  
            }  
        }  
          
    } 
```

## Binary Search 應用
```cpp
int find_lowbound(vector<int>& nums, int target){ // 找出第一個大於或等於target的元素
        
        int left = 0, right = nums.size() - 1;
        
        while(left <= right)
        {
            int mid = (left + right) / 2;
            
            if(nums[mid] < target)
                left = mid + 1;
            else
                right = mid - 1;
        }
        
        return left; 
    }
```


## BFS Search Algorithm: 需要有一個Queue存input近來的數字順序
```cpp
void BFS_find(vector<vector<int>> &res, queue<TreeNode*> &q)  
{  
          
        if(q.front() == nullptr) // 如果pointer是空值，return  
            return;  
          
        while(!q.empty()) // BFS algorithm  
        {  
            vector<int> tmp;  
            int level_num = q.size(); // 先把同level的node個數存起來 ex: level 2有9個數  
              
            for(int i = 0; i < level_num; i++)   
            // iterate 同level的每個數，每次for loop會跑完同一個level的所有數字  
            {  
                cout << q.front()->val << endl;  // 把同level數字push到tmp  
              
                if(q.front()->left != nullptr) // 如果有左右節點，放到queue後面當作下一個level  
                    q.push(q.front()->left);  
                if(q.front()->right != nullptr)      
                    q.push(q.front()->right);  
                  
                q.pop(); // 把已push的node pop out  
                  
            }  
        }  
    }  
```

## Transpose Matrix Algorithm(NxN)
```cpp
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        
        int n = matrix.size();
        
        for(int i = 0; i < n; i++)
        {
            for(int j = i + 1; j < n; j++)
                swap(matrix[i][j], matrix[j][i]); // 做transpose 只需要loop上對角線或是下對角線互換
        }
        
        
    }
};
```
## Dynamic Programming
### 需要判斷是否可以到終點(用暴力法判斷結果會超時)，這時可以使用由結果往前推的概念(55. Jump Game 是其中一個應用)
1. 由終點往前找看看哪一點是成功可以跳到終點的點，把它當作"上一個成功點"，再由上一個成功點再往前推。<br>
2. 如果目前的點的數值 + 點的位置 >= 上一個成功點，表示目前的點一定可以跳到上一個成功點，到達上一個成功點就表示可以跳到終點。<br>
3. 最後再看看上一個成功點會不會等於最一開始的點(i == 0)，如果是表示此點一定可以到達終點<br>
```cpp
class Solution {
public:
    
    bool canJump(vector<int>& nums) {
        
        int last_suc_pt = nums.size() - 1;
        
        for(int i = nums.size() - 2; i >= 0; i--)
        {
            if(i + nums[i] >= last_suc_pt)
                last_suc_pt = i;
        }
        
        return (last_suc_pt == 0) ? true : false;
    }
};
```
### Stock以及最大收益的問題(309. Best Time to Buy and Sell Stock with Cooldown)
```cpp
/*
Dynamic Program 題目:

開兩個vector:
    buy[i] = max(sell[i - 2] - price[i], buy[i - 1]): 前i天中以buy為結尾的最大利潤
    sell[i] = max(sell[i - 1], buy[i - 1] + price[i]): 前i天中以sell為結尾的最大利潤
    而最後結尾收益要最大一定是要sell[N]的時候
    
    explanation:
    but[i] = max(sell[i - 2] - price[i], buy[i - 1]):
        1.sell[i - 2]為前i-2天時最後賣掉之後的利潤因為i-1天前最後一個action時候是要rest,
          所以i - 1的時候不能算進來。
          而到了第i天前的最後一個axction是buy，表示rest完之後一天用price[i]的價格買了stock，
          所以總收益就會是:sell[i - 2] - price[i]。
        2.另外還有一種可能是buy[i-1] => i - 1天前最後買了stock，而第i天rest不買，
          此時的收益就是維持在buy[i-1]。
          
    sell[i] = max(sell[i - 1], buy[i - 1] + price[i]):
        1.sell[i - 1]為第i-1前最後是sell，然後rest，收益維持在sell[i - 1]。
        2.buy[i - 1] + price[i]為第i-1天最後是buy，然後i天前把它賣掉了，所以收益多一個price[i]。

*/
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        
        int n = prices.size();
        vector<int> buy(n, 0), sell(n, 0);
        
        if(n <= 1)
            return 0;
        
        buy[0] = -prices[0];
        buy[1] = max(buy[0], -prices[1]); // max(第0天買, 第0天不買第一天買)
        sell[1] = max(prices[1] - prices[0], 0); // max(第0天買第一天賣, 第0天沒有買，沒動作)
        
        for(int i = 2; i < n; i++)
        {
            buy[i] = max(sell[i - 2] - prices[i], buy[i - 1]);
            sell[i] = max(sell[i - 1], buy[i - 1] + prices[i]);
        }
        
        return sell[n - 1];
        
    }
};
```

## List All Subsets (refer to 78. Subsets) 
```cpp
// 需要列出所有可能，使用recursion 
// 第i 個數的subset只需要從i+1開始找就好了(避免重複)
// EX: {1,2,3} => 1會找到{1,2} {1,3} 如果2也去找1會變成{2,1} =====> 和{1,2}重複了
class Solution {
public:
    
    void find_subsets(vector<int>& nums, vector<vector<int>>& res, vector<int>& subseq, int index){ 
    // 找出所有subset
        
        for(int i = index; i < nums.size(); i++) // 從現有的index開始找，每找到一個數就把他加到res裡面
        {
            // EX: index = 0 時會從 {1, 2, 3} loop去找
            vector<int> tmp = subseq; // 把目前sub_seq存到tmp裡面避免目前的sub_seq被蓋掉
            
            tmp.push_back(nums[i]); // 把1加進去 
            res.push_back(tmp); // {1} 也算是subset
            find_subsets(nums, res, tmp, i + 1); // 1找過了，之後從1後面開始找{2,3}
        }
    }
    
    vector<vector<int>> subsets(vector<int>& nums) {
        
        vector<vector<int>> res;
        res.push_back({}); // 空集合也算subset
        vector<int> start = {};
        
        find_subsets(nums, res, start, 0); // start 是空的array，從index 0開始找
        return res;
        
    }
};
```
## LinkedList 相關Algorithms
### LinkedList Reverse
```cpp
    ListNode* reverse_list(ListNode* head){
        
        ListNode* first = head;
        ListNode* second = head->next;
        ListNode* third;
        
        first->next = nullptr;
        
        while(true)
        {
            if(second == nullptr)
                return first;
            
            third = second->next;
            second->next = first;
            first = second;
            second = third;
        }
    }
```
### LinkedList使用快慢指針用法 ====> 找出中間數
```cpp
ListNode* find_middle(ListNode* head){
        
        ListNode* fast = head;
        ListNode* slow = head;
        
        while(true){
            
            slow = slow->next;
            fast = fast->next->next;
            
            if(fast == nullptr) // 偶數
                return slow;
            if(fast->next == nullptr) // 奇數
                return slow->next;
            
        }
        
    }
```

## Tree
### Tree diameter: 任兩點的距離
max Diameter 定義: max(任一點的左子樹的max dept加上右子樹max dept) <br>
例題: 543. Diameter of Binary Tree <br>
```cpp
class Solution {
public:
    
    int get_length(TreeNode* node, int &max_dia){
        
        if(node == nullptr)
            return 0;
        
        int leftdept = 0, rightdept = 0;
        
        if(node->left != nullptr)
            leftdept = get_length(node->left, max_dia);
        if(node->right != nullptr)
            rightdept = get_length(node->right, max_dia);
        
        max_dia = max(max_dia, leftdept + rightdept); // 左右子樹最大深度相加跟當前的max_len比較大小
        return 1 + max(leftdept, rightdept);
        
    }
    
    int diameterOfBinaryTree(TreeNode* root) {
        
        int max_dia = 0;
        get_length(root, max_dia);
        return max_dia;
        
    }
};
```
### Tree Inverse: child node 左右對調 (101. Symmetric Tree)
```cpp
TreeNode* getsymetric(TreeNode* node){
        
        if(node == nullptr || node->left == nullptr && node->right == nullptr)
            return node;
        
        TreeNode* tmp = getsymetric(node->left);
        node->left = getsymetric(node->right);
        node->right = tmp;
        
        return node;
    }
```
### Same Tree: 比對兩個子樹是不是一模一樣
```cpp
bool same_tree(TreeNode* left, TreeNode* right){

    if(left == nullptr && right == nullptr)
        return true;

    if((left == nullptr && right != nullptr) || (left != nullptr && right == nullptr))
        return false;

    if(left->val != right->val)
        return false;

    return same_tree(left->left, right->left) && same_tree(left->right, right->right);
}
```

## Traversal in Binary Tree以及Algorithms:
Tree的找法分成三種: (1) Inorder Traversal (2) Preorder Traversal (3) Postorder Traversal (4) Level-Order Traversal<br>
### Inorder Traversal: 左->中->右
### Preorder Traversal: 中->左->右
### Postorder Traversal: 左->右->中

![image](https://github.com/t51113030/Leetcode/blob/master/pic/Tree.jpg) <br>

### Inorder + Preorder array 或 Inorder + Postorder array 可以決定一棵樹的構造，參考以下程式碼: <br>
#### 106. Construct Binary Tree from Inorder and Postorder Traversal<br>
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    
    TreeNode* buildTree(vector<int>& inorder, int ileft, int iright, vector<int>& postorder, int pleft, int pright){
        
        if(ileft > iright || pleft > pright) return nullptr;
        
        int i;
        for(i = ileft; i <= iright; i++)
            if(postorder[pright] == inorder[i]) break; // post 是最右邊為根節點，所以從右邊開始找
        
        TreeNode* node = new TreeNode(postorder[pright]);
        node->right = buildTree(inorder, i + 1, iright, postorder, pright - (iright - i) , pright - 1); // post 是左右中，所以中找完了就下一個就是找右邊subtree
        node->left = buildTree(inorder, ileft, i - 1, postorder, pleft, pright - (iright - i) - 1); // 右邊之後才是找左邊
        // 最難的是subtree 的左右邊界怎麼訂，一定要看清楚
        return node;
    }
    
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        
        TreeNode* tree = buildTree(inorder, 0, inorder.size() - 1, postorder, 0, postorder.size() - 1);
        return tree;
    }
};
```
#### 105. Construct Binary Tree from Preorder and Inorder Traversal<br>
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        
        TreeNode* tree = buildTree(preorder, inorder, 0, preorder.size() - 1, 0, inorder.size() - 1);
        
        return tree;
    }
    
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder, int pleft, int pright, int ileft, int iright){
        
        if(pleft > pright || ileft > iright)
            return nullptr;
        
        int bound;
        for(int i = ileft; i <= iright; i++)
        {
            if(preorder[pleft] == inorder[i]) // preoreder 是最左邊為根節點，所以從左邊開始找
            {
                bound = i;
                break;
            }
        }    
        
        TreeNode* node = new TreeNode(preorder[pleft]);
        node->left = buildTree(preorder, inorder, pleft + 1, pleft + bound - ileft, ileft, bound - 1); // pre 是中左右，所以中找完了就下一個就是找left subtree
        node->right = buildTree(preorder, inorder, pleft + bound - ileft + 1, pright, bound + 1, iright); //然後才是找right subtree
        
        return node;
        
    }
};
```
## 圖論
### 圖論的問題，以後看到選課之類的問題就要想到有向圖判斷是否有loop
### 想到有向圖就要想到三個變數
```cpp
vector<int> indegree // 負責存每個點的indegree
unordered_map<int, vector<int>> graph // 存每個點出去的時候指到那些點的關係圖
queue<int> q // 負責存目前indegree為0的點(表示出發點)
```
### indegree: vertex中有多少個箭頭指向自己
### outdegree: vertex有多少箭頭出去
### search方式: BFS or DFS <br>

## Dictionary Tree
主要有3個特點:
- [x] 根節點不包括字符，除了根節點之外每個子節點都會包括一個字母。
- [x] 各節點之間連接起來就是形成一個字串。
- [x] 每個節點的所有子節點包含的字元都不相同。

![image](https://github.com/t51113030/Leetcode/blob/master/pic/Dic_tree.jpg) <br>

### Implementation(最容易的方式就是每個節點開一個26個字母的array，每個array的內容為一個指標指向下一個node): Refer to 208. Implement Trie (Prefix Tree)
- [1] 需要先建立Node的data structure <br>
```cpp
class TrieNode{
 
public:
    TrieNode *child[26]; // 每個node都有26個pointer，代表著26個字母
    bool isWord; // 判斷最後走道這個node是不是一個word
    
    TrieNode() : isWord(false){ // initial 每個child指到nullptr
        
        for(auto &i : child)
            i = nullptr;
    }
    
};
```
- [2] 各個操作 <br>
```cpp
class TrieNode{
 
public:
    TrieNode *child[26]; // 每個node都有26個pointer，代表著26個字母
    bool isWord; // 判斷最後走道這個node是不是一個word
    
    TrieNode() : isWord(false){ // initial 每個child指到nullptr
        
        for(auto &i : child)
            i = nullptr;
    }
    
};

class Trie {
    
TrieNode *root;
    
public:
    /** Initialize your data structure here. */
    Trie() {
        root = new TrieNode();
    }
    
    /** Inserts a word into the trie. */
    void insert(string word) {
        
        TrieNode *curptr = root;
        for(auto &a : word)
        {
            if(curptr->child[a - 'a'] == nullptr) // insert的話就是一層一層找下來，如果沒有child就加一個
                curptr->child[a - 'a'] = new TrieNode();
            curptr = curptr->child[a - 'a'];
        }
        curptr->isWord = true; // 最後形成一個word，所以要把isWord = true
    }
    
    /** Returns if the word is in the trie. */
    bool search(string word) { 
        
        TrieNode *curptr = root;
        for(auto &a : word)
        {
            if(curptr->child[a - 'a'] == nullptr)
                return false;
            
            curptr = curptr->child[a - 'a'];
        }
        if(curptr->isWord == false)
            return false;
        
        return true;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) {
        
        TrieNode *curptr = root;
        for(auto &a : prefix)
        {
            if(curptr->child[a - 'a'] == nullptr)
                return false;
            curptr = curptr->child[a - 'a'];
        }
        return true;
    }
};
```

## Sort
### Quick Sort
Quick Sort是一種「把大問題分成小問題處理」的Divide and Conquer方法，概念如下： <br>
- 在數列中任意挑選一個數，稱為pivot，然後調整數列，使得「所有在pivot左邊的數，都比pivot還小」，而「在pivot右邊的數都比pivot大」。 <br>
- 接著，將所有在pivot左邊的數視為「新的數列」，所有在pivot右邊的數視為「另一個新的數列」，「分別」重複上述步驟(選pivot、調整數列)，直到分不出「新的數列」為止。 <br>
![image](https://github.com/t51113030/Leetcode/blob/master/pic/Q_sort.jpg) <br>
```cpp
void quick_sort(vector<int>& nums, int start, int end){ // start initial 為 0 end 為 nums.size() - 1
        
        if(start >= end)
            return;
        
        int pivot = nums[end];
        int i = start - 1; // 有多少個數在pivot左邊
        
        for(int j = start; j < end; j++)
        {
            if(nums[j] < pivot)
            {
                i++;
                swap(nums[i], nums[j]);
            }
        }
        swap(nums[i+1], nums[end]);
        quick_sort(nums, start, i);
        quick_sort(nums, i+1, end);
}
```
