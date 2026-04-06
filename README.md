#  笔记本

## 直接照抄：

```c++
#include<bits/stdc++.h>
#define int long long
#define endl '\n'
using namespace std;
const int N = -1;
const int MOD = 1;
#define MOD debug;

void solve() {
}

signed main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);//
    int _ = 1;
    //	cin>>_;
    //	cout<<fixed<<setprecision(1);
    while (_--) {
        solve();
    }
    return 0;
}

```



## 比赛直接查询使用：

### 头文件：

```c++
#include<bits/stdc++.h>//万能头，但是耗时高
#include<iostream>//适用：cin>> cout<<  
#include<cstdio>//正常编译所需要的头文件，适用：scanf printf
#include<cmath>//适用：abs(),sin(),cos();
#include<algorithm>//适用：min(),max()，sort()；
#include<vector>//stl的动态数组
#include<deque>//stl的双端队列
#include<list>//stl的链表
#include<queue>//stl的队列
#include<stack>//stl的栈
#include<set>//stl的集合
#include<map>//stl二元集合,可以当成数组来使用
#include<iterator>//迭代器的头文件
```

### 交互题使用函数

```c++
//注意,做交互题的时候不能关闭同步流
cout<<endl;//endl会刷新缓存区,使得缓存区里面的东西都输出出来
cout.flush();//手动刷新缓存区
fflush(stdout);//手动刷新缓存区
```

### 小技巧：

#### 切断同步流：

```c++
ios::sync_with_stdio(false);
cin.tie(0);
cout.tie(0);
```

#### cout小数点输出：

```c++
cin<<fixed<<setprecision(1);
```

#### 整行读入:

```c++
//注意，scanf和cin不会读入\n，但是getline是读入到\n截止，所以在前面有scanf或者cin的时候，我们需要添加一个getchar()来把回车读掉
getline(cin,name);//使用当前读入整行
```

#### scanf读入技巧

| 格式控制符     | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| %c             | 读取一个单一的字符                                           |
| %hd、%d、%ld   | 读取一个十进制整数，并分别赋值给 short、int、long 类型       |
| %ho、%o、%lo   | 读取一个八进制整数（可带前缀也可不带），并分别赋值给 short、int、long 类型 |
| %hx、%x、%lx   | 读取一个十六进制整数（可带前缀也可不带），并分别赋值给 short、int、long 类型 |
| %hu、%u、%lu   | 读取一个无符号整数，并分别赋值给 unsigned short、unsigned int、unsigned long 类型 |
| %f、%lf        | 读取一个十进制形式的小数，并分别赋值给 float、double 类型    |
| %e、%le        | 读取一个指数形式的小数，并分别赋值给 float、double 类型      |
| %g、%lg        | 既可以读取一个十进制形式的小数，也可以读取一个指数形式的小数，并分别赋值给 float、double 类型 |
| %s             | 读取一个字符串（以空白符为结束）                             |
| %[ 字符-字符 ] | 读取自定义的字符,满足条件就一直读入,不满足条件就停止         |

```c++
//在%号后面加上数字,代表只能读取这么长长度
scanf("%5d",&a);//代表最多读入五位整数
//在%号后面加上*,代表读入后进行舍弃
scanf("%*d %d",&a);//第一个带有*号的,会讲读入的东西舍弃,本质上第二个%d读入数据传递给a
//%[]内加上^代表取反,not条件,不读入
scanf("%[^\n]");//表示一直读入,直到遇到换行符为止
```

#### __int128开方

```c++
__int128 sqrt128(__int128 x) {//注意，__int128存在开方问题，可能因为爆炸导致无法正确开方。
    __int128_t y = (__int128_t) ceil(sqrt((long double) x));
    for (; y * y <= x; ++y);
    for (--y; y * y > x; --y);
//    return y * y == x;
    return y;
}
```

#### long double

```c++
//注意有些题及其傻逼，注意判断long double的范围
long double a;
scanf("%Lf", &a);
printf("%Lf", &a);//注意这里是大写L
cin >> a;
cout << a;
```

#### 在函数内定义函数

```c++
function</*返回值类型*/(/*参数类型*/, /*参数类型*/.....)> /*函数名字*/ = [&](/*参数类型*/ /*参数名*/,/*参数类型*/ /*参数名*/.....) {
       
    };//定义可递归函数
auto /*函数名字*/ = [&](/*参数类型*/ /*参数名*/,/*参数类型*/ /*参数名*/.....) {
       
    };//定义不可递归函数
```

#### 子集的枚举：

```c++
for (int str = i; str; str = (str - 1) & i) {
   //这样是枚举i的所有子集,str代表i的所有子集。

}
```

#### 二进制下1的个数：

```c++
__builtin_popcount(/*整数*/);
```

#### 取整：

```c++
ceil();//表示为向上取整，英语意思为天花板
floor();//表示为向下取整，英语意思为地板
Round();//表示为四舍五入，
```

#### 顺序赋值：

```c++
iota(/*数组起始地址*/,/*数组终止地址*/,/*第一个赋值*/);//这个函数为第一个数赋值，之后每一个赋值的数字都会加一
```

#### 全排列:

```c++
next_permutation(/*起始地址*/，/*终止地址的后一位*/);//是用来将数组转变为下一个全排列方案的函数
prev_permutation(/*起始地址，终止地址的后一位*/);//是用来将数组转变为上一个全排列的方案的函数
int main() {
    int a[10];
    for(int i = 1; i <= 5; ++i) {
        a[i] = i;
    }
    do {
        for(int i = 1; i <= 5; ++i) {
            cout << a[i] << " ";
        }
        cout << endl;
    } while(next_permutation(a + 1, a + 6));//想要用该函数生成全排列，那么数组原始必须处于从小到大的有序转态。
    return 0;
}
```

#### 内置数据存储极值:

```c++
numeric_limits</*内置数据类型*/>::max();//返回最大值
numeric_limits</*内置数据类型*/>::min();//返回最小值
```

#### 链式前向星:

```c++
int head[N],to[N],nt[N],tot=1;//这里是构建单项边的链式前向星星
void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
for(int i=head[u];i;i=nt[i]){//这里是遍历u所连接的所有的边的情况,i被赋值成存储的边的序号

}
//我们采用^1来寻找到另一条边,所以边的存储方式需要从0开始,01为一对,23为一对,初始化所有head=-1代表没有边了,此时for内的结束条件是~i
//或者你的边从2号开始,此时head可以为0,且for内的结束条件为0
```

#### 位运算骚操作

```c++
x&-x//返回最小的1对应二进制下面的数字
(~x)&(x+1)//返回最小的0改成当成1，二进制下的数字
```



### 编译器使用：

#### dev更改满足c++11/c++14的使用：

dev打开工具(按T之后按C)进入编译器选项，勾选编译时加入以下命令，并且在下方输入

```c++
-std=c++11
-std=c++14 
```

### STL工具附带函数解析：

#### 元素迭代器

```c++
 /*容器定义类型*/::iterator it;
```

#### array：

```c++
#include<array>//使用array的时候需要加上的头文件
array</*类型*/,/*数组长度*/> 名字
```

#### vector：

```c++
#include <vector>//在使用vector时应当加上这一个头文件
//初始化
vector</*类型*/> 名字[/*个数*/](/*每一个vector内有多少个元素*/,/*每一个元素的值*/);
vector</*类型*/> 名字(/*另一个vector的起点*/,/*另一个vector的终点*/);

//函数的适用，这里以a为例子
a.assign();//将a重新初始化，方式类似上述
a.back();//返回a的末尾元素
a.front();//返回a的第一个元素
a.clear();//清空a的元素
a.empty();//返回a是否为空
a.pop_back();//弹出队尾元素，没有元素是执行这一步会报错
a.push_back();//将元素加入队尾
a.emplace_back();//将元素加入队尾，这个可以自动识别变量类型
a.erase(/*起始地址*/,/*终止地址*/);//删除从起始地址到终止地址前一个元素
a.insert(/*插入地址*/,/*插入个数*/,/*插入元素*/)；//注意，原本在插入位置的元素，会往右边移动。
a.insert(/*插入地址*/,/*另一个vector的起始地址*/，/*另一个vector的终止地址*/)；//将另一个vector的元素插入，注意，终止地址对应的元素不会插入
a.size();//返回a内有多少元素
a.capacity();//返回a这个动态数组目前空间开的大小
a.resize(/*个数*/);//将a的空间调整至个数个，多则删，少则补
a.resize(/*个数*/，/*用来补的数字*/);//将a的空间调整至个数个，多则删，少则补
a.reserve(/*个数*/)；//将a的空间扩充到个数个
a.swap(b);//交换a，b内部的元素

//迭代器的使用
vector</*类型*/>::iterator 名字;

//常用算法
reverse(a.begin(),a.end());//倒置a内部的元素

```

#### string:

```c++
#include <string>//需要加上的头文件
//初始化
string zfc(/*字符串*/);
string zfc(/*字符串*/，/*开始下标*/，/*读入个数*/);//从字符串给予的下标开始，读入个数个
string zfc(/*字符串*/，/*读入个数*/);//截取字符串前个数个
string zfc(/*个数*/，/*单个字符*/);//赋予初值为个数个该字符
string zfc(/*字符串*/，/*开始下标*/);//注意，这里和上面的开始下标都是从位置0开始读入的

//函数的适用，这里以zfc为例子
zfc.size();//返回内部字符个数
zfc.length();//返回内部字符个数
zfc.data();//将字符串转换成printf中%s可以打印的字符串类型
zfc.c_str();//将字符串转换成printf中%s可以打印的字符串类型
zfc.max_size();//返回string对象最多能够包含的字符的个数
zfc.capacity();//返回重新分配内存前，string对象能包含的最大字符数
zfc.push_back();//在结尾处插入一个字符
zfc.insert(/*插入地址*/,/*字符串*/);// 在插入地址后插入字符串,原本处于该位置的字符串右移
zfc.append(/*字符串*/);//在结尾处插入一个字符串
/*符号运算符+，+=，=在string的操作中皆可使用*/
zfc.erase(/*迭代器*/);//删除zfc中迭代器指向的字符
zfc.erase(/*起始迭代器*/，/*终止迭代器*/);//删除[起始迭代器，终止迭代器)上的所有字符
zfc.erase(/*起始索引*/,/*长度*/);//删除字符串包括起始索引往后长度个字符；
zfc.clear()//删除字符串中所有字符
zfc.replace(/*起始索引*/,/*长度*/，/*字符或者字符串*/);//将包括起始索引往后长度个字符替换
zfc.replace(/*起始迭代器*/,/*终止迭代器*/,/*字符串*/);//将[起始迭代器，终止迭代器)内部的字符替换
zfc.find(/*字符串*/);//查找zfc的字串，如果找到，则返回找到的首索引，如果没找到，返回-1
zfc.find(/*字符串*/，/*数字*/);//从数字索引对应的位置开始查找zfc的字串，其余同上
zfc.rfind(/*字符串*/)；//这个同上，不过是从右侧开始进行查找
zfc.substr(/*起始索引*/,/*分割长度*/);//返回字符串的分割结果，注意这里是0(n)的时间复杂度
zfc.substr(/*起始索引*/);//代表从哪个位置开始分割
分割字符串还可以使用的函数：strtok();
头文件:#include<string.h>
    strtok(/*被分割的字符串*/,/*用来分割的字符的集合*/);//返回分割的结果
如果需要将整个字符串进行分割，那么则通常需要使用到while循环。
    在多次分割时,则需要变成如下的形式：strtok(NULL,/*用来分割的字符的集合*/);//将会一直分割字符串，如果已经分割完了，则返回NULL;

//string的大小写转换以及转换成数字
大小写转换方法一：利用tolower()和toupper();
	tolower(/*字符*/);//tolower是将内部字符转换成小写的形式，但是因为一次只能够转换一个字符，所以需要适用循环来进行复制
	toupper(/*字符*/);//同理

大小写转换方法二：利用transform函数
    transform是一个将操作用于给定范围的所有元素的函数。
    transform(/*起始地址*/,/*终止地址*/,/*存放结果的迭代器*/，::tolower);//将指定范围的字符串转换成小写	     transform(/*起始地址*/,/*终止地址*/,/*存放结果的迭代器*/，::toupper);//将指定范围的字符串转换成大写
字符串转换数字方法：利用atoi()和stoi()来进行转换;
	头文件：include<cstdlib>
	atoi(/*字符串*/)；//找到第一个非空格字符进行转换为int类型，直到遇到非数字时停止，返回读入的数字
	stoi(/*字符串*/);//转化同上，唯一区别为stoi会对数字进行检查，如果超过int范围就报错，atoi不会检查，超过上界输出上界，超过下界，输出下界。
	stod(/*字符串*/);////找到第一个非空格字符进行转换为double类型，直到遇到非数字时停止，返回读入的数字
将数字转化为字符串方法：利用to_string()函数来进行达成；
   	头文件：#include <string>
	to_string(/*数字*/)；//将数字转换为字符串。里面各种类型都可以传
```

#### map：

```c++
#include <map>//需要加上的头文件
//初始化
map</*key键值类型*/,/*value键值类型*/> mp;
map</*key键值类型*/,/*value键值类型*/> mp={{/*key键值类型*/,/*value键值类型*/};//赋值构造
map</*key键值类型*/,/*value键值类型*/> mp(mp1);
map</*key键值类型*/,/*value键值类型*/> mp(mp1.begin(),mp1.end());//赋值构造
map</*key键值类型*/,/*value键值类型*/,greater</*key键值类型*/>> mp;//指定数据按key降序存储
map</*key键值类型*/,/*value键值类型*/,less</*key键值类型*/>> mp;//指定数据按ke升序存储                             
//map中常见函数
插入数据:
mp.insert(pair</*key键值类型*/,/*value键值类型*/>(/*key*/,/*value*/));
mp.insert(make_pair(/*key*/,/*value*/));
mp[/*key*/]=/*value*/；

mp.begin();//返回排序后第一个键值对的迭代器
mp.end();//返回排序后最后一个键值对下一个的迭代器
map</*key键值类型*/,/*value键值类型*/>::iterator it;//创建迭代器
mp.size();//返回内部元素个数
mp.empty();//返回是否为空
mp.find(/*key*/);//在mp中查找key这一个键值的元素是否存在，如果存在，则返回迭代器，如果没有，返回end()这个迭代器
mp.count(/*key*/);//查找这个键的出现次数，但是mp中键是唯一的，所以值要不是0，要不就是1
mp.erase(/*key*/);//删除mp中key对应的键值对
mp.erase(/*迭代器*/);//删除mp中这一个迭代器所指向的键值对
mp.erase(/*起始迭代器*/，/*终止迭代器*/);//删除范围内[)区间的键值对，配合begin，end适用可以做到删除所有元素
mp.lower_bound(key);//按照小到大从左至右排序的数组中，找到第一个大于等于key的位置，并且返回地址
mp.upper_bound(key);//按照小到大从左至右排序的数组中，找到第一个大于key的位置，并且返回地址                              
```

#### unordered_map

```c++
其使用方法与map类似，只不过unordered_map底层是采用哈希表实现的，而map的底层是采用红黑树来实现的
```



#### queue:

```c++
#include<queue>//需要包含的头文件
//初始化
queue</*变量类型*/> dl;
queue</*变量类型*/,/*底层实现容器*/> dl;//这里的底层实现容器可以为链表，也可以为双端队列;既list</*变量类型*/>,deque</*变量类型*/>

//queue中常见函数
dl.push(/*元素*/);//将元素加入队尾
dl.pop(/*元素*/)；//删除队头元素
dl.front();//返回队列队头元素
dl.empty();//返回队列是否为空
dl.size()//返回内部元素个数
dl.back()//返回队尾元素

```

#### priority_queue:

```c++
#include<queue>//需要加上的头文件
//初始化
priority_queue</*变量类型*/> dl;//实现原理为内部排序，然后取最右侧的元素,默认适用<来进行排序
priority_queue</*变量类型*/,/*底层实现容器*/,/*调用的排序符号*/> dl;
/*如果第三个参数传入的是less<>,则变量类型会按照 < 来进行排序，如果传入的是greater<>,则会按照 > 来进行排序，对于自定义的结构体来说，使用的什么，就需要适用operator来重载相对应的符号*/
/*如果需要对已经存在的元素设置判断方法，则需要新开一个结构体，并且在这一个结构体内重载()号即可：
*/

```

```c++
struct type {//对已经存在元素的判断条件设置方法
    bool operator()(const pair<int,int> a,const pair<int,int> b) {
        return ；
    }
};
priority_queue<pair<int,int >,vector<pair<int,int> >,type> dl;
struct type {//对自定义元素的条件设置方法
	friend bool operator<(const type& x,const type& y) {//需要定义友元
		return ;
	}
};//注意，priority_queue是先进行排序，然后将排序后最右边的元素进行输出
priority_queue<type> dl;
```

```c++
//priority_queue常用函数
dl.push(/*元素*/);//将元素加入到优先队列中去
dl.pop();//弹出队顶端元素
dl.top();//返回队顶端元素
dl.size();//返回队列中元素的个数
dl.empty()；//返回队列是否非空
dl.emplace();//原地构造一个元素并且插入序列
```

#### deque:

```c++
#include<deque>//需要加上这一个函数头
//初始化
deque</*元素类型*/> dl;
deque</*元素类型*/> dl(n,value);//创建含有n个权值为value的双端队列
deque</*元素类型*/> dl={x1,x2,x3.....};//创建包含这些元素的双端队列

//deque中常见函数
dl.begin();//返回首元素的迭代器
dl.end();//返回队列尾元素下一个位置的迭代器
dl.size();//返回内部存放的元素的个数
dl.empty();//返回deque内部是否为空
dl.resize();//改变deque的大小为n，如果有则保留，没有就补零
dl.at(/*索引*/);//访问索引位置所对应的元素
dl[/*索引*/];//同样是可以访问索引位置对应的元素

dl.front();//返回队列队头元素
dl.back();//返回队列尾部元素
dl.push_front(/*元素*/);//将元素加入队列队首
dl.push_back(/*元素*/);//将元素加入队列队尾
dl.pop_front(/*元素*/);//删除队首元素
dl.pop_back(/*元素*/);//删除队尾元素

dl.assign()；//重新初始化，初始化的操作与一开始初始化的方式相同
    
dl.insert(/*迭代器*/,/*元素*/);//将元素插入到迭代器所指向的位置，并且返回新插入元素的迭代器
dl.insert(/*迭代器*/，/*个数*/,/*权值*/);//在迭代器指向位置插入若干个元素，并且返回第一个元素的迭代器
dl.insert(/*迭代器*/,/*起始迭代器*/,/*终止迭代器*/);//将[起始，终止)之内的元素插入到迭代器指向位置之前

dl.erase(/*迭代器*/);//删除迭代器指向元素
dl.erase(/*起始迭代器*/,/*终止迭代器*/);//删除[起始迭代器，终止迭代器)之间的元素

dl.clear();//清空dl内部的所有元素
dl.swap(/*另一个deque*/);//交换两个迭代器之间的元素，这样子是指针交换，时间复杂度为O1
dl.emplace(/*迭代器*/,/*元素*/);//在迭代器的位置插入元素，c11特有
dl.emplace_back(/*元素*/);//创建一个元素并且插入尾部,该函数直接在容器尾部构造元素，省去了复制移动元素的过程
dl.emplace_front(/*元素*/);//创建一个元素并且插入头部,该函数直接在容器头部构造元素，省去了复制移动元素的过程

```

#### stack：

```c++
#include<stack>//需要加入的头文件
//初始化
stack</*元素类型*/> zhan;
stack</*元素类型*/> zhan[/*个数*/];//创建个数个栈

//stack中常见函数
stack.empty();//判断栈是否为空
stack.pop();//删除栈顶元素
stack.size();//返回栈内元素个数
stack.top();//返回堆栈顶部的元素
stack.push(/*元素*/);//将元素压入栈顶
```

#### set:

```c++
#include<set>//需要加入的头文件
//初始化
set</*元素类型*/> st;//默认升序排列
set</*元素类型*/,/*排序方式*/> st;//这里的排序方式可以填入仿函数，greater<>,less<>什么的

//set常用函数解析
st.insert(/*元素*/);	//插入元素
st.erase(/*元素*/);	//删除q中的x元素,返回0或1,0表示set中不存在x
st.clear();//清空set表
st.empty();//判断set表是否为空，若是返回1，否则返回0
st.size();//返回set表中元素的个数
st.find(/*元素*/);//在set表中查找该元素，返回该元素的迭代器，若元素不存在，则返回指向元素尾部的迭代器即 q.end()
st.lower_bound(/*元素*/); //返回一个迭代器，指向第一个键值大于等于该元素的元素,若元素不存在，则返回指向元素尾部的迭代器即 q.end()
st.upper_bound(/*元素*/); //返回一个迭代器，指向第一个键值大于该元素的元素,若元素不存在，则返回指向元素尾部的迭代器即 q.end()

st.rend();		  //返回第一个元素的的前一个元素迭代器
st.begin();		  //返回指向q中第一个元素的迭代器

q.end();		 //返回指向q最后一个元素下一个位置的迭代器
q.rbegin();		 //返回最后一个元素
```

#### bitset：

```c++
#include<bitset>//需要加入的头文件
//初始化
bitset</*数字*/> bt;
bitset</*数字*/> bt(/*字符串*/);//这个字符串需要由1和0组成
bitset</*数字*/> bt(/*数字*/);//将数字转换陈二进制形式，存储到bitset中，多的位置补0，不够的舍弃大位置上的
bitset</*数字*/> bt[/*个数*/];//创建多个bitset表。类似于数组
 
//bitset常用工具
位运算的工具都可以使用
&//与符号，同时为1才是1，其余情况都是0，按照每一位数进行
|//或符号，有1就是1，两个都没1才是0，按照每一位数进行
~//非符号，这是单目运算符，1变成0，0变成1
^//异或符号，相同为0，不同为1
>>//所有数字整体往右边移动一格，相当于除二
<<//所有数字整体往左边移动一格，相当于乘二
    
bt.size();//返回位数
bt.count();//返回1的个数
bt.any();//返回是否有1；
bt.none();//返回是不是全是0
bt.set()；//将每一个位置上的数字改成1
bt.set(/*位置*/)；//将位置对应的数变成1，注意这里的位是从0开始
bt.set(/*位置*/,/*数字*/)；//将位置对应的数字变成传进来的数字,1或者0
bt.reset();//全部变成0
bt.reset(/*位置*/);//将位置对应的数字变成0
bt.flip()；//全部取反
bt.flip(/*位置*/)；//将位置上的数字取反
bt.to_ulong();//将bitset转化成unsigned long类型的的数字，超出范围就报错
bt.to_ullong();//将bitset转化成unsigned long long 类型的数字，超出范围就报错
bt.to_string();//将bitset转化为string类型的结果
bt.test(/*索引*/);//返回索引对应位置的数字是1还是0*
bitset可以通过下标来访问对应元素位置的数字
```

#### mutiset:

mutiset是一个按照升序排列的，内部元素可以重复的容器。

```c++
#include<set>//需要加入的头文件
//初始化
mutiset</*元素类型*/> mtst;
mutiset</*元素类型*/> mtst={/*元素*/,/*元素*/,/*元素*/,/*元素*/,/*元素*/};//进行初始化并且往里面加入若干元素

//mutiset常用工具
mtst.insert(/*元素*/);//将元素插入到must中插入元素
mtst.find(/*元素的值*/);//查找第一个元素值为这个的，并且返回该元素的迭代器，如果没有则返回末尾迭代器
mtst.erase(/*元素*/);//删除mtst中的这个元素，这里是删除所有值为这个元素的元素
mtst.erase(/*迭代器*/);//删除这一个迭代器所指向的元素
mtst.begin();//返回mtst开头迭代器
mtst.end();//返回mtst末尾迭代器
mtst.equal_range(/*元素*/);//返回值为这个的元素的范围，返回值是一个pair，first是开头迭代器，second是末尾迭代器
```

#### list:

```c++
#include <list>//需要加入的头文件
//初始化
list</*元素类型*/> lb={/*元素*/,/*元素*/,/*元素*/,/*元素*/,/*元素*/};//进行初始化并且往里面加入若干元素
list</*元素类型*/> lb(la);//拷贝构造
list</*元素类型*/> lb(/*元素个数*/,/*元素值*/);
list</*元素类型*/> lb(/*迭代器起始坐标*/,/*迭代器终止地址的下一个*/);//赋值迭代器这一段区间内的值创建链表
//常用工具
lb.size();//返回有效元素个数
lb.resize(/*元素个数*/,/*元素值*/);//调整容器有效元素大小,如果变小,则阶段,如果变大,则在末尾填上元素值,元素值默认为0
lb.empty();//返回容器是否为空
lb.clear();//清空容器
lb.front();//返回起始元素
lb.back();//返回末尾元素
lb.push_front();//头部插入元素
lb.pop_front();//删除头部元素
lb.push_back();//尾部插入元素
lb.pop_back();//尾部删除元素
lb.insert(/*迭代器*/,/*元素值*/);//在迭代器指向元素的前面添加一个元素,返回指向添加元素的迭代器
lb.insert(/*迭代器*/,/*元素个数*/,/*元素值*/);//跟上面同理,只不过时同时插入多个
lb.insert(/*a迭代器*/,/*起始迭代器*/,/*终止迭代器*/);//在a迭代器前面的元素添加其实迭代器到终止迭代器之间的元素
lb.erase();
```



## 最短路问题：

### floyed算法(n^3)

```c++
//使用注意点，floyed不能够解决出现负环的最短路(可以通过负环无限制的缩短两点之间的距离)。可以解决出现负边的情况。
//如果要判断的时候，只需要检测点到自己的距离是正还是负即可
//floyed算法的思想是通过逐步枚举中转点来缩短两点之间的距离。
void floyed(){
    for(int k=1;k<=n;k++){//枚举k作为中转点
		for(int a=1,a<=n;a++){
			for(int b=1;b<=n;b++){//枚举ab之间的点，用k来缩短ab之间的距离
                if(ab距离>ak距离+bk距离){
                    //使用k作为中转点缩短ab之间距离
                }
        	}
    	}	
    }
}
```

### dijkstra算法(nlogn)

```c++
//dijkstra算法用于解决固定一个点，这一个点到其他各个点的最短路问题
//注意，dijkstra算法不能够解决出现了负边的最短路(dijkstra运用了贪心的思想，如果出现负边，则会出问题)
//dijkstra算法的思想是，在每个能够到达的点中选择一个最小花费的点固定下来，然后更新经过这个点到达其他点的最短距离。
//优先选择最小的花费是因为如果我选择一个大的花费，那么之后一定会更大，而不会变小，所以最小的花费是已经固定下来的

int jl[N];//记录起始点到当前这一个点的距离
void dijkstla(int head) {
	jl[head]=0;//起始点自己到自己的距离为0
	memset(jl,0x3f,sizeof(jl));
	memset(bj,0,sizeof(bj));
	priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int> > > dl;//采用优先队列优化,第一维存距离；
    //注意，对于稠密图，也就是如果边数接近点数的平方个时，此时的复杂度接近n^2log,此时不用堆优化，时间复杂度更低
	dl.push({0,head});////起始点自己到自己的距离为0
	while(!dl.empty()) {
		auto dq=dl.top();
		dl.pop();
		if(jl[dq.second]<=dq.first) continue;
		for(int i=1; i<=N; i++) { //遍历当前这个点能够通向的其他点
			if(jl[i]>jl[dq.second]+"i和dq.second之间的距离") {
				jl[i]=jl[dq.second]+"i和dq.second之间的距离";
				dl.push(jl[dq.second]+"i和dq.second之间的距离",i);
			}
		}
	}
}
```

### Bellman-Ford算法(n^3或者n*m)

```c++
//bellmanford算法与floyed算法的内容相似，floyed是通过选择点来缩短两点之间的距离，而bellmanFord是通过选择点来缩短边长度
//同样也是解决单源最短路问题，从一个起点除法通向其他点之间的距离的
int jl[N];//单源最短路问题
int ljjj[N][N];//邻接矩阵ljjj[i][j]代表从i到j的长度
void bellman-ford(int head) {
	memset(jl,0x3f,sizeof(jl));//将长度进行初始化
	jl[head]=0;//本身到本身的距离为0
	for(int i=1; i<n; i++) { //枚举遍历n-1次,每一次枚举必然有最短边加入到图中间去,最短路径一定是一颗树，所以来n-1次即可，如果有多次，则代表有负环
//		for(int j=1; j<=m; j++) { //m为总边数，我们通过枚举边来逐步达到最短路
//			if(jl[zd]>jl[qd]+w){
//				jl[zd]=jl[qd]+w;
//			}//这里还可以进行修改，直接枚举两个点即可
		for(int a=1; a<=n; a++) {//在这里直接枚举两个点就可以直接枚举出每条边了，
			for(int b=1; b<=n; b++) {
				if(dis[b]>dis[a]+ljjj[a][b]) {
					dis[b]=dis[a]+ljjj[a][b];
				}
			}
		}
	}
}
```

### spfa算法(n*m)

```c++
//spfa是bellmanford的队列优化版本，采用队列进行优化
//bellmanford是逐步添加边进行优化，那么我们知道，我们从起始点逐步添加边，是逐步扩展到整个图中去的，我们只用考虑激活点即可
//spfa可以解决负环的情况，
int jl[N];
int vis[N];//标记当前点是否在队列中
int cnt[N];//建立一个数组，内部存储最短路的边数，如果最短路的边数大于了n，就说明出现了负环
vector<pair<int,int>> ljb[N];//采用邻接表对边进行存储
int spfa(int head) {
	memset(jl,0x3f,sizeof(jl));
	queue<int> dl;
	dl.push(head);
	jl[head]=0;
	vis[head]=1;
	while(!dl.empty()) {
		auto dq=dl.front();
		dl.pop();
		vis[dq]=0;
		cnt[dq]=0;
		for(auto it : ljb[dq]) {//遍历这条边的所有临边
			if(jl[it.second]>jl[dq]+it.first) {//遍历这个点相邻的所有其他边
				jl[it.second]=jl[dq]+it.first;
				//cnt[it.second]=cnt[dq]+1;
				//if(cnt[it.second]>=n) return 0;这两步是用来判断负环的
				if(!vis[it.second]) {
					dl.push(it.second);
					vis[it.second]=1;
				}
			}
		}
	}
}
```

## 最小生成树

### prim算法(mlongm)

```c++
//prim算法是用于求出来最小从生成树的算法,其根本思想类似于dijkstra算法,逐步选择离已经构成的最小生成树最近的点加入最小生成树。逐步扩大。运用了贪心的思维。
vector<pair<int,int> > jb[N];
int jl[N];
int bj[N];//标记每个点是否已经加入最小生成树中
int prim(int head) {
	priority_queue<int,vector<int>,greater<int> > dl;//采用优先队列优化选择，每次选择能够到达的最小值
	dl.push({0,head});
	while(!dl.empty()) {
		auto dq=dl.top();
		dl.pop();
		if(bj[dq.second]) {
			continue;
		}
		bj[dq.second]=1;
		jl[dq.second]=dq.first;
		for(auto it:ljb[dq.second]) {
			dl.push({it.second,it.first});
		}
	}
	int sum=0;
	for(int i=1; i<=n; i++) {
		sum+=jl[i];
	}
	return sum;
}
```

### kruskal算法(mlogm)

```c++
//采用并查集的思维方法,运用并查集判断是否在同一个并查集区间内。每次添加边都将两个集合进行合并
//同时也运用了贪心的算法，优先选择最小的边来构建最小生成树
vector<pair<int,int> > ljb[N];//采用邻接表来对边进行存储，邻接表的第一维目标点，第二维存长度
int bcj[N];
inline int cx(int dq) {
	return bcj[dq]=(bcj[dq]==dq?dq:cx(bcj[dq]));
}
inline void hb(int u,int v) {
	bcj[cx(u)]=cx(v);
}
int kruskal() {
	priority_queue<pair<int,pair<int,int> >,vector<pair<int,pair<int,int> > >,greater<pair<int,pair<int,int> > > > dl;
	//优先队列的第一个存长度，第二个pair存起始点和目标点
    for(int i=1; i<=n; i++) {
		for(auto it :ljb[i]) {
			dl.push({it.second,{i,it.first}});//采用优先队列,优先选择最小边加入进最小生成树,来保证能够得到的值是最小的
		}
	}
	int ans=0;
	while(!dl.empty()) {
		auto dq=dl.top();
		dl.pop();
		if(cx(dq.second.first)==cx(dq.second.second)) {
			continue;
		}//如果这两个在同一个集合之内则不进行计算
		hb(dq.second.first,dq.second.second);
		ans+=dq.first;
	}
	return ans;
}
```

## 分块：

###  数列分块

```c++
//数列分块是将数列进行分块，每隔同一个长度的格子属于同一个块内，类似于打标记的操作
int gs[N];//设立每一块的归属
int st[N],ed[N];//统计每一块的开始节点，每一块的终止节点
int len=sqrt(n);//这里是块的长度
int cnt=n/len;//这里是统计一共有多少个块
for(int i=1;i<=cnt;i++){
	st[i]=(i-1)*len+1;
    ed[i]=i*len;
}
ed[cnt]=n;//将最后一块进行特判
for(int i=1;i<=n;i++){
    gs[i]=(i-1)/len+1;//i-1代表i之前有多少个元素。这里是计算每一个块的分块情况
}

```

### 分块+莫队（带修）

//注意,带修莫队的分块长度是n的2/3次方，不然时间会t

```c++
//分块常用于莫队，通过将查询进行分块来减少其指针挪动范围
//我们首先对范围内的所有元素进行分块,标记处每一个元素所在的块内
//然后对范围进行排序
//我们先将左端点按照块的升序排序
//再将左侧同一个块内的询问按照右侧端点进行排序
int wz[N]; //标记每一个元素属于哪一个块
struct type {
    //用来存储询问
    int l,r,t;
} query[N];

bool cmp(type a, type b) {
    if (wz[a.l] != wz[b.l]) {
        //先将左侧端点按照块的递增方式排序
        return wz[a.l] != wz[b.l];
    } //对于同一个左侧块内的值，我们按照右侧位置进行排序，这个排序方法可以运用奇偶方法来优化
    if (wz[a.l] & 1) {
        return a.r > b.r;
    } else {
        return a.r<b.r;
    }
}

// bool cmp(Node a, Node b) {
//     return wz[a.l] < wz[b.l] ||
//            wz[a.l] == wz[b.l] &&
//            ((wz[a.r] < wz[b.r]) ||
//             wz[a.r] == wz[b.r] && a.t<b.t);
// } //排序,待修莫队使用这一个板子
inline void add(int x) {
    //我们可以通过添加两个函数来控制指针L和R的加减
}

inline void del(int x) {
}

void modui() {
    int L = 1, R = 0; //区间表示为[l,r]左闭右闭区间,这么赋值将初始区间设置为空
    for (int i = 1; i <= m; i++) {
        while (L < query[i].l) {
            del(L++);
        }
        while (L > query[i].l) {
            add(--l);
        }
        while (R < query[i].r) {
            add(++r);
        }
        while (R > query[i].r) {
            del(r--);
        }
    }
}

void solve() {
    int block = sqrt(n); //用来存每一个块内有多少个元素
    // int block = pow(n,0.67); //待修莫队中,用来存每一个块内有多少个元素
    for (int i = 1; i <= n; i++) {
        wz[i] = (i - 1) / block + 1; //确定每一个点所在的块内，后面的+1是用来确定起始分块从1开始，前面的-1将分块的目标往前移动一格
    }
}

```

## 高级结构

### ST表

```c++
//st[i][j]表示以i号为(左/右)端点，往(右/左)延伸1<<j长度的区间内的某个性质(gcd,lcm，最大值，最小值，指针等等)；
//在计算st表的时候，我们依次从小到大枚举区间的长度，由小区间推导出大区间的值
auto cx = [&](int l,int r) {//这一个是查询在l~r区间内的值
        int cd = log2(r - l + 1);
        return /*st[l][cd]和st[r - (1 << cd) + 1][cd]计算得到的值*/;
    };
```

### 树状数组

```c++
//树状数组能够支持动态查询前缀和,单点修改
//注意，树状数组查询的是前缀和,如果是单点查询的话,可以用树状数组存储差分数组。
int tree[N];
int lowbit(int x) {
	return x&-x;
}
int cx(int x) {
	int ans=0;
	while(x>0) {
		ans+=tree[x];
		x-=lowbit(x);
	}
	return ans;
}
void update(int x,int zhi) {
	while(x<=N) {
		tree[x]+=zhi;
		x+=lowbit(x);
	}
}
```

### 线段树

```c++
//线段树可以分为一下步骤
//建树(给树所有节点赋初始值，如果没有，可以不用)
//pushup(用子节点的状态来更新本身的状态，对于一个区间来说，如果其子区间发生了更新，那么则需要使用pushup)
//pushdown(这一个是再需要打lazytag的区间发生变动的时候, 需要将延迟标记下放,对子区间进行处理)
//query(线段树的区间查询操作)
//xg(线段树的区间修改操作)
//注意，不管是再哪个时候，往下递归导致区间的完整性被破坏的时候，需要用到pushdown，如果是子区间发生了修改，则需要用到pushup
int tree[N<<2];//线段树
int tag[N<<2];//每个区间的tag,注意tag标记着这个区间的子区间需不需要修改,而不是其本身需不需要修改
void pushup(/*根据实际情况传递*/) { //根据子区间来更新自己的区间

}
void pushdown(/*根据实际情况传递*/) { //将tag值往下放,注意下放的过程模拟操作,需要修改子区间的值

}
void build(int l,int r,int dq) { //l表示当前区间的左侧，r表示当前区间的右侧,dq表示当前区间所对应的序号
	if(l==r) {
		//修改tag值，修改tree线段树本身的值
	}
	int mid=l+r>>1;//将区间分成[l,mid][mid+1,r]这两份,
	build(l,mid,dq<<1);
	build(mid+1,r,dq<<1|1);
	pushup();
}
int cx(int l,int r,int ml,int mr,int dq) { //l表示当前线段的左侧区间,r表示当前线段的右侧区间,ml代表要修改的左侧区间,mr代表要修改的右侧区间,dq代表当前区间
	if(l<=ml&&mr<=r) {
		return ;
	}
	pushdown();
	int mid=l+r>>1;
	//这里填写询问,这里的询问可能会合并
	pushup();
	return ;
}
void xg(int l,int r,int ml,int mr,int dq,int zhi) {//与上面的查询相同,zhi代表再[ml,mr]区间内具体需要进行的操作
	if(l<=ml&&mr<=r) {
		return ;
	}
	pushdown();
	int mid=l+r>>1;
	//这里填写询问,这里的询问可能会合并
	pushup();
	return ;
}
```

### 动态开点线段树

```c++

```



### 主席树

```c++
//主席树是一个支持回溯操作的线段树，用于访问历史条件下的某一个查询
//主席树运用到了动态开点的的方法，以及共用前一个状态的数据,只创建更行了的值，剩下的没有变的格子公用上一个线段树的值
//注意，区间修改的主席树，打lazy标记的时候，不能够随便乱下放，因为每次修改，都会开一条链，这条链上的点会连接之前的点，但是新开的链所在的时间和他相连的点的时间是不同的，如果把lazy标记下放的话，会把lazy放置到一个他不应该存在的时间中去，导致查询之前的时间出错，所以我们需要永久化标记，只在开的点上完全覆盖的标记位置上打tag。并且保持标记不下放
 struct type {
	int l,r;//左儿子，右儿子
	//里面存每个区间的特征值
} tree[N<<5];
int gs=0;//动态开点,存每个线段的对应序号
int head[N];//这个函数用来在solve函数内接受build的返回值，用来记录每个树的根节点
int build(int dy,int l,int r,int zhi) {//dy表示上一个线段树对应这个线段树的编号
	int ls=++gs;//每次先新创建一个节点
    tree[ls]=tree[dy];//然后将这个节点先指向历史的值
	//下面在这里对值进行修改
    //tree[ls].?++什么的
	int mid=l+r>>1;
	if(l<r) {
		if(zhi<=mid) {//判断下一个节点往左边扩展还是右边扩展
			tree[ls].l=build(tree[dy].l,l,mid,zhi);
		} else {
			tree[ls].r=build(tree[dy].r,mid+1,r,zhi);
		}
	}
	return ls;//build返回的值代表这一个区间的序号,这样返回方便给其父亲区间赋值
}
int query(int u,int v,int l,int r,int k) {//在可持久化线段树中,一般还会使用两个线段树同步遍历的方法
	if(l==r) {
		return ;
	}
	int mid=l+r>>1;
	if(/*判断往哪一个方向进行遍历*/) {
		return;
	} else {
		return;
	}
}
```

### 树上启发式合并

$$
我们设cnt为用来存储目前节点的桶\\
树上启发式合并按以下的步骤进行遍历：\\
先遍历 𝑢 的轻（非重）儿子，并计算答案，但 不保留遍历后它对 𝑐𝑛𝑡 数组的影响；\\
遍历它的重儿子，保留它对 𝑐𝑛t 数组的影响；\\
再次遍历 𝑢 的轻儿子的子树结点，加入这些结点的贡献，以得到 𝑢 的答案。\\
$$



## tarjans算法

### 有向图

#### 求强连通分量

```c++
//有向图求强连通分量通常用于有向图缩点
int qz[N];//记录每个点的点权
int head[N],to[N],nt[N],tot;
int id[N],xu;//记录每个节点的dfs序号
int scc[N],sccsum;//记录每个点所在的强连通子图
int vis[N];//记录每一次搜索内部存在的节点
vector<int> sd[N];//记录每一个缩点后的点内部含有的子图
int ans=0;
int low[N];//记录每个子节点能够访问的dfs序号最高节点
void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
stack<int> zhan;
void tarjan(int dq) {
	id[dq]=++xu;
	low[dq]=xu;
	vis[dq]=1;
	zhan.push(dq);//将当前的点放入栈中
	for(int i=head[dq]; i; i=nt[i]) {
		int y=to[i];
		if(!id[y]) {//如果目标节点还没有被访问过
			tarjan(y);
			low[dq]=min(low[dq],low[y]);
		} else if(vis[y]) { //如果这个点已经被访问过了,为返祖边,注意这里的vis必须存在，这个只能对于同义次搜索中的使用，如果是多次搜索，则在后面的点指向联通子图时，low数组会发生错误。
			low[dq]=min(low[dq],low[y]);//这里如果用low会怎样
		}
	}
	if(low[dq]==id[dq]) {//stack内部村的是low只想上方的点，如果没有指向的，则内部会自己给自己赋值一个点
		sccsum++;
		while(1) {
			int mb=zhan.top();
			zhan.pop();
			sd[sccsum].push_back(mb);
			scc[mb]=sccsum;//记录每个点属于哪一个强连通子图
			vis[mb]=0;
			if(dq==mb) break;
		}
	}
}
void solve() {
	for(int i=1; i<=n; i++) {
		if(!id[i]) { //如果这个点没有被访问过。
			tarjan(i);
		}
	}
}
```



### 无向图

#### 求割点

$$
割点是指把连通图中的一个点删除后,剩下的点会被分成两个连通块
$$

```c++
//有向图和无向图求割点的情况都相似，只是边存几次的问题
//割点的判断条件是对于当前节点，有没有子节点能够通过额外边访问到我的上面来，如果有，则这个点不是割点
//如果没有，那么这个点就是割点
//注意，因为头节点没有上面的点，所以应该对头节点进行特判
int head[N],to[N],nt[N],tot;
inline void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
int id[N],xu;//记录每一个节点的dfs序
int low[N];//记录每个节点，以当前节点根节点的子树能够通过额外边访问到的最高点
int gd[N];//用于记录每个点是否是割点
void tarjan(int dq,int fu) {
	id[dq]=++xu;
	low[dq]=xu;
	int ci=0;
	for(int i=head[dq]; i; i=nt[i]) {
		int y=to[i];
		if(y==fu) continue;
		if(!id[y]) {
			ci++;
			tarjan(y,dq);
			low[dq]=min(low[dq],low[y]);
			if(fu&&low[y]>=id[dq]) { //如果这个节点不是根节点，而且子节点无法访问到比我这个节点更高的地方，那么我这个地方就是割点
				//注意，当多个环共用一个点的时候，割点是重合的，所以不可以在这里统计数量
				gd[dq]=1;//注意这里加入的位置，不要放在下面了 ，额外边只用来更新id的最小值，而判断割点是dfs边来进行的，
			}
		} else { //因为这里是无向图，所以不存在多次访问的情况，一次访问将所有连通块全部访问完,这里是易错点
			low[dq]=min(low[dq],id[y]);
		}
		//加下来判断这个点是不是割点
	}
	if(!fu&&ci>=2) { //如果当前的点是根节点,则判断往下的子节点个数
		gd[dq]=1;
	}
}
void solve() {
	for(int i=1; i<=n; i++) {
		if(!id[i]) {
			tarjan(i,0);
		}
	}
}
```

#### 求割边

$$
割边是指,去除掉一个连通图内部的一条边后,会分开成两个连通块
$$

```c++
//对于求割边，无向边和有向边的情况都差不多，存边的差异而已
//割边的判断条件是，能不能通过额外回到我这个点，或者我这个点的上方。如果不能回到，则删除这一条边，连通性会发生改变
int head[N],to[N],nt[N],tot;
inline void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
int id[N],xu;//记录每一个节点的dfs序
int low[N];//记录每个节点，以当前节点根节点的子树能够通过额外边访问到的最高点
int gb[N];//用于记录每个点是否是割点
void tarjan(int dq,int fu) {
	id[dq]=++xu;
	low[dq]=xu;
	for(int i=head[dq]; i; i=nt[i]) {
		int y=to[i];
		if(y==fu) continue;
		if(!id[y]) {
			tarjan(y,dq);
			low[dq]=min(low[dq],low[y]);
			if(low[y]>id[dq]) { //如果我下面的点无法通过其他的边回到我这个点,则说明我这个边是割边
				gb[(i+1)/2]=1;
			}
		} else { //因为这里是无向图，所以不存在多次访问的情况，一次访问将所有连通块全部访问完,这里是易错点
			low[dq]=min(low[dq],low[y]);//注意，割边时,这里需要使用low,因为点动,可以使用多条边
		}
	}
}
void solve() {
	for(int i=1; i<=n; i++) {
		if(!id[i]) {
			tarjan(i,0);
		}
	}
}
```

#### 求点双连通分量

$$
点双联通分量满足:删除任何一个点，剩下的图仍然联通
$$



```c++
//点双连通分量就类似于找个割点，然后将割点分配给下面的连通块
int head[N],to[N],nt[N],tot;
inline void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
int id[N],xu;//记录每一个节点的dfs序
int low[N];//记录每个节点，以当前节点根节点的子树能够通过额外边访问到的最高点
stack<int> zhan;
vector<int> lt[N];//用来存储得到的点双连通分量的内部点
int cnt;
void tarjan(int dq,int fu) {//因为这里是找割边，然后两点之间可能会有重边，所以需要记录每个边的编号
	id[dq]=++xu;
	low[dq]=xu;
	int son=0;
	zhan.push(dq);//我们一开始进行的时候，不用管栈中是不是之前放了东西，之前放了东西，就压在这个上面，不会影响到后来放的东西
	for(int i=head[dq]; i; i=nt[i]) {
		int y=to[i];
		if(y==fu) {
			continue;
		}
		if(!id[y]) {
			tarjan(y,dq);
			son++;
			low[dq]=min(low[dq],low[y]);
			if(low[y]>=id[dq]) { //当前这个点就像对于y来说就是割点
				cnt++;
//				while(zhan.top()!=dq) {
//					lt[cnt].push_back(zhan.top());
//					zhan.pop();
//				}
//				lt[cnt].push_back(dq);这里不能这么写,这里是易错点
//				如果当前点和当前点的孩子构成一个大的连通分量，然后中间出了一个小的连通分量的时候，大长度的连通分量会留在栈里面，这时候添加会出错
//				也就是说，dq和y之间，会插入其他的节点，所以不能直接将栈中到dq的元素直接加入联通点
				int sy=-1;
				while(sy!=y) {
					sy=zhan.top();
					zhan.pop();
					lt[cnt].push_back(sy);
				}
				lt[cnt].push_back(dq);
			}
		} else {
			low[dq]=min(low[dq],id[y]);
		}
	}
	if(!son&&!fu) {//如果是单纯的!fu，那么每个头节点都被放入了进去，还应该判断这个节点有没有子节点，如果有子节点，则这个节点被子节点加入了进去，所以不用加入了。这里是特判只有一个点的情况
		cnt++;
		lt[cnt].push_back(dq);
	}
}
void solve() {
	for(int i=1; i<=n; i++) {
		if(!id[i]) {
			tarjan(i,0);
		}
	}
}
```

#### 求边双连通分量

$$
边双连通分量满足:删除任意一条边,图仍然联通
$$

```c++
//边双连通分量适用于无向图缩点
//边双的定义是，再图中,找到一个子图，使得这个子图中，无论删除哪条边，其联通性质不会发生改变
//对于无向图的情况，我们只需要将这一个图的割边给去除，然后剩下的图就是边双
int head[N],to[N],nt[N],tot;
inline void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
int id[N],xu;//记录每一个节点的dfs序
int low[N];//记录每个节点，以当前节点根节点的子树能够通过额外边访问到的最高点
int gb[N];//记录割边的序号
int vis[N];//记录下面的dfs中有没有被跑过
void tarjan(int dq,int from) {//因为这里是找割边，然后两点之间可能会有重边，所以需要记录每个边的编号
	id[dq]=++xu;
	low[dq]=xu;
	for(int i=head[dq]; i; i=nt[i]) {
		if((i+1)/2==(from+1)/2||to[i]==dq) {//如果是父亲边，则直接跳过,
			continue;
		}
		int y=to[i];
		if(!id[y]) {
			tarjan(y,i);
			low[dq]=min(low[dq],low[y]);
			if(low[y]>id[dq]) {
				gb[(i+1)/2]=1;
			}
		} else {
			low[dq]=min(low[dq],low[y]);//用额外边去构造能够到达的最高点，来检测dfs边，如果是桥，则一定会在dfs边中
		}
	}
}
vector<int> sd[N];//类似于缩点,sd用来存储边双连通分量
int cnt=0;
void dfs(int dq,int fu) {
	vis[dq]=1;
	sd[cnt].push_back(dq);
	for(int i=head[dq]; i; i=nt[i]) {
		int y=to[i];
		if(to[i]==fu||gb[(i+1)/2]||vis[y]) continue;
		dfs(y,dq);
	}
}
void solve() {
	for(int i=1; i<=n; i++) {
		if(!id[i]) {
			tarjan(i,0);
		}
	}//再tarjan找到缩点之后，我们再来一次dfs,然后选中不是割边的边联通成一个连通块
	for(int i=1; i<=n; i++) {
		if(!vis[i]) {
			cnt++;
			dfs(i,0);
		}
	}
}
```

## 二分图

### 匈牙利算法(nm)

```c++
//匈牙利算法的本质是构建出增广路，然后对增广路进行取反，这样子每次构建出一条增广路，都会有一条边加入到匹配边中间去，最后直到无法构建出增广路为止
//增广路是从左侧非匹配点出发,依次经过非匹配边，匹配边，最后回到非匹配点的一条路径。
int head[N],to[N],nt[N],tot;
void build(int u,int v) {
	to[++tot]=v;
	nt[tot]=head[u];
	head[u]=tot;
}
int vis[N];//标记当前点是否出现在了这一次dfs的查询中
int match[N];//用来存储右边的点匹配到了哪一个左边的点
void dfs(int dq) {
	for(int i=head[dq]; i; i=nt[i]) {
		int y=to[i];
		if(!vis[y]) {
			if(!match[y]||dfs(match[y])) { //这里直接找到了右侧的待匹配点,或者是在后面找到了待匹配点，将路径直接取反，也可以构造
				match[y]=dq;
				return 1;
			}
		}
	}
	return 0;
}
void solve() {
	for(int i=1; i<=n; i++) { //这里是从小到大一次枚举左侧的点作为待匹配点,
		memset(vis,0,sizeof(vis));
		if(dfs(i)) ans++;
	}
}
```

### km算法(n^3)

```c++
//km是用来解决二分图带权最大权值匹配问题的一种方法
//注意，km算法只能解决"带权最大匹配一定是完备匹配，也就是每个点都可以匹配上"的情况
//km算法是匈牙利算法的进阶版本，运用贪心的思想，通过引入顶标对加入图中的边加以限制。直到构建完毕为止
//km限制图中只存在 左侧顶标+右侧顶标=边权 的边，我们可以选择已经匹配的图中，通过 左侧顶标-w，右侧顶标+w，来使得原本存在于交错路中的边不变，但是左侧在，右侧不在的 左侧顶标+右侧顶标 减少。来达到将边加入到图中去
int la[N],lb[N];//存储左右侧点顶标的值
int va[N],vb[N];//与匈牙利中的vis相似,用来标记左右侧顶点是不是在已经构建的增广路中
int match[N];//用来标记右边的点连接的是哪一个左侧的节点
int ljjj[N][N];//邻接矩阵存图
int upd[N];//upd[i]表示非匹配点i(右边)如果要将一条边加入到图，则最小需要改变顶标的值
bool dfs(int dq) {
	va[dq]=1;
	for(int i=1; i<=n; i++) {
		if(!vb[i]) { //如果这一个点这次没有访问
			if(la[dq]+lb[i]==ljjj[dq][i]) {
				vb[i]=1;//标记i号点，加入到增广路中去
				if(!match[i]||dfs(match[i])) {
					match[i]=dq;
					return 1;
				}
			} else {//如果这个点不在增广路中，那么我记算一次要减少的值
				upd[i]=min(upd[i],la[dq]+lb[i]-ljjj[dq][i]);
			}
		}
	}
	return 0;
}
int km() {
	for(int i=1; i<=n; i++) { //给顶标赋初始值,左侧顶标赋值为其左侧边的最大值，右侧顶点标记赋值为0
		la[i]=INT_MIN;
		lb[i]=0;
		for(int j=1; j<=n; j++) {
			la[i]=max(la[i],ljjj[i][j]);
		}
	}
	for(int i=1; i<=n; i++) { //枚举左侧的点作为待匹配点
		while(1) { //一直进行下去直到全部匹配完为止
			memset(va,0,sizeof(va));
			memset(vb,0,sizeof(vb));
			for(int j=1; j<=n; j++) {
				upd[i]=INT_MIN;
			}
			if(dfs(i)) break;//如果加入加入成功了，则直接break;
			int w=INT_MAX;
			for(int j=1; j<=n; j++) {
				if(!vb[j]) {//这里是找不在增广路中间的点
					w=min(w,upd[w]);
				}
			}
			for(int j=1; j<=n; j++) {
				if(va[j]) la[j]-=w;
				if(vb[j]) lb[j]+=w;
			}
		}
	}
}
```

## 网络流

### Edmonds-Karp增广路算法(nm^2)

```c++
//在解决费用流的时候，我们运用贪心的思考方法，将原本bfs找最近路径换成spfa找最优路径，我们把反向边看成负数,这样就需要使用到是spfa了。
int head[N],nt[N],to[N],val[N],tot=1;//注意，这里tot是从1开始的，边是从2开始存，2^1=3,3^1=2,这样子能够更加方便的去查询反向边
void build(int u,int v,int vl) {
	to[++tot]=v;
	val[tot]=vl;//用来存储当前这一条边的剩余可用流量
	nt[tot]=head[u];
	head[u]=tot;
}
int pre[N];//记录找出来的增广路中,当前这一个点是通过通过哪一条边到来的
int vis[N];//标记当前bfs中有没有访问过这一个点
int ll[N];//用来存储到达当前这个点能够汇集的最大流量
int bg,ed;//用来存储网络流的源点和汇点
int ans=0;//用来统计答案
bool bfs() { //返回能不能构建出增广路
	memset(vis,0,sizeof(vis));//先将这些都标记为没有访问
	queue<int> dl;
	dl.push(bg);
	ll[bg]=INT_MAX;//从源点能够出来无数的流量
	vis[bg]=1;
	while(dl.empty()) {
		auto dq=dl.front();
		dl.pop();
		for(int i=head[dq]; i; i=nt[i]) {
			int y=to[i];
			if(!val[i]||vis[y]) continue;//不跑流量为0的边，不跑已经访问过的点
			ll[y]=min(ll[dq],val[i]);//将到达y的这条边取min
			vis[y]=1;
			pre[y]=i;//标记到达y这个点走的是哪一条边
			dl.push(y);
			if(y==ed) {
				return 1;
			}
		}
	}
	return 0;
}
void update() {
	int dq=ed;//从末尾往前面递归计算
	while(dq!=bg) {
		int i=pre[dq];
		val[i]-=ll[ed];//注意，这里使用的流量是汇点的流量
		val[i^1]+=ll[ed];//正向边减少,反向边增加,往前计算
		dq=to[i^1];//往前跳动一个格子
	}
	ans+=ll[ed];
}
void solve() {
	while(bfs()) update();//一直找增广路，直到找不到为止
}
```

### Dinic算法(mn^2)

```c++
int head[N],to[N],nt[N],val[N],tot=1;
int now[N];//当前弧度优化，不跑已经无法往下再扩展的边
int bg,ed;//记录源点和汇点
void build(int u,int v,int vl) {
	to[++tot]=v;
	val[tot]=vl;
	nt[tot]=head[u];
	head[u]=tot;
}
int sd[N];//记录每一个点的深度
bool bfs() { //bfs一次,确定图上每一个点的深度,返回是否能够构建出增广路
	memset(sd,sizeof(0),sd);
	queue<int> dl;
	sd[bg]=1;
	dl.push(sd);
	now[bg]=head[bg];//给起点的访问弧初始化
	while(!dl.empty()) {
		auto dq=dl.front();
		dl.pop();
		for(int i=head[dq]; i; i=nt[i]) {
			if(sd[to[i]]||!val[i]) continue;//之前已经访问过的点，或者这条边的深度为0,那么我就不访问
			now[to[i]]=head[to[i]];//这一步很重要，给图中每一个访问到的点进行当前弧初始化
			sd[to[i]]=sd[dq]+1;
			dl.push(to[i]);
			if(to[i]==ed) return 1;
		}
	}
	return 0;
}
int dinic(int dq,int ll) { //ll表示访问到dq这个点的时候，从上面传递了多少流量给这个点
	if(dq==ed) return ll;
	int sy=ll;//用来记录这个点还剩下多少流量
	for(int i=now[dq]; i&&sy; i=nt[i]) {//注意，这里判断条件的sy不要掉，这是当前弧能够成立的基础
		now[dq]=i;//记录当前弧
		if(!val[i]||sd[dq]+1!=sd[to[i]]) continue;
		int use=dinic(to[i],min(sy,val[i]));//将流量传递给下一个点
		if(!use) {
			sd[to[i]]=0;//如果目标点无法构建出路，那么我直接删掉，用来剪枝
		}
		val[i]-=use;
		val[i^1]+=use;
		sy-=use;
	}
	return ll-sy;//返回这个点流下去的流量
}
void solve() {
	int ans=0;
	while(bfs()) {//直到构建不出增广路为止
		int use=0;
		while(use=dinic(bg,INT_MAX)) ans+=use;
	}
}
```

## 字符串

### 重要定义

$$
周期：设字符串s的长度为n。如果存在整数p\in (1 \leq p \leq n)，\\使得对于所有  i \in [p, n] ，有  s[i] = s[i-p] ，则称  p  是  s  的一个周期。\\
循环节：如果周期p满足 p \mid n,则称p是s的一个循环节\\
Border：如果字符串s长度为k的前缀等于长度为k的后缀，则称长度为k的前缀是s的一个border。\\
border性质:\begin{cases} 
若s为字符串的周期，则n-s长度的前缀一定为本身的border(可以利用这点求出border后来反推出周期)\\
本身border的border一定为本身的border
\end{cases}\\
$$

### kmp算法

$$
next数组:存储zfc的前缀的最大非平凡border的长度(非平凡意味着不等于本身)\\
字符串下标从1开始,故next[0]=1\\
我们通过对模式串构建next数组,然后对匹配串进行跳跃,则可o(n)事件复杂度之内匹配字符串
$$

#### 普通next数组

```c++
int nex[N]; //用来存储每个前缀的最大border
string zfc; //作为模式串参与匹配

void getnext() {
    //构建next数组,这个字符串从1号开始存储字符
    int dq = 0; //用来存储i号的border的长度
    for (int i = 2; i < zfc.size(); i++) {
        while (dq > 0 && zfc[dq + 1] != zfc[i]) {
            dq = nex[dq];
        }
        if (zfc[dq + 1] == zfc[i]) {
            dq++;
        }
        nex[i] = dq;
    }
}

vector<int> kmp(string ls) {
    //ls从1号位置开始存储字符串
    vector<int> wz; //用来存储出现的位置
    int dq = 0; //用来存储到目前为止，成功匹配的长度
    for (int i = 1; i < ls.size(); i++) {
        while (dq > 0 && zfc[dq + 1] != ls[i]) {
            dq = nex[dq];
        }
        if (zfc[dq + 1] == ls[i]) {
            dq++;
        }
        if (dq == zfc.size() - 1) {
            //如果完整出现，那么记录一下
            wz.push_back(i - zfc.size() + 2);
            dq = nex[dq];
        }
    }
    return wz;
}
```

#### 优化nextval数组

$$
我们发现,查询next数组时如果匹配不成功,那么就一直往后跳\\
在这个往后跳的过程中,如果判断条件的字符与上一个判断失败的字符一样的话，那么我们不用判断直接跳\\
我们优化掉这个跳跃的过程,可以使得next数组更优
$$



```c++
int nex[N]; //用来存储kmp数组的后跳数组
string zfc; //作为模式串参与匹配

void getnext() {
    //构建next数组,这个字符串从1号开始存储字符
    int dq = 0; //用来存储i号的border的长度
    for (int i = 2; i < zfc.size(); i++) {
        while (dq > 0 && zfc[dq + 1] != zfc[i]) {
            dq = nex[dq];
        }
        if (zfc[dq + 1] == zfc[i]) {
            dq++;
        }
        nex[i] = dq;
        if (zfc[nex[i] + 1] == zfc[i]) {
            nex[i] = nex[nex[i]];
        }
    }
}

vector<int> kmp(string ls) {
    //ls从1号位置开始存储字符串
    vector<int> wz; //用来存储出现的位置
    int dq = 0; //用来存储到目前为止，成功匹配的长度
    for (int i = 1; i < ls.size(); i++) {
        while (dq > 0 && zfc[dq + 1] != ls[i]) {
            dq = nex[dq];
        }
        if (zfc[dq + 1] == ls[i]) {
            dq++;
        }
        if (dq == zfc.size() - 1) {
            //如果完整出现，那么记录一下
            wz.push_back(i - zfc.size() + 2);
            dq = nex[dq];
        }
    }
    return wz;
}
```

### 字符串哈希

```c++
const int mod = 998244353 //1e9+7
const int base = 131;
const int N = 1;
int hash[N];
int p[N];

int get_hx(int l, int r) {
    return ((hash[r] - (hash[l - 1] * p[r - l + 1]) % mod) % mod + mod) % mod;
}

signed main() {
    string s;
    p[0] = 1;
    for (int i = 1; i < N; i++) {
        p[i] = (p[i - 1] * base) % mod;
    }
    for (int i = 1; i <= n; i++) {
        hash[i] = (hash[i - 1] * base + s[i]) % mod;
    }
}

```

### 最小表示法

```c++
//用于解决循环移位后最小字典序的字符串或数组  ans代表从左往右移动多少位构造成功答案不妨先考虑 S[i+k]>S[j+k] 的情况，我们发现起始位置下标 l 满足 i<=l<= i+k 的字符串均不能成为答案。因为对于任意一个字符串 S_{i+p}（表示以 i+p 为起始位置的字符串，p in [0, k]）一定存在字符串 S_{j+p} 比它更优。
int work(){
	int i=0;//假设从i开始
	int j=1;//假设从j开始
	int k=0;
	while(i<n&&j<n&&k<n){
		if(a[(i+k)%n]==a[(j+k)%n]){//左右相同拓展区间
			k++;
		}
		else{
			if(a[(i+k)%n]>a[(j+k)%n]){//将大的一段变成小的
				i+=k+1;
			}
			else{
				j+=k+1;
			}
			if(i==j){
				i++;
			}
			k=0;//重置区间重新比较

		}
	}
	return min(i,j);
}
void solve(){
	cin>>n;
	for(int i=0;i<n;i++){
		cin>>a[i];
	}
	int ans=work();//求解需从左往右移动多少位能构成最小字典序
	for(int i=0;i<n;i++){
		cout<<a[(i+ans)%n]<<' ';
	}
}
```

### 马拉车求回文

```c++
//求 *S* 中最长回文串的长度
void built(){//先拓展字符串防止出现偶数串的情况也防止边界问题
	cin>>s;
	c[cnt]='~';
	cnt++;
	c[cnt]='|';
	cnt++;
	for(int i=0;i<s.length();i++){
		c[cnt++]=s[i];
		c[cnt++]='|';
	}
	c[cnt++]='!';
}
void work1(){
	int mr=0,ans=0,mid=0;//p[i]代表以i为回文中心的最长回文长度 //mr代表最远的一个回文串的右端点 //mid代表最右边回文串的回文中心
	for(int i=2;i<=cnt-1;i++){
		if(i<=mr){
			p[i]=min(p[mid*2-i],mr-i+1);//已经在最远出现过的回文中所以当前点作为回文中心的长度一定有一个起点是 当前点到右边界的长度或者当前点与现在											最远的回文中心的对称点的回文长度比较取最小 保证所有情况都已经被遍历过
		}
		else{
			p[i]=1;//如果当前点为被拓展过则当前点的回文长度至少为本身也就是1
		}
		while(c[i-p[i]]==c[i+p[i]]){//暴力拓展回文长度//
			p[i]++;
		}
		if(i+p[i]>mr){//更新最远点
			mr=i+p[i]-1;
			mid=i;
		}
		ans=max(ans,p[i]);
	}
	cout<<ans-1;


}
void solve(){
	built();
	work1();
}
```

### ac自动机

```c++
int n;
const int N = 1;
string s;
int tr[N][26];
int fail[N];
int val[N]; //对应要求的各种值
//int head=0;
int cnt = 0;

void built() {
    //直接在字典树的对应边上跳转到失配的情况//
    queue<int> q;
    for (int i = 0; i < 26; i++) {
        if (tr[0][i]) {
            q.push(tr[0][i]);
        }
    }
    while (!q.empty()) {
        //模拟bfs 一层一层构建失配指针
        int u = q.front();
        q.pop();
        for (int i = 0; i < 26; i++) {
            if (tr[u][i]) {
                //因为当前点深度之前的点的失配指针都已经完成构建所以只需要找这个点之前的失配指针就行了
                fail[tr[u][i]] = tr[fail[u]][i]; //如果当前点失配了那就跑到这个点失配指针指向的点看看它是否有第i个字母
                q.push(tr[u][i]);
            } else {
                tr[u][i] = tr[fail[u]][i]; //已经失配的情况//			
            }
        }
    }
}

void solve() {
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> s;
        int m = s.length();
        int now = 0;
        for (int j = 0; j < m; j++) {
            //构造字典树
            int tmp = s[j] - 'a';
            if (tr[now][tmp] != 0) {
                now = tr[now][tmp];
            } else {
                tr[now][tmp] = ++cnt;
                now = cnt;
            }
        }
    }
    built(); //构建字典树之中的失配指针
    cin >> s;
    int m = s.length();
    int p = 0;
    for (int i = 0; i < m; i++) {
        int tmp = s[i] - 'a';
        p = tr[p][tmp]; //文本串匹配
        for (int t = p; t; t = fail[t]) {
            //遍历所有出现过的串
        }
    }
}

```

### KMP自动机

```c++
struct KMP{
    int nxt[N];
    int len;
    int aut[N][26];
    string p;
    void built(string s){//构建失配指针
        
        len=s.length();
        //cout<<len<<'\n';
        s='.'+s;
        p=s;
        for(int i=2;i<=len;i++){
            nxt[i]=nxt[i-1];
            while(nxt[i]&&s[nxt[i]+1]!=s[i]){
                nxt[i]=nxt[nxt[i]];
            }
            nxt[i]+=(s[nxt[i]+1]==s[i]);
        }
    }
    void authbuilt(){//kmp自动机
        aut[0][p[1]-97]=1;
       // cout<<p[1]<<'\n';
        for(int i=1;i<=len;i++){
            for(int j=0;j<26;j++){
                char tmp='a'+j;
                if(i!=len&& tmp==p[i+1]){
                    aut[i][j]=i+1;
                }
                else{
                    aut[i][j]=aut[nxt[i]][j];
                }
            }
        }
    }
}//kmp;
```



## 数学

### GCD与筛法：

#### 普通gcd

```c++
int gcd(int x, int y) {
    return y == 0 ? x : gcd(y, x % y);
}
```

#### 拓展欧几里得：

$$
由于辗转相除法可得\gcd(a,b)=\gcd(b, a\%b)\\
由于裴蜀定理可知，一定存在整数x,y，使ax+by=\gcd成立\\
所以我们可以利用辗转相除法的递归过程,求出x与y的值\\
首先,辗转相除的过程中,求\gcd(a,b),a=最大公因数,b=0时,此时系数x=1,y=0\\
对于两项\gcd(a,b)=\gcd(b, a\%b),可列出方程为 \begin{cases} 
ax_1+by_1=\gcd\\
bx_2+(a\%b)y_2=\gcd\\
  \end{cases}\\
  由于是递归过程,现我们已知a,b,x_2,y_2,\gcd,现在我们要倒推x_1,y_1\\
  我们设a=b\times\lfloor \frac{a}{b} \rfloor +r\, ,此时有a\%b=r,此时公式可替换为 
  \begin{cases} 
(b\times\lfloor \frac{a}{b} \rfloor +r)x_1+by_1=\gcd\\
bx_2+ry_2=\gcd\\
  \end{cases}\\
  合并同类相得\begin{cases} 
b(\lfloor \frac{a}{b} \rfloor x_1+y_1)+rx_1=\gcd\\
bx_2+ry_2=\gcd\\
  \end{cases}\\
  可以得到两个等式为:\begin{cases} 
\lfloor \frac{a}{b} \rfloor x_1+y_1=x_2  \\
x_1=y_2\\
  \end{cases}\\
  得到答案为:\begin{cases} 
y_1=x_2-\lfloor \frac{a}{b} \rfloor y_2  \\
x_1=y_2\\
  \end{cases}\\
$$

**下面是通解推导**
$$
现在我们已知ax_0+by_0=\gcd,我们需要求x与y的通解\\
我们可列出方程为\begin{cases} 
ax_0+by_0=\gcd\\
ax+by=\gcd\ \ (x和y为我们要求的通解)
  \end{cases}\\
  上下两式相减得:a(x_0-x)+b(y_0-y)=0\\
  移项得:a(x_0-x)=-b(y_0-y)=b(y-y_0)\\
  两边同除以a和b的\gcd(a,b)得:\frac{a}{\gcd}(x_0-x)=\frac{b}{\gcd}(y-y_0)\\
  因为\frac{a}{\gcd}与\frac{b}{\gcd}互质,故\frac{a}{\gcd}|(y-y_0)且\frac{b}{\gcd}|(x_0-x)\\
  我们两边同乘k得到等式:k\frac{a}{\gcd}(x_0-x)=k\frac{b}{\gcd}(y-y_0)\\
  因为上面互质关系,可令\begin{cases}
k\frac{b}{\gcd}=(x_0-x)\\
k\frac{a}{\gcd}=(y-y_0)\\
  \end{cases}\\
  故通解为:\begin{cases}
x=x_0-k\frac{b}{\gcd}\\
y=y_0+k\frac{a}{\gcd}\\
  \end{cases}\\
$$

```c++
//对于a或者b为负数的情况,我们可以把负号提到x,y上面去,保证a,b为正数
int exgcd(int a, int b, int &x, int &y) {//需要保证传入的参数为正数
    if (b == 0) return x = 1, y = 0, a;
    int gcd = exgcd(b, a % b, y, x);
    y -= a / b * x;
    return gcd;
}
```

判断解是否在范围内常用代码

```c++
bool check(int a,int b,int gcd,int x,int y,int minx,int maxx,int miny,int maxy) {
    //ax+by==你要满足的值,判断能否同时满足x在[minx,maxx]且y在[miny,maxy]的范围内
    //如果不能满足,下面自己定义返回值;
    int bsx = b / gcd, bsy = a / gcd;
    if (x < minx) {
        int bs = ceil(1.0 * (minx - x) / bsx);
        x += bs * bsx;
        y -= bs * bsy;
    }
    //进行这一步之后,x比minx要大了，此时我们把x拉到x的最小值
    int bs = floor(1.0 * (x - minx) / bsx);
    x -= bs * bsx;
    y += bs * bsy;
    //现在x是最小的了，我们移动y使得y变小,x变大
    if (y > maxy) {
        int bs = ceil(1.0 * (y - maxy) / bsy);
        y -= bs * bsy;
        x += bs * bsx;
    }
    if (minx <= x && x <= maxx && miny <= y && y <= maxy) {
        return 1;
    }else {//根据题目需要，可以更改成返回x与y的值
        return 0;
    }
}
```

#### 埃氏筛

```c++
int prim[N], tot;
int bj[N]; //用来记录每个数的最小质因子
void getprim() {
    for (int i = 2; i < N; i++) {
        if (!bj[i]) {
            prim[++tot] = i;
            bj[i] = i; //每个数字除以这个数字
            for (int j = 2 * i; j < N; j += i) {
                if (!bj[j])bj[j] = i;
            }
        }
    }
}
```

#### 欧拉筛

```c++
int prim[N], tot;
int bj[N]; //用来记录每个数的最小质因子
void getprim() {
    for (int i = 2; i < N; i++) {
        if (!bj[i]) {
            prim[++tot] = i;
            bj[i] = i; //每个数字除以这个数字
        }
        for (int j = 1; j <= tot && prim[j] * i < N; j++) {
            bj[prim[j] * i] = prim[j];
            if (i % prim[j] == 0)break;
        }
    }
}
```

#### 大整数的GCD

$$
当我们求两个大整数(\_\_int128也存不下)的GCD的时候,\%运算非常耗费时间\\
这时候使用stein算法可在\mathcal{O}\left( \log(\max\{a, b\})^2 \right)求出\gcd\\
算法流程为:
  \begin{cases} 
  如果a=0或者b=0,则\gcd(0,b)=b,\gcd(a,0)=a\\
  如果a,b都为偶数则\gcd(a,b)=2*\gcd(a/2,b/2)\\
  如果a为奇数,b为偶数,则\gcd(a,b)=\gcd(a,b/2)\\
  如果a为偶数,b为奇数,则\gcd(a,b)=\gcd(a/2,b)\\
  如果a,b都为奇数,则设a>b,则\gcd(a,b)=\gcd(b,a-b)\\
  \end{cases}\\
$$

### 同余与模与逆元

#### 欧拉函数

$$
欧拉函数 \varphi(n) 定义为：
\varphi(n) = \sum_{d=1}^n [\gcd(d, n) = 1],其中\varphi(1)=1\\
更具体来说为:
定义欧拉函数 \varphi(n) 为正整数n与序列 1,2,...,n-1,n 中互质的数的个数。\\
设 n=p_1^{\alpha_1}p_2^{\alpha_2}...p_k^{\alpha_k}，则利用容斥原理可得  \\
\varphi(n) = (p_1 - 1)p_1^{\alpha_1 - 1} \times (p_2 - 1)p_2^{\alpha_2 - 1} \times ....
\times (p_k - 1)p_k^{\alpha_k - 1}\\
利用该式结合欧拉筛可以得到每个数字的欧拉函数\\\\
欧拉函数重要性质:n=\sum_{d|n}\varphi(d)
$$

求多个数字的欧拉函数：

```c++
int prim[N], tot;
int bj[N]; //用来记录每个数的最小质因子
int phi[N]; //记录每个数字的欧拉函数
void oulahanshu() {
    phi[1] = 1;
    for (int i = 2; i < N; i++) {
        if (!bj[i]) {
            prim[++tot] = i;
            bj[i] = i; //每个数字除以这个数字
            phi[i] = i - 1;
        }
        for (int j = 1; j <= tot && prim[j] * i < N; j++) {
            bj[prim[j] * i] = prim[j];
            if (i % prim[j] == 0) {
                phi[prim[j] * i] = phi[i] * prim[j];
                break;
            }
            phi[prim[j] * i] = phi[i] * (prim[j] - 1);
        }
    }
}
```

求单个数字的欧拉函数O(log(a))

```c++
int getoula(int a) {
    // 求n的欧拉函数
    int phi = 1;
    for (int i = 2; i * i <= a; i++) {
        if (a % i == 0) {
            phi *= (i - 1);
            a /= i;
            while (a % i == 0) phi *= i, a /= i;
        }
    }
    if (a > 1) phi *= (a - 1);
    return phi;
}
```

#### 欧拉定理&费马小定理

$$
欧拉定理:\\
如果 \gcd(a, m) = 1，那么 a^{\varphi(m)} \equiv 1 \pmod{m}。\\
其中\varphi(m)为欧拉函数
\\
费马小定理:\\
如果p为质数，如果 p不能整除a，那么 a^{p-1} \equiv 1 \pmod{p}。\\
我们可以利用上面定理,来解决模数不是质数的情况,来求逆元 \\
设 m 为正整数，a \in \mathbb{Z}_m, \gcd(a, m) = 1，逆元 a^{-1} = a^{\varphi(m)-1}  \\
设 p 为质数，a \in \mathbb{Z}_p, 0 < a < p，逆元 a^{-1} = a^{p-2}\\
$$

#### 拓展欧拉定理(欧拉降幂)

$$
a^c \equiv a^{c \bmod \varphi(m) + \varphi(m)} \pmod{m}\quad \text{若} c \geq \varphi(m)\\
当c过大的时候,我们可以利用该公式降低幂次使用快速幂进行求解
$$

#### 线性递推求多项逆元

$$
我们现在已经知道前i-1项逆元,现在要求第i项逆元,即i^{-1}\\
p=i\times\lfloor \frac{p}{i} \rfloor +p\%i,我们设k=\lfloor \frac{p}{i} \rfloor,t=p\%i，可知t<i\\
此时有:i\times k+t\equiv0(mod\ p)\\
移项得:i\times k\equiv -t(mod\ p)\\
两边同乘i^{-1},t^{-1}得:t^{-1}\times k\equiv -i^{-1}(mod\ p)\\
i^{-1}\equiv-t^{-1}\times k(mod\ p)\\
故我们可以使用递推公式:i^{-1}=((-(p\%i)^{-1}*\lfloor \frac{p}{i} \rfloor)\%p+p)\%p进行递推
$$

```c++
int inv[N];
void getinv() {
    inv[1] = 1;
    for (int i = 2; i < N; i++) {
        inv[i] = ((-1 * inv[MOD % i] * (MOD / i)) % MOD + MOD) % MOD;
    } //注意(MOD / i)用了括号使得向下取整,不要忘记加了
}
```

#### 解同余方程组

$$
求方程组\begin{cases} 
	x\equiv a_1(mod\ m_1)\\
	x\equiv a_2(mod\ m_2)\\
	.\\.\\.\\
	x\equiv a_k(mod\ m_k)\\
  \end{cases}\\
  我们依次合并两项,将大小为k的问题转换为大小为k-1的问题,具体来说,考虑k=2的情况\\
  此时有\begin{cases} 
	x\equiv a_1(mod\ m_1)\\
	x\equiv a_2(mod\ m_2)\\
  \end{cases}--->\begin{cases} 
	x= a_1+y_1\times m_1\\
	x= a_2+y_2\times m_2\\
  \end{cases}\\
  a_1+y_1\times m_1=a_2+y_2\times m_2\\
  移项得:y_1\times m_1+y_2\times (-m_2)=a_2-a_1,其中a_2-a_1,m_1,m_2是定值\\
  运用拓展欧几里得,当\gcd(m_1,m_2)|a_2-a_1时有解，有解时,我们可以解出y_1,y_2\\
  y_1的通解为:y=y_1-k\frac{m_2}{\gcd},y_2的通解为:y=y_2+k\frac{m_1}{\gcd}\\
  带入得:x=a_1+(y_1-k\frac{m_2}{\gcd})\times m_1=a_2+(y_2+k\frac{m_1}{\gcd})\times m_2\\
  化简得:x=(a_1+y_1\times m_1)-k\frac{m_1m_2}{\gcd}=(a_2+y_2\times m_2)+k\frac{m_1m_2}{\gcd}\\
  可以发现\frac{m_1m_2}{\gcd}=lcm(m_1,m_2)\\
  我们令x_0=a1+y_1\times m_1=a_2+y_2\times m_2\\
  所以\begin{cases} 
	x\equiv a_1(mod\ m_1)\\
	x\equiv a_2(mod\ m_2)\\
  \end{cases}可化为 x\equiv x_0(mod\ lcm(m_1,m_2))\\
  我们将新生成的等式替代原来的两式，故大小为k的问题转换为大小为k-1的问题,使用k-1次即可求解完毕
$$

```c++
int a[N], m[N];
int exgcd(int a, int b, int &x, int &y) {
    //需要保证传入的参数为正数
    if (b == 0) return x = 1, y = 0, a;
    int gcd = exgcd(b, a % b, y, x);
    y -= a / b * x;
    return gcd;
}

pair<int,int> tongyu(int n) {//返回总体的a和总体的模数
    int prea = ((a[1] % m[1])+m[1])%m[1], prem = m[1];
    for (int i = 2; i <= n; i++) {
        int y1, y2;
        a[i] = ((a[i]%m[i])+m[i])%m[i];
        int gc = exgcd(prem, m[i], y1, y2);
        if ((a[i] - prea) % gc) return {-1, -1};
        y1 *= (a[i] - prea) / gc;//这一步很容易因为longlong爆,数据过大需要替换为龟速乘
        int ms = m[i] / gc;
        y1 = (y1 % ms + ms) % ms;
        prea = y1 * prem + prea;
        prem = prem / gc * m[i];
        prea = (prea % prem + prem) % prem;
    }
    return {prea, prem};
}
```

#### 中国剩余定理

$$
解同余方程组时,若m_1,m_2,m_3....m_k两两互质,此时我们可以运用中国剩余定理,求出其构造解\\
设  m_1, m_2, \ldots, m_k  是两两互质的  k  个正整数，

则方程组  

\begin{cases} 
x \equiv a_1 \pmod{m_1} \\ 
x \equiv a_2 \pmod{m_2} \\ 
\vdots \\ 
x \equiv a_k \pmod{m_k} 
\end{cases}的解为  x \equiv \sum_{i=1}^k M_i^{-1} M_i a_i \pmod{M}\\
其中  M = m_1 m_2 \cdots m_k ,  M_i = M/m_i ,  M_i^{-1} M_i \equiv 1 \pmod{m_i} 。\\
详细来说M为所有模数的乘积，M_i为除去i号模数之外,其余模数的乘积,M_i^{-1}为M_i关于m_i的逆元\\
我们对于\sum_{i=1}^k M_i^{-1} M_i a_i 取m_s模数时\\第s项之外的M中都包含m_s,第s项,又因为M_s^{-1}是M_s关于m_s的逆元，M_s^{-1}把M_i抵消了,剩下a_s.满足x \equiv a_s \pmod{m_s}
$$

```c++
int a[N], m[N];
int exgcd(int a, int b, int &x, int &y) {
    //需要保证传入的参数为正数
    if (b == 0) return x = 1, y = 0, a;
    int gcd = exgcd(b, a % b, y, x);
    y -= a / b * x;
    return gcd;
}

int inv(int a,int m) {
    //求a在%m情况下的逆元,因为m不一定是质数,中国剩余定理只保证了互质,所以不可以用费马小定理用快速幂来求逆元
    int x, y;
    int gc = exgcd(a, m, x, y); //ax+my=1,此时x就是逆元
    return ((x % m) + m) % m;
}

pair<int,int> tongyu(int n) {
    int M = 1;
    int A = 0;
    for (int i = 1; i <= n; i++) {
        M = M * m[i];
    }
    for (int i = 1; i <= n; i++) {
        A = (A + a[i] * (M / m[i]) * inv((M / m[i]), m[i])) % M;
    }
    return {A, M};
}
```

### 排列与组合

#### 基本公式：

$$
A_{n}^{m}=A(n, m) = \frac{n!}{(n-m)!}\\
C_{n}^{m}=C(n, m) = \binom{n}{m} = \frac{n!}{m!(n-m)!}\\
C_{n}^{m}=C_{n-1}^{m-1}+C_{n-1}^{m}=\frac{n}{m}C_{n-1}^{m-1}=\frac{n-m+1}{m}C_{n}^{m-1}\\
对于取模类型问题,如果模数和分母不互质,则无法使用费马小定理\&欧拉定理求逆元\\
此时我们就不能使用定义式来求取模后的结果,此时应当使用递推式
$$

动态规划递推求C

```c++
int C[N][N];
void getc() {
    C[0][0] = 1;
    for (int i = 1; i < N; i++) {
        C[i][0] = 1;
        for (int j = 1; j < N; j++) {
            C[i][j] = (C[i - 1][j - 1] + C[i - 1][j]);//数字过大时，根据题目要求加上取模
        }
    }
}
```

逆元求C(用到了逆元，MOD数字最好为质数)

```c++
int ksm(int di,int mi) {
    int ans = 1;
    while (mi) {
        if (mi & 1) {
            ans = (ans * di) % MOD;
        }
        mi >>= 1;
        di = (di * di) % MOD;
    }
    return ans;
}

int jc[N]; //用来记录阶乘的结果,需要提前计算出来
int C(int a,int b) {
    //返回在a中取b个的结果
    return (((jc[a] * ksm(jc[b], MOD - 2)) % MOD) * ksm(jc[a - b], MOD - 2)) % MOD;
}

//下面预处理的时候使用
void yuchuli() {
    //预处理函数,在计算之前,直接调用即可
    jc[0] = 1;
    for (int i = 1; i < N; i++) {
        jc[i] = (jc[i - 1] * i) % MOD;
    }
}
```

#### 卢卡斯定理(求逆元不一定存在情况下的组合数)

$$
我们可以使用逆元和递推公式C_{n}^{m}=\frac{n!}{m!(n-m)!}来求C_{n}^{m}(mod\ p)情况下的组合数\\
$$

$$
当p为素数时,若分母大于p,则不一定保证互质,此时使用逆元则会出现问题\\
我们可以使用卢卡斯定理:C_{n}^{m}\equiv C_{n\%p}^{m\%p}\times C_{\lfloor \frac{n}{p} \rfloor}^{\lfloor \frac{m}{p} \rfloor},其中 C_{n\%p}^{m\%p}使用逆元求解,C_{\lfloor \frac{n}{p} \rfloor}^{\lfloor \frac{m}{p} \rfloor}使用递归求解
$$

```c++
int ksm(int di,int mi) {
    int ans = 1;
    while (mi) {
        if (mi & 1) {
            ans = (ans * di) % MOD;
        }
        mi >>= 1;
        di = (di * di) % MOD;
    }
    return ans;
}

int jc[N]; //用来记录阶乘的结果,需要提前计算出来
int C(int a,int b) {
    //返回在a中取b个的结果
    return (((jc[a] * ksm(jc[b], MOD - 2)) % MOD) * ksm(jc[a - b], MOD - 2)) % MOD;
}

int lukasi(int a,int b) {
    //返回a中取b个使用卢卡斯定理的结果
    if (b == 0) return 1;
    return (C(a % MOD, b % MOD) * lukasi(a / MOD, b / MOD)) % MOD;
}

//下面预处理的时候使用
void yuchuli() {
    //预处理函数,在计算之前,直接调用即可
    jc[0] = 1;
    for (int i = 1; i < N; i++) {
        jc[i] = (jc[i - 1] * i) % MOD;
    }
}
```

##### 拓展卢卡斯定理

$$
待补充.用来解决p不为素数情况下的求组合数
$$



#### 环排列问题

$$
对于有n个元素的普通全排列,方案数目为n!种\\
对于环上去重全排列方案数,我们可以看成选一个元素固定为第一个,此时剩下n-1个元素,故方案为(n-1)!种\\
我们可能会运用到隔板法使得元素变少,设用了i次捆绑法，此时剩下n-i个元素,故方案为(n-i-1)!种\\
使用到隔板法时,应当逐项计算,不能统一计算再除以总数量长度,这样计算会出问题
$$

#### 重复性质元素排列数(多重组合数)

$$
对于一个长度为n的可重集合,求其内部元素长度为n的排列时，我们看成n个位置,依次往里面放数字,相同数字同一次放。\\
对于k_1个a_1,k_2个a_2,k_3个a_3...k_n个a_n情况时。有\prod_{i=1}^{n}C_{n-{\sum_{j=1}^{i-1}k_j}}^{k_i}种可能\\
即C_{n}^{k_1}*C_{n-k_1}^{k_2}*C_{n-k_1-k_2}^{k_3}..*C_{k_n}^{k_n}\\
化简得:\frac{n!}{\prod_{i=1}^{n}{k_i!}}
$$

#### 隔板法(解下线固定不定方程组合数)

$$
隔板法用于解决分配类型问题,其题目类似于把n分成k份,第i份最少a_i个,问方案数
其题目具体如下:\\
对于不定方程:x_1+x_2+...+x_k=n,其中x_i>=a_i,a_i>=0\\\\
当特殊情况:所有a=1时,题目类似于在n个物体中插入k-1个板子,每两个物体之间最多插入一个板\\
此时一共n-1个可能可以插入板子的地方，所以答案为C_{n-1}^{k-1}\\\\
当一般情况:对于a!=1时,x_i>=a_i,即x_i-a_i>=0,x_i-a_i+1>=1\\
我们令y_i=x_i-a_i+1,此时题目转化为了求y_i>=1的方案数\\
此时不定方程为:(y_1+a_1-1)+(y_2+a_2-1)+....+(y_k+a_k-1)=n\\
化简为:y_1+y_2+...+y_k=n- \sum_{i=1}^{k} a_i+k\\
此时答案为C_{n+k-1- \sum_{i=1}^{k} a_i}^{k-1}\\\\
若要求x_1+x_2+...+x_k<=n,其中x_i>=a_i,a>=0的方案书时,我们可以在限制条件内添加x_{k+1},x_{k+1}>=0\\
此时转换为求x_1+x_2+...+x_k+x_{k+1}=n的方案数
$$

#### 卡特兰数

$$
我们设卡特兰数第n项为KTL(n)\\
通项公式为:KTL(n)=\begin{cases} 
C_{2n}^n-C_{2n}^{n-1}\\
\frac{1}{n+1}C_{2n}^{n}\\
\frac{4n-2}{n+1}KTL(n-1)&(其中KTL(0)=1)\\
\end{cases}
$$

### 容斥定理

#### 全容斥原理

$$
我们可以使用容斥定理,将求并集转化为求交集\\
  \bigcup_{i=1}^k A_i  = \sum_{j=1}^k (-1)^{j-1} \sum_{1 \leq w_1 < w_2 < \dots < w_j \leq k}  A_{w_1} \cap A_{w_2} \cap \dots \cap A_{w_j}  \\
  \bigcup_{i=1}^k A_i表示为对于A_1,A_2,A_3...A_k组成的就条件中,至少满足一个条件时的方案数\\
  举例来说，如果我们要求A_1,A_2,A_3之间的并集，可使用公式:\\
S=S_{A_1}+S_{A_2}+S_{A_3}-(S_{A_1A_2}+S_{A_1A_3}+S_{A_2A_3})+S_{A_1A_2A_3}\\
设全集为S，则S-\bigcup_{i=1}^k A_i=\sum_{j=0}^k (-1)^{j} \sum_{1 \leq w_1 < w_2 < \dots < w_j \leq k}  A_{w_1} \cap A_{w_2} \cap \dots \cap A_{w_j}\\
表示为对于所有A_i都不满足时的方案数
$$

#### 解上下限固定不定方程组合数

$$
我们使用隔板法,可以解决下限固定的不定方程，可如果上限下限都固定的不定方程,则需要我们进一步使用容斥来解决\\
例如:对于不定方程:x_1+x_2+...+x_k=n,其中x_i \in \left[l_i,r_i\right](l,r>=0)。求其方案数\\
\\
我们先忽略r_i的限制条件,我们对于“{x_1+x_2+...+x_k=n,其中x_i>=l_i}”可以通过令y_i=x_i-l_i+1,使用隔板法来进行求解\\
我们得到所有{x_i>=l_i}条件都满足的方案数为S\\
我们令{x_i>=r_i+1}的方案数为A_i,故对于A_1,A_2....A_k,至少有一个A_i满足的方案为\bigcup_{i=1}^k A_i\\
对于x_i \in \left[l_i,r_i\right]问题,即S-\bigcup_{i=1}^k A_i为题目要求的方案数\\
S-\bigcup_{i=1}^k A_i=S-(\sum_{j=1}^k (-1)^{j-1} \sum_{1 \leq w_1 < w_2 < \dots < w_j \leq k}  A_{w_1} \cap A_{w_2} \cap \dots \cap A_{w_j}  )\\
对于求A_{w_1} \cap A_{w_2} \cap \dots \cap A_{w_j}即求\\
对于不定方程x_1+x_2+...+x_k=n\\满足x_{w_1}>=r_{w_1}+1,x_{w_2}>=r_{w_2}+1...x_{w_j}>=r_{w_j}+1且i\notin\{w_1,w_2...w_j\}时,x_i>=l_i的不定方程的根的数量\\
$$

```c++
const int MOD = 998244353;
int jc[N]; // 阶乘数组
int l[N + 1], r[N + 1];//每一项不定方程的限制,l存储下界,r存储上界
int ksm(int di, int mi) {
    int ans = 1;
    while (mi) {
        if (mi & 1) {
            ans = (ans * di) % MOD;
        }
        mi >>= 1;
        di = (di * di) % MOD;
    }
    return ans;
}
int C(int a, int b) {
    if (a < 0 || b < 0 || a < b) return 0;
    return ((jc[a] * ksm(jc[b], MOD - 2)) % MOD * ksm(jc[a - b], MOD - 2)) % MOD;
}
int budingfangcheng(int k, int n) {
    //不定方程有k项,加起来总和为n,返回根的个数
    int suml=0,sumr = 0;
    for (int i = 1; i <= k; i++) {
        suml += l[i];
        sumr += r[i];
    }
    if (n < suml || n > sumr) return 0;
    int ans = 0;
    for (int s = 0; s < (1 << k); s++) {
        //遍历每一种情况
        int cnt = 0;
        int add = 0;
        for (int i = 0; i < k; i++) {
            if (s & (1 << i)) {
                //判断此时枚举的哪种情况
                cnt++;
                add += (r[i + 1] - l[i + 1] + 1);
            }
        }
        if (n + k - 1 - (suml + add) < 0) continue;
        if (cnt % 2 == 0) {
            //根据奇偶性判断其符号
            ans = (ans + C(n + k - 1 - (suml + add), k - 1)) % MOD;
        } else {
            ans = (ans - C(n + k - 1 - (suml + add), k - 1) + MOD) % MOD;
        }
    }
    return ans;
}
//下面部分放入开头，提前预处理
void yuchuli() {
    //预处理函数,在计算之前,直接调用即可
    jc[0] = 1;
    for (int i = 1; i < N; i++) {
        jc[i] = (jc[i - 1] * i) % MOD;
    }
}
```

#### 部分容斥原理

$$
对于条件A_1,A_2\ldots A_a,和B_1,B_2\ldots B_b,要求满足A_1,A_2\ldots A_a,但不满足B_1,B_2\ldots B_b时的方案数时,可采用容斥原理的符号形式\\

我们定义:容斥原理的符号形式\\
\begin{cases} 
设  S  是一个有限集,A_1, A_2, \ldots, A_n是n种条件\\
记  N(A_i) 为  S  中满足A_i条件的元素的数量。特殊的，记  N(1) =S。\\
记  N(1 - A_i)  为  S  中不满足A_i条件的元素的数量。\\
 N(A_{i_1}A_{i_2}\ldots A_{i_k})表示对A_{i_1}, A_{i_2}, \ldots, A_{i_k}取并集,代表S中同时满足  A_{i_1}, A_{i_2}, \ldots, A_{i_k}条件的元素的数量。\\
 N(A \pm B) = N(A) \pm N(B)。\\
  \end{cases}\\

对于所有A_i都不满足时的方案数S-\bigcup_{i=1}^n A_i可表示为:\\
S-\bigcup_{i=1}^n A_i=N((1 - A_1)(1 - A_2)\cdots(1 - A_n)) = \sum_{i=0}^{n} (-1)^i \sum_{1 \leq j_1 < j_2 < \cdots < j_i \leq n} N(A_{j_1}A_{j_2}\ldots A_{j_i})\\
举例来说,对于N((1 - A_1)(1 - A_2))=N(1-A_1-A_2+A_1A_2)=N(1)-(N(A_1)+N(A_2))+N(A_1A_2)\\\\
故满足A_1,A_2\ldots A_a,但不满足B_1,B_2\ldots B_b时的方案数可表示为:\\
N(A_1 A_2 \cdots A_a (1 - B_1)(1 - B_2) \cdots (1 - B_b)) = \sum_{i=0}^{b} (-1)^i \sum_{1 \leq k_1 < k_2 < \cdots < k_i \leq b} N(A_1 A_2 \cdots A_a B_{k_1} B_{k_2} \cdots B_{k_i})\\
举例来说,对于N(A_1A_2(1 - B_1)(1 - B_2))=N(A_1A_2-A_1A_2B_1-A_1A_2B_2+A_1A_2B_1B_2)\\=N(A_1A_2)-(N(A_1A_2B_1)+N(A_1A_2B_2))+N(A_1A_2B_1B_2)\\\\
$$

#### 第二类斯特林数

$$
把n个球放入到k个互不区分盒子中,且每个盒子至少有一个球的方案数称为:第二类斯特林数\\
我们设函数STL(n,k)为把n个球放入到k个互不区分盒子中,且每个盒子至少有一个球的方案数\\
则递推式为:\\
STL(n,k)=STL(n-1,k-1)+k*STL(n-1,k)\\
STL(n-1,k-1)代表新开一个盒子,k*STL(n-1,k)代表不新开一个盒子,在之前加入过的k个盒子内选一个加入\\\\
我们可以利用容斥原理求解:我们先赋予每个盒子一个编号,我们设A_i条件为i号盒子中没有球,S为全集\\
则\bigcup_{i=1}^k A_i代表至少有一个盒子中没有球,故S-\bigcup_{i=1}^k A_i代表盒子内都有球\\
S-\bigcup_{i=1}^k A_i=N((1 - A_1)(1 - A_2)\cdots(1 - A_k))=\sum_{i=0}^{k} (-1)^i \sum_{1 \leq j_1 < j_2 < \cdots < j_i \leq k} N(A_{j_1}A_{j_2}\ldots A_{j_i})\\
又因为我们赋予每个盒子一个编号,而实际上盒子之间是没有去别的,所以我们需要除去盒子排列的方案数\\
故方案数为:\frac{\sum_{i=0}^{k} (-1)^i \sum_{1 \leq j_1 < j_2 < \cdots < j_i \leq k} N(A_{j_1}A_{j_2}\ldots A_{j_i})}{k!}\\\\
第二类斯特林数有一个重要结论
n^m=\sum_{k=0}^{n}C_{n}^{k}\times STL(m,k)\times k!\\
n^m可以看成m个物体放入n个盒子的方案数,C_{n}^{k}在n个盒子中选k个盒子,STL(m,k)让这些盒子至少有一个物品,k!对盒子排列
$$

```c++
int jc[N]; // 阶乘数组
int ksm(int di, int mi) {
    int ans = 1;
    while (mi) {
        if (mi & 1) {
            ans = (ans * di) % MOD;
        }
        mi >>= 1;
        di = (di * di) % MOD;
    }
    return ans;
}
int C(int a, int b) {
    return (((jc[a] * ksm(jc[b], MOD - 2)) % MOD) * ksm(jc[a - b], MOD - 2)) % MOD;
}
int STL(int n, int k) {//输入物品数,盒子数
    if (k > n) return 0;
    if (k == 0) return n == 0 ? 1 : 0;
    int sum = 0;
    for (int i = 0; i <= k; i++) {
        int term = C(k, i) * ksm(k - i, n) % MOD;
        if (i & 1) {
            sum = ((sum - term) % MOD + MOD) % MOD;
        } else {
            sum = (sum + term) % MOD;
        }
    }
    sum = sum * ksm(jc[k], MOD - 2) % MOD;
    return sum;
}
//下面是预处理
void yuchuli() {
    //预处理函数,在计算之前,直接调用即可
    jc[0] = 1;
    for (int i = 1; i < N; i++) {
        jc[i] = (jc[i - 1] * i) % MOD;
    }
}
```

### 求和公式处理：

#### 数论分块

$$
对于形如\sum_{i=1}^n f(i)\lfloor\frac{n}{i}\rfloor类型的问题，我们可以使用整数分块,使得复杂度在\sqrt{n}之内\\
我们发现对于\lfloor\frac{n}{i}\rfloor,随着i的增大,其数字之间的变化会越来越小\\
我们对\lfloor\frac{n}{i}\rfloor的值进行分块,值相同在同一个块中,此时块的总数量小于2\sqrt{n}\\
且i所在的块的右侧端点为\lfloor\frac{n}{\lfloor\frac{n}{i}\rfloor}\rfloor,实现上来说为:n/(n/i)\\
我们可以对f(i)跑一次前缀和,运用前缀和来进行计算\\
\\
\sum_{i=1}^n f(i)\lfloor\frac{a_1}{i}\rfloor\lfloor\frac{a_2}{i}\rfloor...\lfloor\frac{a_k}{i}\rfloor时,我们r的取值为i所在的每个分块的右端点的最左侧点\\
即r=min(\lfloor\frac{a_1}{\lfloor\frac{a_1}{i}\rfloor}\rfloor,\lfloor\frac{a_2}{\lfloor\frac{a_2}{i}\rfloor}\rfloor...\lfloor\frac{a_k}{\lfloor\frac{k}{a_i}\rfloor}\rfloor);
$$

```c++
for (int l=1,r;l<=n;l=r+1) {
        r=a[1]/(a[1]/l);
        for (int i=2;i<=k;i++) {
            r=min(r,a[i]/(a[i]/l));
        }
        //现在l~r的块已经找出来了,在下面使用前缀和计算即可
}
```

#### 变换规律

$$
对于和式计算满足以下规律\\
\begin{cases}
\sum_{k \in K} c a_k = c \sum_{k \in K} a_k &分配律\\
\sum_{k \in K} (a_k + b_k) = \sum_{k \in K} a_k + \sum_{k \in K} b_k&结合律\\
\sum_{k \in K} a_k = \sum_{p(k) \in K} a_{p(k)}&交换律\\
\end{cases}\\
替换条件式:\\
\sum_{i=1}^n \sum_{j=1}^m \sum_{d \mid \gcd(i,j)} d = \sum_{i=1}^n \sum_{j=1}^m 
\sum_{d=1}^{\min(n,m)} [d \mid i][d \mid j] d\\
替换指标变量:\\
\sum_{i=1}^n \sum_{j=1}^m [\gcd(i,j) = k] = \sum_{ki=1}^n \sum_{kj=1}^m [\gcd(ki, kj) = k]=\sum_{ki=1}^n \sum_{kj=1}^m [\gcd(i, j) = 1]=\sum_{i=1}^{\lfloor\frac{n}{k}\rfloor} \sum_{j=1}^{\lfloor\frac{m}{k}\rfloor} [\gcd(i, j) = 1]\\
交换求和次序:\\
\sum_{i=1}^n \sum_{j=1}^m A(i)B(j) = \sum_{j=1}^m \sum_{i=1}^n A(i)B(j)\\
分离变量:\\
\sum_{i=1}^n \sum_{j=1}^m A(i)B(j) = \sum_{i=1}^n A(i)   \sum_{j=1}^m B(j)= \left( \sum_{i=1}^n A(i) \right) \left( \sum_{j=1}^m B(j) \right)
$$



#### 替换公式

$$
合式变换的重要公式:\\
\begin{cases}
n=\sum_{d|n}\varphi(d)&(\varphi()代表欧拉函数)\\
\epsilon(n)=[n=1]=\sum_{d|n}\mu(d)&(\mu()代表莫比乌斯函数)\\
\sum_{d|n}\mu(d)\frac{n}{d}=\varphi(n)&(将莫比乌斯函数\mu转换成欧拉函数\varphi)\\
d(ij)=\sum_{x|i}\sum_{y|j}[\gcd(x,y)=1]&(将因数函数转换成单位函数)\\
\end{cases}
$$



### 积性函数

#### 积性函数概念

$$
如果函数  F : \mathbb{N} \to \mathbb{R},满足对于任意一对互质的正整数p,q，都有F(pq) = F(p)F(q),则称F为积性函数。\\
我们可以把F(p)和F(q)函数拆解成两个表达式,两个表达式乘积满足与F(pq)的表达式相等\\
积性函数举例:\\
\begin{cases} 
id(n)& \text{(函数本身)}\\
\epsilon(n)=[n=1]&(单位函数,是1则返回1,不是1则返回0)\\
\varphi(n)=\sum_{i=1}^{n}[\gcd(i,n)=1]&(1 \ldots n中与n互质的数的数量)\\
d(n)&(n的正因子的数量)\\
\end{cases}\\


如果 f(n), g(n)是积性函数，则h(n) = f(n)g(n)也是积性函数。\\
如果F()为积性函数,设n=p_{1}^{a_1}p_{2}^{a_2}...p_{k}^{a_k}\\
F(n)=F(p_{1}^{a_1})F(p_{2}^{a_2})...F(p_{k}^{a_k})\\
$$

#### 莫比乌斯函数

$$
\\莫比乌斯函数\mu(n) 定义如下：
\\
\mu(n) = 
\begin{cases} 
1 & \text{如果 } n = 1, \\
(-1)^k & \text{如果 } n \text{ 是 } k \text{ 个不同质数的乘积}, \\
0 & \text{如果 } n \text{ 被一个质数的平方整除}.
\end{cases}\\
莫比乌斯函数是积性函数\\\\
重要性质:\\
[n=1]=\sum_{d|n}\mu(d)\\
\sum_{d|n}\mu(d)\frac{n}{d}=\varphi(n)
$$

**欧拉筛求莫比乌斯函数**

```c++
int prim[N], tot;
int bj[N]; //用来记录每个数的最小质因子
int mu[N]; //莫比乌斯函数

void getprim() {
    mu[1] = 1;
    for (int i = 2; i < N; i++) {
        if (!bj[i]) {
            prim[++tot] = i;
            bj[i] = i; //每个数字除以这个数字
            mu[i] = -1;
        }
        for (int j = 1; j <= tot && prim[j] * i < N; j++) {
            bj[prim[j] * i] = prim[j];
            if (i % prim[j] == 0) {
                mu[prim[j] * i] = 0;
                break;
            }
            mu[prim[j] * i] = -mu[i];
        }
    }
}
```

#### 因子莫比乌斯反演

$$
我们已知两个函数之间某一单向过程f,求其逆过程f^{-1}的过程我们便称之为反演\\
莫比乌斯反演:\\
设  f: \mathbb{N} \to \mathbb{R},\ g: \mathbb{N} \to \mathbb{R}  是两个函数，则\\
f(n) = \sum_{d|n} g(d) \quad \Leftrightarrow \quad g(n) = \sum_{d|n} \mu\left(\frac{n}{d}\right) f(d)
\\\\
运用容斥定理证明如下:\\
我们现在已知f(n) = \sum_{d|n} g(d)，我们分解n得到n=p_1^{a_1}p_2^{a_2}...p_k^{a_k},带入原式并且展开得\\
f(p_1^{a_1}p_2^{a_2}...p_k^{a_k}) = g(p_1^{a_1}p_2^{a_2}...p_k^{a_k})+g(p_1^{a_{1}-1}p_2^{a_2}...p_k^{a_k})+g(p_1^{a_1}p_2^{a_{2}-1}...p_k^{a_k})+.....\\
我们现在要求g(p_1^{a_1}p_2^{a_2}...p_k^{a_k}),可以用利用容斥原理求解:\\
设\begin{cases} 
全集方案数为S,故S=f(p_1^{a_1}p_2^{a_2}...p_k^{a_k})\\
满足条件:n的第i位素因子p_i的幂最大为a_{i}-1的方案数为A_i,故A_i=f(p_1^{a_1}...p_i^{a_i-1}...p_k^{a_k})\\
\end{cases}\\
故\bigcup_{i=1}^k A_i为满足条件为至少有一个素因子p_i,其幂不超过a_i-1的方案数\\
故S-\bigcup_{i=1}^k A_i为所有质因子p_i的幂=a_i的方案数\\
g(n)=S-\bigcup_{i=1}^k A_i=\sum_{i=0}^{k}\left(-1\right)^i\sum_{j_1+j_2+...+j_k=i且j_w\in\{0,1\}}f(p_1^{a_1-j_1}p_2^{a_2-j_2}...p_k^{a_k-j_k})\\
我们设d=p_1^{a_1-j_1}p_2^{a_2-j_2}...p_k^{a_k-j_k},则p_1^{j_1}p_2^{j_2}...p_k^{j_k}=\frac{n}{d}\\
(-1)^i取决于\frac{n}{d}中质因子的个数,我们令函数\mu(\frac{n}{d})=\left(-1\right)^i
\\用莫比乌斯函数来代替容斥中的\left(-1\right)^i,并且当\frac{n}{d}有重复质因子时令\mu=0,故可以消除拥有重复质因子的因数\\
g(n)=\sum_{i=0}^{k}\left(-1\right)^i\sum_{j_1+j_2+...+j_k=i且j_w\in\{0,1\}}f(p_1^{a_1-j_1}p_2^{a_2-j_2}...p_k^{a_k-j_k})=\sum_{d|n}\mu\left(\frac{n}{d}\right)f(d)
$$

#### 环计数问题

$$
用a\in[1,r]之内的数字填满一个长度为n的环,数字可重,求环不重的方案数(环之间不能通过旋转使得其相等)\\
我们设长度为x的内部不包含循环节的方案数为f(x)\\
则答案为\sum_{i=1}^nf(i),其中f(x)=\frac{1}{x}\sum_{d|x}\mu(\frac{x}{d})r^d

\\证明如下:\\
对于用a\in[1,r]之内的数字填满一个长度为n的环,其总方案数为r^n\\
我们发现,如果对环去重,对于一个重复方案,必定可以移动用循环节长度使其重合,而且这一个循环节为总长度n的因数\\
我们找到总方案数和f(x)之间的关系为r^n=\sum_{d|n}d\times f(d),其中d中代表一个循环节能产生的贡献数\\
我们使用莫比乌斯反演可得:n\times f(n)=\sum_{d|n}\mu(\frac{n}{d})r^d,故f(n)=\frac{1}{n}\sum_{d|n}\mu(\frac{n}{d})r^d\\
\sum_{i=1}^nf(x)=\sum_{i=1}^n \frac{1}{i}\sum_{d|i}\mu(\frac{i}{d})r^d,我们发现对于一个d,由多个i满足情况,我们重写求和得:\\
\sum_{i=1}^n \frac{1}{i}\sum_{d|i}\mu(\frac{i}{d})r^d=\sum_{d=1}^{n}r^d\sum_{k=1}^{\lfloor \frac{n}{d}\rfloor}\frac{1}{dk}\mu(k),其中d\times k表示重写之前的i\\
化简得:\sum_{i=1}^nf(i)=\sum_{d=1}^{n}\frac{r^d}{d}\sum_{k=1}^{\lfloor \frac{n}{d}\rfloor}\frac{\mu(k)}{k}
$$

```c++
int prim[N], tot;
int bj[N]; //用来记录每个数的最小质因子
int mu[N]; //莫比乌斯函数
int inv[N];
int premu[N]; //用来记录mu(k)/k的前缀和
void getprim() {
    mu[1] = 1;
    for (int i = 2; i < N; i++) {
        if (!bj[i]) {
            prim[++tot] = i;
            bj[i] = i; //每个数字除以这个数字
            mu[i] = -1;
        }
        for (int j = 1; j <= tot && prim[j] * i < N; j++) {
            bj[prim[j] * i] = prim[j];
            if (i % prim[j] == 0) {
                mu[prim[j] * i] = 0;
                break;
            }
            mu[prim[j] * i] = -mu[i];
        }
    }
}

void getinv() {
    inv[1] = 1;
    for (int i = 2; i < N; i++) {
        inv[i] = ((-1 * inv[MOD % i] * (MOD / i)) % MOD + MOD) % MOD;
    } //注意(MOD / i)用了括号使得向下取整,不要忘记加了
}

void yuchuli() {
    //预处理函数,在计算之前,直接调用即可
    getprim();
    getinv();
    for (int i = 1; i < N; i++) {
        premu[i] = ((mu[i] * inv[i]) % MOD + MOD) % MOD;
        premu[i] = (premu[i] + premu[i - 1]) % MOD;
    }
}

int huanjishu(int n,int r) {
    //返回n个位置,放k种元素的环上去重方案数
    int ans = 0;
    int dqr = 1;
    for (int i = 1; i <= n; i++) {
        dqr = (dqr * r) % MOD;
        ans = (ans + ((((dqr * inv[i]) % MOD) * premu[n / i]) % MOD)) % MOD;
    }
    return ans;
}
```

#### 倍数莫比乌斯反演

$$
设f:\mathbb{N}\to\mathbb{R},g:\mathbb{N}\to\mathbb{R}是两个函数，且存在正整数N,对于所有n > N,f(n) = g(n) = 0则  \\
f(n) = \sum_{n|m} g(m) \Leftrightarrow g(n) = \sum_{n|m} \mu\left(\frac{m}{n}\right) f(m)\\
\\
证明方法同理,运用容斥定理证明如下:\\
我们现在已知f(n) = \sum_{n|m} g(m)，我们分解n得到n=p_1^{a_1}p_2^{a_2}...p_k^{a_k},带入原式并且展开得\\
f(p_1^{a_1}p_2^{a_2}...p_k^{a_k}) = g(p_1^{a_1}p_2^{a_2}...p_k^{a_k})+g(p_1^{a_{1}+1}p_2^{a_2}...p_k^{a_k})+g(p_1^{a_1}p_2^{a_{2}+1}...p_k^{a_k})+.....\\
我们现在要求g(p_1^{a_1}p_2^{a_2}...p_k^{a_k}),可以用利用容斥原理求解:\\
设\begin{cases} 
全集方案数为S,故S=f(p_1^{a_1}p_2^{a_2}...p_k^{a_k})\\
满足条件:n的第i位素因子p_i的幂最少为a_{i}+1的方案数为A_i,故A_i=f(p_1^{a_1}...p_i^{a_i+1}...p_k^{a_k})\\
\end{cases}\\
故\bigcup_{i=1}^k A_i为满足条件为至少有一个素因子p_i,其幂至少为a_i+1的方案数\\
故S-\bigcup_{i=1}^k A_i为所有质因子p_i的幂=a_i的方案数\\
g(n)=S-\bigcup_{i=1}^k A_i=\sum_{i=0}^{k}\left(-1\right)^i\sum_{j_1+j_2+...+j_k=i且j_w\in\{0,1\}}f(p_1^{a_1+j_1}p_2^{a_2+j_2}...p_k^{a_k+j_k})\\
我们设m=p_1^{a_1+j_1}p_2^{a_2+j_2}...p_k^{a_k+j_k},则p_1^{j_1}p_2^{j_2}...p_k^{j_k}=\frac{m}{n}\\
(-1)^i取决于\frac{m}{n}中质因子的个数,我们令函数\mu(\frac{m}{n})=\left(-1\right)^i
\\用莫比乌斯函数来代替容斥中的\left(-1\right)^i,并且当\frac{m}{n}有重复质因子时令\mu=0,故可以消除拥有重复质因子的因数\\
g(n)=\sum_{i=0}^{k}\left(-1\right)^i\sum_{j_1+j_2+...+j_k=i且j_w\in\{0,1\}}f(p_1^{a_1+j_1}p_2^{a_2+j_2}...p_k^{a_k+j_k})=\sum_{n|m}\mu\left(\frac{m}{n}\right)f(m)
$$

### 矩阵和高斯消元

#### 矩阵计算

$$
三角函数的递推关系可以写成矩阵形式:\\
\sin(A \pm B) = \sin A \cos B \pm \cos A \sin B\\
\cos(A \pm B) = \cos A \cos B \mp \sin A \sin B\\
我们已知\sin(A),\cos(A)与B可以得出:\\
[\sin(A+B),\cos(A+B)]=[\sin(A),\cos(A)]\times 
\begin{bmatrix}
\cos B & -\sin B\\
\sin B & \cos B
\end{bmatrix}\\
为了递推的方便,可以讲初始矩阵设置成:\begin{bmatrix}
\cos A  & -\sin A\\
\sin A  & \cos A
\end{bmatrix}\\
累加递推关系:
\begin{bmatrix}
\cos(A+B) & -\sin(A+B)\\
\sin(A+B) & \cos(A+B)
\end{bmatrix}=
\begin{bmatrix}
\cos A & -\sin A\\
\sin A & \cos A
\end{bmatrix}\times \begin{bmatrix}
\cos B & -\sin B\\
\sin B & \cos B
\end{bmatrix}\\
累减递推关系：
\begin{bmatrix}
\cos(A-B) & -\sin(A-B)\\
\sin(A-B) & \cos(A-B)
\end{bmatrix}
=
\begin{bmatrix}
\cos A & -\sin A\\
\sin A & \cos A
\end{bmatrix}
\times
\begin{bmatrix}
\cos B & \sin B\\
-\sin B & \cos B
\end{bmatrix}\\
$$



```c++
const int matrixsize = 2; //用来记录矩阵大小
struct matrix {
    int jz[matrixsize][matrixsize];

    matrix() {
        for (int i = 0; i < matrixsize; i++) {
            for (int j = 0; j < matrixsize; j++) {
                jz[i][j] = 0;
            }
        }
    }

    void clear() {
        //清空矩阵
        for (int i = 0; i < matrixsize; i++) {
            for (int j = 0; j < matrixsize; j++) {
                jz[i][j] = 0;
            }
        }
    }

    void init() {
        //初始化为单位矩阵
        clear();
        for (int i = 0; i < matrixsize; i++) {
            jz[i][i] = 1;
        }
    }

    matrix operator +(const matrix &dx) {
        matrix ls;
        for (int i = 0; i < matrixsize; i++) {
            for (int j = 0; j < matrixsize; j++) {
                ls.jz[i][j] = jz[i][j] + dx.jz[i][j];
            }
        }
        return ls;
    }

    matrix operator -(const matrix &dx) {
        matrix ls;
        for (int i = 0; i < matrixsize; i++) {
            for (int j = 0; j < matrixsize; j++) {
                ls.jz[i][j] = jz[i][j] - dx.jz[i][j];
            }
        }
        return ls;
    }

    matrix operator *(const matrix &dx) {
        matrix ls;
        for (int i = 0; i < matrixsize; i++) {
            for (int j = 0; j < matrixsize; j++) {
                for (int k = 0; k < matrixsize; k++) {
                    ls.jz[i][j] = ls.jz[i][j] + jz[i][k] * dx.jz[k][j];
                }
            }
        }
        return ls;
    }

    matrix ksm(int mi) {
        //返回该矩阵的这么多幂次方
        matrix ls, di = *this;
        ls.init();
        while (mi) {
            if (mi & 1) {
                ls = ls * di;
            }
            mi >>= 1;
            di = di * di;
        }
        return ls;
    }
};
```

#### 高斯消元

$$
求解线性方程组x的值,形如
\begin{cases} 
a_{11}x_{1}⊕a_{12}x_{2}⊕a_{13}x_{3}⊕...⊕a_{1m}x_{m}=b_1\\
a_{21}x_{1}⊕a_{22}x_{2}⊕a_{23}x_{3}⊕...⊕a_{2m}x_{m}=b_2\\
....\\
a_{n1}x_{1}⊕a_{n2}x_{2}⊕a_{n3}x_{3}⊕...⊕a_{nm}x_{m}=b_n\\
\end{cases}其中⊕为运算符号\\
对于上述线性方程组,我们可以写成如下形式:\\
\begin{bmatrix}
a_{11}&a_{12}&a_{13}&....&a_{1m}\\
a_{21}&a_{22}&a_{23}&....&a_{2m}\\
...\\
a_{n1}&a_{n2}&a_{n3}&....&a_{nm}\\
\end{bmatrix}\times\begin{bmatrix}
x_1\\
x_2\\
...\\
x_m
\end{bmatrix}=\begin{bmatrix}
b_1\\
b_2\\
...\\
b_n
\end{bmatrix}\\
为了求解如上线性方程组,我们可以将线性方程组写成增广矩阵形式:\\
\begin{bmatrix}
a_{11}&a_{12}&a_{13}&....&a_{1m}&b_1\\
a_{21}&a_{22}&a_{23}&....&a_{2m}&b_2\\
...\\
a_{n1}&a_{n2}&a_{n3}&....&a_{nm}&b_n\\
\end{bmatrix}
\\
对于增广矩阵运算,满足如下性质\begin{cases} 
交换两行结果不变\\
对某一行每个元素同时做某操作结果不变&(操作要满足⊕运算的性质)\\
将某一行⊕运算到另一行结果不变
\end{cases}\\
利用上述性质，我们可以使用高斯消元来求解\\
高斯消元流程:\begin{cases}
0.设置当前秩=0,逐步扩大秩\\
1.枚举主元列x_i,从秩+1行往后找到该列系数不为0的某一行，找不到则直接跳过,找下一列\\
2.将该行与当前秩+1行元素交换\\
3.将该行进行变换,使得其主元行上的系数为1\\
4.将该行⊕运算到其余行，使得除秩+1行外其余行系数为0\\
5.秩增加1,依次进行上述操作,直到矩阵变为行阶梯型矩阵\\
\end{cases}\\
我们可以通过看行阶梯型矩阵的秩,来判断其解的情况:\\
\begin{cases} 
无解:答案矩阵的秩比>原行阶梯型矩阵的秩\\
唯一解:答案矩阵的秩=原行阶梯型矩阵的秩\\
无数解:答案矩阵的秩<原行阶梯型矩阵的秩\\
\end{cases}
$$

#### 线性基

$$
向量空间的基:向量空间中最大的线性无关组被称为向量空间的基\\
即满足a_1x_1+a_2x_2+..a_nx_n!=0(其中a_i为任意实数)的最大x的个数n\\\\
线性基:\and 操作所对应向量空间中的基\\
对于集合S中若干个向量,我们可以构造基,获得基后,我们便可得到能够表示的向量个数以及最大(最小)向量\\
线性基类似于将向量统合成矩阵,进行变换得到行阶梯型矩阵中的秩\\
在行阶梯型矩阵中,我们可以利用秩来表示出其他所有向量,线性基同理\\
在求线性基时,我们可以使用高斯消元的简化版,使其计算更加方便
$$

```c++
const int maxsize = 64; //数字最高位
struct xianxingji {
    int xxj[maxsize]; //xxj[i]表示最高位为第i位的线性基
    xianxingji() {
        for (int i = 0; i < maxsize; i++) {
            xxj[i] = 0;
        }
    }

    void add(int dq) {
        //讲dq这个数字加入到线性基中去
        for (int i = maxsize - 1; i >= 0; i--) {
            if ((dq >> i) & 1) {
                if (xxj[i]) {
                    dq ^= xxj[i];
                } else {
                    xxj[i] = dq;
                    return;
                }
            }
        }
    }

    bool query(int dq) {
        //判断dq是否能用已经存在的线性基表示
        for (int i = maxsize - 1; i >= 0; i--) {
            if ((dq >> i) & 1) {
                if (xxj[i]) {
                    dq ^= xxj[i];
                } else {
                    return 0;
                }
            }
        }
        return 1;
    }
};
```

### 生成函数

#### 普通生成函数(组合数问题)

$$
对于不定方程:x_1+x_2+...+x_k=n,其中x_1,x_2...x_k分别由多项约束性质,我们可以使用普通生成函数来求解\\
对于我们将加法原理转化为幂相乘时指数上的加法以及系数的合并同类项,乘法原理转换为同底幂的加法\\使用生成函数之间的乘法来快速计算组合\\
比如x_1+x_2+...+x_k=n,其中x_1不能超过a,x_2是b的倍数,x_3不能比c小,x_4在d到e之间.....\\
我们可以构造\begin{cases} 
a_1的生成函数(1+x+...+x^a)\\
a_2的生成函数(1+x^b+x^{2b}+....)\\
a_3的生成函数(x^c+x^{c+1}+x^{c+2}....)\\
a_4的生成函数(x^d+x^{d+1}+...+x^{e})\\
.......
\end{cases}\\
通过将上述所有生成函数相乘,再取第n项x^n的系数,即可得到我们想要的组合数\\
\\
例:x_1+x_2+x_3=6,其中x_1不能超过1,x_2是2的倍数,x_3不能比3小\\
则所有生成函数相乘为:(1+x)(1+x^2+x^4+x^6)(x^3+x^4+x^5+x^6)\\
化简后得到多项式:x^3 + 2x^4 + 3x^5 + 4x^6 + 4x^7 + 4x^8 + 4x^9 + 4x^{10} + 3x^{11} + 2x^{12} + x^{13}\\
故x^6的系数4为答案
$$

#### 指数生成函数(排列数问题)

$$
数列\{a_n\}对应的指数生成函数为:\sum_{n=0}^{+\infty}\frac{x^n}{n!}\\
我们可以构造指数生成函数,来解决排列数问题,其计算方法与组合数的总生成函数类似,合并再展开\\
通过将所有指数生成函数相乘,再取第n项\frac{x^n}{n!}这个整体的系数,即可得到我们想要的排列数\\\\
例:1,2,3组成的数字中,要求1必须出现但不能出现超过两次,2出现不能超过两次,3出现偶数次,求所形成的五位数的个数\\
则可得到多项式:(\frac{x}{1!}+\frac{x^{2}}{2!})(1+\frac{x}{1!}+\frac{x^{2}}{2!})(1+\frac{x^{2}}{2!}+\frac{x^{4}}{4!})\\
展开后得:x+\frac{3x^2}{2}+\frac{3x^3}{2}+x^{4}+\frac{13x^{5}}{24}+\frac{3x^{6}}{16}+\frac{x^7}{24}+\frac{x^8}{96}\\
我们取第五项\frac{x^5}{5!}的式子\frac{13x^{5}}{24},可化为\frac{13*5!}{24}*\frac{x^5}{5!}\\
故方案数为:\frac{13*5!}{24}=65种
$$

#### 生成函数化简

$$
遇到生成函数类型的题目时,通常采用如下流程:
\begin{cases} 
1.将无穷级数字使用有限公式代换表示\\
2.将有限公式化简\\
3.拆开有限公式,重构无穷级数\\
4.取对应项系数作为答案
\end{cases}\\
牛顿二项式系数:
\binom{\alpha}{k} = 
\begin{cases}
0 & k < 0 \\
1 & k = 0 \\
\dfrac{\alpha(\alpha-1)\cdots(\alpha-k+1)}{k!} & k > 0
\end{cases}\\
特别的,当\ n, m 皆为正整数且\ m \leq n\ 时：
\binom{n}{m} = C_n^m = \frac{n!}{m!(n-m)!}\\
牛顿二项式定理:(x+y)^a=\sum_{n=0}^{+\infty}\binom{a}{n}x^{n}y^{a-n}\\
对于生成函数，我们常用:
\frac{1}{(1-x)^a}=\sum_{n=0}^{+\infty}\binom{a+n-1}{n}x^n=\sum_{n=0}^{+\infty}C_{a+n-1}^{n}x^n(最后C的替换时满足上条件才成立)\\
如下为常用普通生成函数化简代换公式:\begin{cases} 
1+x^1+x^2+...+x^n\Leftrightarrow \frac{1-x^{n+1}}{1-x}&(等比数列求和公式)\\
1+x^1+x^2+...\Leftrightarrow \frac{1}{1-x}&(牛顿二项式定理)\\
C_{1}^{0}+C_{2}^{1}x^1+C_{3}^{2}x^2+...\Leftrightarrow \frac{1}{(1-x)^2}&(牛顿二项式定理)\\
1+x^2+x^4+x^6+... \Leftrightarrow \frac{1}{1-x^2}\\
1+x^a+x^{2a}+x^{3a}+...\Leftrightarrow \frac{1}{1-x^a}\\
\end{cases}\\
如下为常用指数生成函数化简代换公式:\begin{cases} 
\sum_{n=0}^{+\infty}\frac{x^n}{n!}=\sum=1+\frac{x}{1!}+\frac{x^{2}}{2!}....=e^x\\
\sum_{n=0}^{+\infty}\frac{(cx)^n}{n!}=1+\frac{(cx)}{1!}+\frac{(cx)^{2}}{2!}....=e^{cx}\\
\sum_{n=k}^{+\infty}\binom{n}{k}\frac{x^n}{n!}=\frac{x^k}{k!}e^x\\
\sum_{n=0}^{+\infty}\frac{x^{2n+1}}{(2n+1)!}=\frac{x}{1!}+\frac{x^{3}}{3!}+\frac{x^{5}}{5!}...=\frac{e^x-e^{-x}}{2}\\
\sum_{n=0}^{+\infty}\frac{x^{2n}}{(2n)!}=1+\frac{x^2}{2!}+\frac{x^{4}}{4!}+\frac{x^{6}}{6!}...=\frac{e^x+e^{-x}}{2}\\
\end{cases}
$$



### 全期望公式(逆推)

$$
期望值（如期望步数、期望收益）通常满足"全期望公式"
\\对于一个状态 i，其期望值 E[i] 可以表示为：
\\
E[i] = \sum_{j} P_{ij} \cdot (C_{ij} + E[j])
\\
其中：
 P_{ij} 是从状态 i 转移到状态 j 的概率，\\
 C_{ij} 是转移的即时成本（如步数），\\
 E[j] 是后继状态 j 的期望值。\\
\
为了计算 E[i]，我们需要先知道所有后继状态 j 的期望值 E[j]。\\
逆推从目标状态（其期望值已知，例如终点状态 E[\text{end}] = 0）开始，逐步向后计算前驱状态，这符合依赖关系。
$$

### bsgs算法(北上广深)

$$
BSGS 算法用于求解形如以下的同余方程：\\

a^x \equiv b \pmod{p}\\

其中：
 a，b，p 是已知的正整数\\
 a 和 p 互质（即 \gcd(a, p) = 1）\\
我们需要求解 x\\


BSGS 算法的核心思想是：\\

a^n \equiv b \cdot inv(a^m) \pmod{p}\\

简化为：\\

a^n \equiv b \cdot invA \pmod{p}\\

其中：\\
invA 表示 a^m 在模 p 下的乘法逆元\\
n 和 m 分别代表大步和小步\\


1. 将 x 表示为 x = im - j，其中 m = \lceil\sqrt{p}\rceil\\
2. 原方程转化为 a^{im} \equiv b \cdot a^j \pmod{p}\\
3. 构建一个表存储所有的 (j, b \cdot a^j \bmod p) 对\\
4. 枚举 i 值，计算 a^{im} \bmod p 并在表中查找匹配项\\

这种方法将时间复杂度从 O(p) 降低到 O(\sqrt{p})。\\
$$



```c++
//它用于求解形如 a^x ≡ b (mod p) 的同余方程，其中 a,b,p 是已知的正整数，且 a 和 p 互质
//BSGS:        An = b * invA  (mod p)
int BSGS(int a,int b,int p){
    b=(b%p+p)%p;
    if(b==1||p==1)return 0;
    int n=sqrt(p)+1;
    unordered_map<int,int> mp;
    int invA=getinv(ksm(a,n,p),p);
    for(int i=n;i>=0;i--){
        mp[invA]=i;
        invA=invA*a%p;
    }
    int An=1,A=ksm(a,n,p);
    for(int k=0;k<=p;k+=n){
        if(mp.count(An))return k+mp[An];
        An=An*A%p;
    }
    return -1;
}
```

```c++
//exBSGS:        An = b * invA  (mod p)
//当a,p不互质时使用
int exBSGS(int a,int b,int p){
    b=(b%p+p)%p;
    if(b==1||p==1)return 0;
    
    int k=1;
    int cnt=0;

    while(1){
        int d=__gcd(a,p);
        if(d==1)break;
        if(b%d!=0)return -1;
        cnt++;
        b/=d;
        p/=d;
        k=k*(a/d)%p;
        if(k==b)return cnt;
    }
    
    map<int,int> mp;
    int n=sqrt(1.0*p)+1;
    int res=b;
    for(int i=0;i<=n;i++){
        mp[res]=i;
        res=res*a%p;
    }
    res=ksm(a,n,p);
    int now=k;
    for(int i=1;i<=n;i++){
        now=now*res%p;
        if(mp[now])return i*n-mp[now]+cnt;
    }
    return -1;
}
```

## 计算几何

### 三角函数公式

#### 正弦定理

$$
\frac{a}{\sin A} = \frac{b}{\sin B} = \frac{c}{\sin C} = 2R\\
其中R为外接圆半径
$$
#### 余弦定理

$$
\begin{align*}
a^2 &= b^2 + c^2 - 2bc \cdot \cos A \\
b^2 &= a^2 + c^2 - 2ac \cdot \cos B \\
c^2 &= a^2 + b^2 - 2ab \cdot \cos C
\end{align*}
$$

#### 其余公式

$$
\sin(A \pm B) = \sin A \cos B \pm \cos A \sin B\\
\cos(A \pm B) = \cos A \cos B \mp \sin A \sin B\\
\tan(A \pm B) = \dfrac{\tan A \pm \tan B}{1 \mp \tan A \tan B}\\

\sin(2A) = 2 \sin A \cos A\\
\cos(2A) = \cos^2 A - \sin^2 A\\
\tan(2A) = \dfrac{2 \tan A}{1 - \tan^2 A}\\

\sin\left(\dfrac{A}{2}\right) = \pm \sqrt{\dfrac{1 - \cos A}{2}}\\
\cos\left(\dfrac{A}{2}\right) = \pm \sqrt{\dfrac{1 + \cos A}{2}}\\
\tan\left(\dfrac{A}{2}\right) = \dfrac{\sin A}{1 + \cos A} = \dfrac{1 - \cos A}{\sin A}\\


\sin \alpha \cos \beta = \dfrac{\sin(\alpha + \beta) + \sin(\alpha - \beta)}{2}\\

\cos \alpha \sin \beta = \dfrac{\sin(\alpha + \beta) - \sin(\alpha - \beta)}{2}\\

\cos \alpha \cos \beta = \dfrac{\cos(\alpha + \beta) + \cos(\alpha - \beta)}{2}\\

\sin \alpha \sin \beta = -\dfrac{\cos(\alpha + \beta) - \cos(\alpha - \beta)}{2}\\
$$

###  向量

#### Steinitz引理

$$
设  B \subset \mathbb{R}^2  是一个关于原点中心对称的凸集（即若  v \in B  则  -v \in B 。  \\
给定任意有限个向量  v_1, v_2, \dots, v_n ，满足每个  v_i \in B  且总和  \sum_{i=1}^n v_i = \mathbf{0} 。  \\
则存在一个排列  \pi  使得所有前缀和\\
S_k = \sum_{i=1}^k v_{\pi(i)}, \quad k = 1,2,\dots,n\\都落在放大一倍的集合  2B = \{ 2x \mid x \in B \}  中。\\
\\
通俗点来讲,如果给你一堆在二维空间中的向量,并且这些向量都在B这个中心对成的凸多边形的范围内\\
那么我们就能够找到一种方法对这些向量进行拼接,使得每次拼接后都在2B范围内\\
通常用于广搜的时候限定搜索的范围.判断通过某些向量能否到达某个点
$$

#### 点乘

$$
\vec{a} \cdot \vec{b} = \|\vec{a}\| \|\vec{b}\| \cos \theta= a_x b_x + a_y b_y \\
     向量的长度:\|\vec{a}\| = \sqrt{\vec{a} \cdot \vec{a}} \\
    向量的夹角:\cos \theta = \frac{\vec{a} \cdot \vec{b}}{\|\vec{a}\| \|\vec{b}\|} \\
     向量的投影:\|\vec{a}\| \cos \theta = \frac{\vec{a} \cdot \vec{b}}{\|\vec{b}\|}\\
     向量垂直:\vec{a} \cdot \vec{b} = 0 \\
\vec{a} \cdot \vec{b} = \vec{b} \cdot \vec{a} \quad \text{(交换律)} \\
\vec{a} \cdot (\vec{b} + \vec{c}) = \vec{a} \cdot \vec{b} + \vec{a} \cdot \vec{c} \quad \text{(分配律)} \\
(\vec{a} \cdot \vec{b}) \cdot \vec{c} \ \text{无定义} \quad \text{(不满足结合律)} \\
$$

#### 叉乘

$$
\vec{a} \times \vec{b} = (a_x b_y - a_y b_x) \hat{k}= \|\vec{a}\|\|\vec{b}\| \sin \theta \hat{k} \\
  \vec{u} \times \vec{v} = 
  \begin{vmatrix}
  \mathbf{i} & \mathbf{j} & \mathbf{k} \\
  a & b & c \\
  d & e & f \\
  \end{vmatrix}= (bf - ce)\mathbf{i} - (af - cd)\mathbf{j} + (ae - bd)\mathbf{k}\\
  	二维叉乘结果我们视作一个标量，三维叉乘结果我们视作一个向量
  \\
平行四边形面积:\|\vec{a}\|\|\vec{b}\| |\sin \theta| = \|\vec{a} \times \vec{b}\|\\
 向量平行:\vec{a} \times \vec{b} = \vec{0} \\
 to-left测试:点P在有向直线AB指向方向哪一侧
  \begin{cases} 
  \vec{AB} \times \vec{AP} > 0, & P在有向直线AB左侧 \\
  \vec{AB} \times \vec{AP} < 0, & P在有向直线AB右侧 \\
  \vec{AB} \times \vec{AP} = 0, & P在有向直线AB上 
  \end{cases}\\
\vec{a} \times (\vec{b} + \vec{c}) = \vec{a} \times \vec{b} + \vec{a} \times \vec{c} \quad \text{(分配律)} \\
(\vec{a} + \vec{b}) \times \vec{c} = \vec{a} \times \vec{c} + \vec{b} \times \vec{c} \quad \text{(分配律)} \\
\vec{a} \times \vec{b} = -\vec{b} \times \vec{a} \quad \text{(反交换律)} \\
(\vec{a} \times \vec{b}) \times \vec{c} \neq \vec{a} \times (\vec{b} \times \vec{c}) \quad \text{(不满足结合律)} \\
$$

##### to_left测试

```c++
int to_left(point a, point b, point p) {
    //判断p点在a->b直线的哪一个方向
    //返回值>0则p在a->b有向直线左侧
    //返回值=0则p在a->b有向直线上
    //返回值<0则p在a->b有向直线右侧
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x);
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}
```

#### 向量旋转

$$
将向量逆时针旋转\theta角的线性变换
\begin{bmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{bmatrix}
\begin{bmatrix}
a_x \\
a_y
\end{bmatrix}
=
\begin{bmatrix}
\cos \theta \, a_x - \sin \theta \, a_y \\
\sin \theta \, a_x + \cos \theta \, a_y
\end{bmatrix}
$$

#### 求两向量之间角度

```c++
typedef double type; // 使用自定义类型便于修改精度
const double EPS = 1e-9; // 浮点比较精度
struct point {
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
type diancheng(point &a, point &b) {
    return a.x * b.x + a.y * b.y;
}
// 计算向量a和向量b之间的夹角（弧度），范围[0, π]
double jiaodu(point &a, point &b) {
    // 计算点积 (a·b)
    type dj = diancheng(a, b);
    // 计算向量模长
    double moa = sqrt(diancheng(a, a));
    double mob = sqrt(diancheng(b, b));
    // 处理零向量情况
    if (fabs(moa) < EPS || fabs(mob) < EPS) {
        return 0.0; // 零向量与任何向量的夹角定义为0
    }
    // 计算余弦值 (a·b)/(|a||b|)
    double yuxuan = dj / (moa * mob);
    // 处理浮点精度溢出
    if (yuxuan > 1.0) yuxuan = 1.0;
    else if (yuxuan < -1.0) yuxuan = -1.0;
    // 返回夹角（弧度）
    return acos(yuxuan);
}

// 计算有向角度版本（可区分顺逆时针）
double youxiangjiao(point &a, point &b) {
    double angle = jiaodu(a, b);
    // 计算叉积判断方向
    double cross_product = a.x * b.y - a.y * b.x;
    // 如果叉积为负，则角度为负（顺时针）
    return cross_product < 0 ? -angle : angle;
}

```

#### 线段

##### 判断两线段有无交点（跨立实验）

跨立实验是运用to-left测试来判断两线段有无相交的算法

判断A-B线段是否和C-D线段有交集，需要保证，A,B 在C-D线段不同侧，且C,D在A-B线段不同侧

如果出现三点共线情况和四点共线情况则需要特殊判断(这种时候to_left测试不适用于判断情况了)

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;

struct point {
    //用来记录点的坐标
    type x, y;

    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};

int sgn(type x) {
    //符号函数，判断是正数负数还是0
    if (fabs(x) < EPS) return 0;
    return x > 0 ? 1 : -1;
}

int to_left(point a, point b, point p) {
    //判断p点在a->b直线的哪一个方向
    //返回值>0则p在a->b有向直线左侧
    //返回值=0则p在a->b有向直线上
    //返回值<0则p在a->b有向直线右侧
    return sgn((b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x));
}

bool dianzaifanweinei(point a, point b, point p) {
    //判断点p是否在线段a,b形成的矩形范围内，结合to_left共线即可判断
    return p.x <= max(a.x, b.x) && p.x >= min(a.x, b.x) && p.y >= min(a.y, b.y) && p.y <= max(a.y, b.y);
}

bool xianduanxiangjiao(point a, point b, point c, point d) {
    //判断线段，a-b是否与c-d相交
    int pd1 = to_left(a, b, c);
    int pd2 = to_left(a, b, d);
    int pd3 = to_left(c, d, a);
    int pd4 = to_left(c, d, b);
    // 检查所有可能的端点在线段上的情况,这里包含了四点共线和三点共线的情况
    if (pd1 == 0 && dianzaifanweinei(a, b, c)) return true;
    if (pd2 == 0 && dianzaifanweinei(a, b, d)) return true;
    if (pd3 == 0 && dianzaifanweinei(c, d, a)) return true;
    if (pd4 == 0 && dianzaifanweinei(c, d, b)) return true;
    //剩下的情况都是严格不共线的情况了，此时进行跨立实验
    // 检查点c,d是否在ab的两侧
    bool flag1 = (pd1 > 0 && pd2 < 0) || (pd1 < 0 && pd2 > 0);
    // 检查点a,b是否在cd的两侧
    bool flag2 = (pd3 > 0 && pd4 < 0) || (pd3 < 0 && pd4 > 0);
    return flag1 && flag2;
}

```

##### 判断点是否在线段上

```c++
typedef double type;
const double EPS = 1e-9; // 使用合理的浮点误差阈值
struct point {
    double x, y;

    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
int to_left(point a, point b, point p) {
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x);
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}
type diancheng(point a, point b) {
    return a.x * b.x + a.y * b.y;
}
bool isonline(point a, point b, point p) {//如果判断一个自己求出来的有误差的点,那么to_left==0这一步，因为是叉乘,所以误差会比较大，此时可能会出错
    point pa = {a.x - p.x, a.y - p.y};
    point pb = {b.x - p.x, b.y - p.y};
    return to_left(a, b, p) == 0 && diancheng(pa, pb) <= 0; //to_left保证p在线上,点乘保证在两点之间
}
```

##### 点到线段的距离

```c++
typedef double type;
const double EPS = 1e-9;
struct point {
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
// 点积函数（新增）
type dianji(point a, point b) {
    return a.x * b.x + a.y * b.y;
}
// 叉乘函数（已有）
type chacheng(point a, point b) {
    return a.x * b.y - a.y * b.x;
}
// 向量模长（已有）
type mochang(point a) {
    return sqrt(a.x * a.x + a.y * a.y);
}
// 点到线段的距离（新增）
type point_to_segment(point A, point B, point P) {
    point AB = {B.x - A.x, B.y - A.y};
    point AP = {P.x - A.x, P.y - A.y};
    // 计算AB长度的平方
    type dot2 = dianji(AB, AB);
    // 处理线段退化为点的情况
    if (dot2 < EPS) {
        return mochang(AP);
    }
    // 计算AP在AB上的投影长度
    type dot1 = dianji(AB, AP);
    if (dot1 <= 0.0) {
        // 投影在A点外侧
        return mochang(AP);
    } else if (dot1 >= dot2) {
        // 投影在B点外侧
        point BP = {P.x - B.x, P.y - B.y};
        return mochang(BP);
    } else {
        // 投影在线段AB上
        return fabs(chacheng(AB, AP)) / sqrt(dot2);
    }
}

```

#### 直线

我们通常使用一个点+向量来代表直线
$$
(x, y) = \overrightarrow{OP} + \lambda \vec{v}
$$

##### 点到直线的距离

$$
求A到直线(P, \vec{v})的距离(B为A在直线(P, \vec{v})上的投影点)\\
\|\overrightarrow{AB}\|=\|\overrightarrow{PA}\||\sin\theta|=\frac{\|\vec{v}\times\overrightarrow{PA}\|}{\|\vec{v}\|}
$$

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;
struct point {
    //用来记录点的坐标
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
struct line {
    point p, v; //p为远点到直线上某一点的向量(坐标),v为这条直线的方向向量，注意这一个方向向量不可为0
    line(point a, point b) : p(a), v(point(b.x - a.x, b.y - a.y)) {
        //初始化时输入两个点即可自动构造出这条曲线
    }
};
type chacheng(point a, point b) {
    //注意，叉乘的结果可能是负数,下面进行计算的时候需要加上绝对值
    //这里的a,b意思为向量，并非点
    return a.x * b.y - a.y * b.x;
}
type mochang(point a) {
    return sqrt(a.x * a.x + a.y * a.y);
}
type point_to_line(line zhixian, point a) {
    //用来计算点到直线的最短距离
    point pa = {a.x - zhixian.p.x, a.y - zhixian.p.y}; // 从直线点到目标点的向量
    return fabs(chacheng(zhixian.v, pa)) / mochang(zhixian.v);
}

```

#####  点在直线上的投影点

$$
求A在直线(P, \vec{v})上的投影点B \\
 \|\overrightarrow{PB}\| = \|\overrightarrow{PA}\| \cos\theta = \frac{\overrightarrow{PA} \cdot \vec{v}}{\|\vec{v}\|} \\

  \overrightarrow{OB} = \overrightarrow{OP} + \overrightarrow{PB} = \overrightarrow{OP} + \frac{\|\overrightarrow{PB}\|}{\|\vec{v}\|} \vec{v}
   = \overrightarrow{OP} + \frac{\overrightarrow{PA} \cdot \vec{v}}{\|\vec{v}\|\|\vec{v}\|} \vec{v} = \overrightarrow{OP} + \frac{\overrightarrow{PA} \cdot \vec{v}}{\|\vec{v}\|^2} \vec{v}
$$

```c++
typedef double type; // 假设使用double类型
struct point {
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
struct line {
    point p, v; // p为直线上一点，v为方向向量
    line(point a, point b) : p(a), v(point(b.x - a.x, b.y - a.y)) {
        //初始化时输入两个点即可自动构造出这条曲线
    }
};
// 点积函数
type dianji(point a, point b) {
    return a.x * b.x + a.y * b.y;
}
// 向量模长
type mochang(point a) {
    return sqrt(a.x * a.x + a.y * a.y);
}
// 计算投影点B
point touyingdian(line zhixian, point a) {
    point PA = {a.x - zhixian.p.x, a.y - zhixian.p.y};
    type t = dianji(PA, zhixian.v) / dianji(zhixian.v, zhixian.v);
    point B = {zhixian.p.x + t * zhixian.v.x, zhixian.p.y + t * zhixian.v.y};
    return B;
}
```

##### 两直线交点

$$
给定两条直线(p_1,\vec{v_1})(p_2,\vec{v_2})，求两条直线交点\\
\alpha为p_1,p_2之间的连线与\vec{v_2}直线的夹角，
\beta为\vec{v_1}与\vec{v_2}之间的夹角
\\
 \begin{cases} 
\frac{\|\overrightarrow{P_1Q}\|}{\sin\alpha} = \frac{\|\overrightarrow{P_1P_2}\|}{\sin\beta}\\

\|\overrightarrow{v_2}\times\overrightarrow{P_2P_1}\|=\|\overrightarrow{v_2}\|\|\overrightarrow{P_2P_1}\|\sin\alpha\\
\|\overrightarrow{v_1}\times\overrightarrow{v_2}\|=\|\overrightarrow{v_1}\|\|\overrightarrow{v_2}\|\sin\beta
\\
  \end{cases}\\
\|\overrightarrow{P_1Q}\| = \frac{\|\overrightarrow{v_2} \times \overrightarrow{P_2P_1}\|\|\overrightarrow{v_1}\|}{\|\overrightarrow{v_1} \times \overrightarrow{v_2}\|}\\
\overrightarrow{OQ} = \overrightarrow{OP_1} + \overrightarrow{P_1Q} = \overrightarrow{OP_1} + \frac{\|\overrightarrow{P_1Q}\|}{\|\overrightarrow{v_1}\|}\overrightarrow{v_1}

= \overrightarrow{OP_1} + \frac{\|\overrightarrow{v_2} \times \overrightarrow{P_2P_1}\|}{\|\overrightarrow{v_1} \times \overrightarrow{v_2}\|}\overrightarrow{v_1}
$$

```c++
typedef double type; // 假设使用double类型
const double EPS = 1e-9;
struct point {
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
struct line {
    point p, v; // p为直线上一点，v为方向向量
    line(point a, point b) : p(a), v(point(b.x - a.x, b.y - a.y)) {
        //初始化时输入两个点即可自动构造出这条曲线
    }
};
// 叉乘函数（二维叉乘返回标量）
type chacheng(point a, point b) {
    return a.x * b.y - a.y * b.x;
}
// 向量模长
type mochang(point a) {
    return sqrt(a.x * a.x + a.y * a.y);
}
// 求两直线交点
point zhixianjiaodian(line L1, line L2) {//注意,这里没有考虑两直线重合的情况，根据题目酌情考虑
    point P2P1 = {L1.p.x - L2.p.x, L1.p.y - L2.p.y};
    if (fabs(chacheng(L1.v, L2.v)) < EPS) {
        return {NAN, NAN}; // 返回无效点，代表两直线平行，无交点,注意，不要对nan使用比较运算符,只能用isnan()函数判断，否则会出错
    }
    type bs = chacheng(L2.v, P2P1) / chacheng(L1.v, L2.v);
    return {L1.p.x + bs * L1.v.x, L1.p.y + bs * L1.v.y};
}

```

##### 直线与线段交点

$$
求直线与线段焦点时，我们需要使用到求两直线交点的代码。\\
先利用两次toleft判断直线与线段有无交点，再使用上面代码求线段和直线的交点\\
注意不要吧线段当成直线先求两直线的交点再判断是否在线段上,这样判断是否在线段上的公式toleft判断会出错，导致判断成点不在线上
$$

```c++
typedef double type; // 假设使用double类型
const double EPS = 1e-9;

struct point {
    type x, y;

    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};

int to_left(point a, point b, point p) {
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x);
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}

struct line {
    point p, v; // p为直线上一点，v为方向向量
    line(point a, point b) : p(a), v(point(b.x - a.x, b.y - a.y)) {
        //初始化时输入两个点即可自动构造出这条曲线
    }
};

// 叉乘函数（二维叉乘返回标量）
type chacheng(point a, point b) {
    return a.x * b.y - a.y * b.x;
}

// 向量模长
type mochang(point a) {
    return sqrt(a.x * a.x + a.y * a.y);
}

// 求两直线交点
point zhixianjiaodian(line L1, line L2) {//注意,这里没有考虑两直线重合的情况，根据题目酌情考虑
    point P2P1 = {L1.p.x - L2.p.x, L1.p.y - L2.p.y};
    if (fabs(chacheng(L1.v, L2.v)) < EPS) {
        return {NAN, NAN}; // 返回无效点，代表两直线平行，无交点,注意，不要对nan使用比较运算符,只能用isnan()函数判断，否则会出错
    }
    type bs = chacheng(L2.v, P2P1) / chacheng(L1.v, L2.v);
    return {L1.p.x + bs * L1.v.x, L1.p.y + bs * L1.v.y};
}

point xianduanzhixianjiaodian(point a, point b, line dq) {
    //求直线与线段的交点，如果没有交点，返回nan
    point p1 = dq.p;
    point p2(dq.p.x + dq.v.x, dq.p.y + dq.v.y);
    if (to_left(p1, p2, a) * to_left(p1, p2, b) <= 0) {//注意,这里没有考虑线段直线重合的情况，根据题目酌情考虑
        //说明一左一右,线段与直线有焦点
        return zhixianjiaodian(line(a, b), dq);
    } else {
        return point(NAN, NAN);
    }
}
```



#### 多边形

$$
我们通常用多边形的端点(p_1,p_2,p_3......p_n)来表示多边形
$$

##### 求多边形面积

$$
我们选定一个点作为O点(O在图形内或图形外答案都一样)我们把多边形拆分成若干三角形,运用叉乘的结果(可正可负)为面积来求解\\
S=\frac{1}{2}|\sum_{i=0}^{n-1}\overrightarrow{OP_i}\times\overrightarrow{OP_{(i+1)\mod n}}|\\
$$

```c++
typedef double type; // 假设使用double类型
const double EPS = 1e-9;
struct point {
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
// 叉乘函数（二维叉乘返回标量）
type chacheng(point a, point b) {
    return a.x * b.y - a.y * b.x;
}
// 计算多边形面积
type duobianxingmianji(vector<point> &poly) {//注意，这个poly数组内部的点必须先按照顺时针/逆时针排序后才可用
    //poly数组存储多边形的端点
    int n = poly.size();
    if (n < 3) {
        return 0.0;
    }
    type sum = 0.0;
    for (int i = 0; i < n; i++) {
        int j = (i + 1) % n; // 下一个点的索引（循环）
        sum += chacheng(poly[i], poly[j]);
    }
    return fabs(sum) / 2;
}
```

##### 判断点是否在凸包内(叉积计算法)O(N)

$$
与上面求面积的方法类似\\如果点在内部,其边的旋转方向统一，叉乘的结果的负号相同\\如果点在外部,则会有某些叉乘的结果符号相反\\如果点在边上,则会有某些叉乘的结果等于0\\
$$

```c++
typedef double type; // 假设使用double类型
const double EPS = 1e-9;
struct point {
    type x, y;
    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
// 叉乘函数（二维叉乘返回标量）
type chacheng(point a, point b) {
    return a.x * b.y - a.y * b.x;
}
int sgn(type x) {
    //符号函数，判断是正数负数还是0
    if (fabs(x) < EPS) return 0;
    return x > 0 ? 1 : -1;
}
// 判断点是否在凸包内
bool dianzaitubaonei(point dq, vector<point> &poly) {
    //注意，这个poly数组内部的点必须先按照顺时针/逆时针排序后才可用
    //poly数组存储多边形的端点
    //根据需要处理退化情况,比如点数少成不了凸包，多点共线
    type pre = 0;
    for (int i = 0, j = poly.size() - 1; i < poly.size(); j = i++) {
        //用来判断点在线上的特殊情况
        type ls = chacheng(point(poly[i].x - dq.x, poly[i].y - dq.y), point(poly[j].x - dq.x, poly[j].y - dq.y));
        if ((sgn(ls) > 0 && sgn(pre) < 0) || (sgn(ls) < 0 && sgn(pre) > 0)) {
            return false; //不满足说明有当前点在外部
        }
        if (sgn(ls) != 0) {
            pre = ls;
        }
    }
    return true;
}
```

##### 判断点是否在多边形内(射线法+回转数法)


$$
从该点引出一条直线，如果直线与多边形有奇数个交点,则该点在多边形内部,否则在直线外部
\\我们向右边引出一条射线,对于每一条边,如果向上穿过射线，我们记为转过了1圈，如果向下穿过射线,我们记为转过-1圈\\
(平行线段对环绕数贡献为0)\\
如果射线经过端点,则需要特殊处理，将点往上移动。
$$

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;

struct point {
    //用来记录点的坐标
    type x, y;

    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};

int to_left(point a, point b, point p) {
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x); //计算叉乘的结果
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}

int sgn(type x) {
    //符号函数，判断是正数负数还是0
    if (fabs(x) < EPS) return 0;
    return x > 0 ? 1 : -1;
}

type diancheng(point a, point b) {
    return a.x * b.x + a.y * b.y;
}

bool isonline(point a, point b, point p) {
    //判断p是否在ab线段上
    point pa = {a.x - p.x, a.y - p.y};
    point pb = {b.x - p.x, b.y - p.y};
    return (to_left(a, b, p) == 0) && (diancheng(pa, pb) <= 0); //to_left保证p在线上,点乘保证在两点之间
}

int huizhuanshu(point &dq, vector<point> &poly) {
    //回转数法判断点是否在封闭图形内
    //判断dq点是否在多边形内，和求poly绕dq数组的圈数
    //根据需要处理退化情况,比如点数少成不了凸包，多点共线
    int ans = 0; //ans为正代表正转,ans为负代表反转
    for (int i = 0, j = poly.size() - 1; i < poly.size(); j = i++) {
        //依次枚举每两条边
        if (isonline(poly[i], poly[j], dq)) {
            //如果点在边界上,那么点在图形内,且回转数为0
            return 0; //如果是判断回转数的圈数,则返回0，如果用于判断是否在圈内，则返回1
        }
        point a = poly[i];
        point b = poly[j];
        if (a.y == dq.y) a.y++;
        if (b.y == dq.y) b.y++; //我们通过抬升端点,解决射线经过端点的特殊情况
        if (a.y > b.y) swap(a, b); //我们交换点，讲y坐标小的点放在下面
        if (sgn((dq.y - a.y) * (dq.y - b.y)) <= 0 && to_left(a, b, dq) > 0) {
            //如果y与这条线有交点，而且dq点在这个点左边，第一个条件能够排除线段与射线平行的情况
            if (poly[i].y > poly[j].y) ans++; //如果是从下面往上面穿的边,逆时针转圈数+1
            else ans--; //如果是上面往下面穿的边,顺时针转圈数+1
        }
    }
    return ans; //如果是判断圈数，则返回ans,如果是判断点是否在圈内，则返回ans!=0,在圈外的点绕转移周一周转过的圈数一定为0
}
```

### 极角序

#### 使用极坐标进行排序

$$
我们可以使用atan2(y,x)公式来返回其对应的极角度\\
其分布规律为\\
\theta逆时针从第一象限到第二象限由0增长到\pi\\
\theta逆时针从第三象限到第四象限由-\pi增长到0\\
\theta \in \left[-\pi, \pi\right]
$$

```c++
struct point {
    //用来记录点的坐标
    type x, y, sita;

    point(type x = 0, type y = 0) : x(x), y(y) {
        sita = atan2(y, x);//常数过大,容易超时
    }
};

bool cmp(point &a, point &b) {
    return a.sita < b.sita;
}
```

#### 使用叉乘进行排序

$$
叉乘能够判断夹角\theta \in \left(0, \pi\right)内的向量的左右关系\\
对于\left(-\pi, \pi\right)内的向量，我们先上下进行分块，块之间按序排序,块之内使用toleft测试进行排序\\
需要注意的是,原点,极轴,极轴负方向的点需要特判
$$

**内置**

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;

struct point {
    //用来记录点的坐标
    type x, y;
    double sita;

    point(type x = 0, type y = 0) : x(x), y(y) {
        //sita = atan2(y, x);
    }

    static type chacheng(point a, point b) {
        //注意，叉乘的结果可能是负数,下面进行计算的时候需要加上绝对值
        //这里的a,b意思为向量，并非点
        return a.x * b.y - a.y * b.x;
    }

    static type diancheng(point a, point b) {
        return a.x * b.x + a.y * b.y;
    }

    friend bool operator<(const point &a, const point &b) {
        auto bh = [](const point &dq) {
            //我们把整个轴分为五块，分别代表远点，极轴正方向,极轴反方向，极轴以上,极轴以下。
            if (dq.y < -EPS) return 1; //代表极轴下面的的点
            if (dq.y > EPS) return 4; //代表极轴上面的的点
            if (dq.x < -EPS) return 5; //代表极轴相反方向那条线
            if (dq.x > EPS) return 3; //代表极轴方向那条线
            return 2; //代表0点
            //如果我们需要改变排序顺序，则修改对应值即可
        };
        int bha = bh(a), bhb = bh(b); //求出a,b两点对应的编号
        if (bha != bhb) return bha < bhb; //不同块时有限拍块
        auto ls = chacheng(a, b); //同块时内部使用叉乘to_left测试排
        if (abs(ls) <= EPS) return diancheng(a, a) < diancheng(b, b) - EPS; //如果在同一条线上，那么把距离近的放在前面
        return ls > EPS;
        //需要定义友元
    }
};
```

**外放**

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;

struct point {
    //用来记录点的坐标
    type x, y;
    double sita;

    point(type x = 0, type y = 0) : x(x), y(y) {
       // sita = atan2(y, x);
    }
};

type chacheng(point a, point b) {
    //注意，叉乘的结果可能是负数,下面进行计算的时候需要加上绝对值
    //这里的a,b意思为向量，并非点
    return a.x * b.y - a.y * b.x;
}

type diancheng(point a, point b) {
    return a.x * b.x + a.y * b.y;
}

bool cmp(point &a, point &b) {
    auto bh = [](const point &dq) {
        //我们把整个轴分为五块，分别代表远点，极轴正方向,极轴反方向，极轴以上,极轴以下。
        if (dq.y < -EPS) return 1; //代表极轴下面的的点
        if (dq.y > EPS) return 4; //代表极轴上面的的点
        if (dq.x < -EPS) return 5; //代表极轴相反方向那条线
        if (dq.x > EPS) return 3; //代表极轴方向那条线
        return 2; //代表0点
        //如果我们需要改变排序顺序，则修改对应值即可
    };
    int bha = bh(a), bhb = bh(b); //求出a,b两点对应的编号
    if (bha != bhb) return bha < bhb; //不同块时有限拍块
    auto ls = chacheng(a, b); //同块时内部使用叉乘to_left测试排
    if (abs(ls) <= EPS) return diancheng(a, a) < diancheng(b, b) - EPS; //同一条线上的保证近的先使用
    return ls > EPS;
}
```

#### 直线进行旋转

$$
如果出现一条直线分割二维平面的题目时，通常采用枚举其中一点,作为原点，然后围绕这点旋转射线去扫一遍的方法\\
因为正负方向上的直线都需要旋转，难以考虑，所以我们通常把负半轴以下的点中心对称到正半轴以上\\
注意特殊考虑原点,共线点,x正负半轴
$$

#### 平面整体旋转


$$
如果出现空间上所有点都要绕原点逆(顺)时针旋转的情况,我们不妨使用相对思想,使得坐标轴绕原点顺(逆)时针旋转\\
我们求出坐标轴需要转到的关键点(投影时相对位置发生改变的点),对这些关键点使用极角序排序,对这些关键点进行分析处理
$$

### 凸包

#### 求凸包

##### grahan scan(极坐标排序)算法求凸包(nlogn)

$$
我们先对图内各点进行极角排序,然后我们从最下面的点开始,依次将每个点放入栈中,每次放入前，我们判断上一个点是否满足凸包的条件\\
如果是凸包,那么边上不会出现内凹的情况,我们使用toleft测试,测试每一条边的情况即可
$$

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;

struct point {
    //用来记录点的坐标
    type x, y;
    double sita;

    point(type x = 0, type y = 0) : x(x), y(y) {
        // sita = atan2(y, x);
    }
};

type chacheng(point a, point b) {
    //注意，叉乘的结果可能是负数,下面进行计算的时候需要加上绝对值
    //这里的a,b意思为向量，并非点
    return a.x * b.y - a.y * b.x;
}

type diancheng(point a, point b) {
    return a.x * b.x + a.y * b.y;
}

int to_left(point a, point b, point p) {
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x);
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}

vector<point> tubao(vector<point> poly) {
    //返回凸包数组
    if (poly.size() <= 2) return poly;
    vector<point> zhan; //我们用数组模拟栈,存储凸包上的每一个点
    point basic = poly[0]; //选择一个基准点
    for (int i = 0; i < poly.size(); i++) {
        if (basic.y > poly[i].y) {
            //选择最下面的点作为基准点
            basic = poly[i];
        } else if (fabs(basic.y - poly[i].y) < EPS && basic.x > poly[i].x) {
            //同一高度的,选择最左侧的
            basic = poly[i];
        }
    }
    sort(poly.begin(), poly.end(), [&](point a, point b) {
        a = point(a.x - basic.x, a.y - basic.y);
        b = point(b.x - basic.x, b.y - basic.y); //将比较的点平移到以basic为基准点进行排序
        auto bh = [](const point &dq) {
            //我们把整个轴分为五块，分别代表远点，极轴正方向,极轴反方向，极轴以上,极轴以下。
            if (dq.y < -EPS) return 2; //代表极轴下面的的点
            if (dq.y > EPS) return 4; //代表极轴上面的的点
            if (dq.x < -EPS) return 5; //代表极轴相反方向那条线
            if (dq.x > EPS) return 3; //代表极轴方向那条线
            return 1; //代表0点, 同时也是基准点
            //如果我们需要改变排序顺序，则修改对应值即可
        };
        int bha = bh(a), bhb = bh(b); //求出a,b两点对应的编号
        if (bha != bhb) return bha < bhb; //不同块时有限拍块
        auto ls = chacheng(a, b); //同块时内部使用叉乘to_left测试排
        if (abs(ls) <= EPS) return diancheng(a, a) < diancheng(b, b) - EPS; //同一条线上的保证近的先使用
        return ls > EPS;
    });
    auto check = [&](vector<point> &ls, point &dq) {
        auto a = ls.back();
        auto b = ls[ls.size() - 2];
        return to_left(b, a, dq) <= 0; //这里三点共线的时候也记录为不加入,如果需要加入，则删除等于号
    };
    for (int i = 0; i < poly.size(); i++) {
        while (zhan.size() > 1 && check(zhan, poly[i])) {
            zhan.pop_back();
        }
        zhan.emplace_back(poly[i]);
    }
    return zhan;
}
```



##### Monotone chain,a.k.a. Andrew's(x坐标排序求上下凸包)算法求凸包(nlogn)

$$
我们先对图内各点进行按x坐标排序,然后我们从最左边的点开始,依次将每个点放入栈中,每次放入前，我们判断上一个点是否满足凸包的条件\\
如果是凸包,那么边上不会出现内凹的情况,我们使用toleft测试,测试每一条边的情况即可(判断点之间旋转的角度是否逆时针)\\
我们正向跑一遍,求出下凸包,再倒着跑一遍,求出上凸包
$$

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;
struct point {
    //用来记录点的坐标
    type x, y;
    double sita;
    point(type x = 0, type y = 0) : x(x), y(y) {
        // sita = atan2(y, x);
    }
};
int to_left(point a, point b, point p) {
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x);
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}
vector<point> tubao(vector<point> poly) {//返回凸包数组
    if (poly.size() <= 2) return poly;
    vector<point> zhan; //我们用数组模拟栈,存储凸包上的每一个点
    sort(poly.begin(), poly.end(), [&](point a, point b) {
        if (a.x == b.x) {
            return a.y < b.y;
        }
        return a.x < b.x;
    }); //按照升序进行排序
    auto check = [&](vector<point> &ls, point &dq) {
        auto a = ls.back();
        auto b = ls[ls.size() - 2];
        return to_left(b, a, dq) <= 0; //这里三点共线的时候也记录为不加入,如果需要加入，则删除等于号
    };
    //用来计算上凸包
    for (int i = 0; i < poly.size(); i++) {
        while (zhan.size() > 1 && check(zhan, poly[i])) {
            zhan.pop_back();
        }
        zhan.emplace_back(poly[i]);
    }
    //用来计算下凸包
    int gs = zhan.size(); //这里创建一个下凸包占用多少个点，防止算上凸包的时候把下凸包的点给弹出去
    zhan.pop_back();
    for (int i = poly.size() - 1; i >= 0; i--) {
        while (zhan.size() > gs && check(zhan, poly[i])) {
            zhan.pop_back();
        }
        zhan.emplace_back(poly[i]);
    }
    zhan.pop_back();
    return zhan;
}
```

#### 应用：

##### 旋转卡壳

$$
对于求凸包直径,凸变形宽,凸边形间最大距离,凸变形间最小距离,最小面积外界矩形,最小周长外接矩形等问题时\\
我们通常会想到使用双指针的做法,但是如果对点之间进行双指针，那么结果就会出错\\
因为凸包上的点不满足单调性的规律(比如一个很瘪的六边形),但是极边满足,点到极边的距离满足三分性\\
我们使用旋转卡壳算法,利用双指针的原理,双指针极边与点。从而求出答案
$$

```c++
typedef double type; // 使用 long long 存储坐标
const double EPS = 1e-9;

struct point {
    type x, y;

    point(type x = 0, type y = 0) : x(x), y(y) {
    }
};
// （旋转卡壳算法）
type xuanzhuankake(vector<point> &hull) {//传入凸包
    /*这里加入特判点数不够的步骤*/
    //上面需要特判点数不够的情况
    auto area = [&](point a, point b, point c) -> type {
    // 计算三角形面积（叉积绝对值）,我们通过等面积法，来找出对锺点
        return abs((b.x - a.x) * (c.y - a.y) - (b.y - a.y) * (c.x - a.x));
    };
    auto next = [&](int dq) {
        //找到下一个指针指向哪
        return (dq + 1) % hull.size();
    };
    int duizhong = 1; //用来记录对锺点
    for (int i = 0, j = next(i); i < hull.size(); j = next(++i)) {//枚举极边,j和i分别代表同一条边的前后两个点
        /*这里加入统计答案的步骤*/
        while (area(hull[i], hull[j], hull[next(duizhong)]) /*根据题目要求更新指针指向*/>= area(hull[i], hull[j], hull[duizhong])) {//这里的判断条件根据题目来判断
            duizhong = next(duizhong);
            /*这里加入统计答案的步骤*/
        }
    }
    return ans;//根据题目需要改变
}
```

##### 判断点是否在凸多边形内O(logn)

###### 基于grahan scan判断

$$
我们通过对极坐标排序后的点进行二分,判断目标点在哪一部分扇形内,二分确定扇形之后,使用toleft测试判断
$$

```c++
typedef double type; //如果改成double，下面判断是否为0的时候还要加上误差值temp
const double EPS = 1e-9;
struct point {
    //用来记录点的坐标
    type x, y;
    double sita;

    point(type x = 0, type y = 0) : x(x), y(y) {
        // sita = atan2(y, x);
    }
};
type chacheng(point a, point b) {
    //注意，叉乘的结果可能是负数,下面进行计算的时候需要加上绝对值
    //这里的a,b意思为向量，并非点
    return a.x * b.y - a.y * b.x;
}
type diancheng(point a, point b) {
    return a.x * b.x + a.y * b.y;
}

int to_left(point a, point b, point p) {
    type ls = (b.x - a.x) * (p.y - a.y) - (b.y - a.y) * (p.x - a.x);
    if (fabs(ls) < EPS) return 0;
    else if (ls < 0) {
        return -1;
    } else {
        return 1;
    }
}
bool dianzaitubaonei(point dq, vector<point> &poly) {
    //poly必须按照逆时针进行排序且为凸包,如果题目给的是顺时针,则需要使用reverse调换

    point basic = poly[0]; //选择一个基准点
    if (fabs(dq.x - basic.x) < EPS && fabs(dq.y - basic.y) < EPS) {
        //如果与原点重合则进行判断
        return true;
    }
    auto check = [&](point a, point b) {
        a = point(a.x - basic.x, a.y - basic.y);
        b = point(b.x - basic.x, b.y - basic.y); //将比较的点平移到以basic为基准点进行排序
        auto bh = [](const point &dq) {
            //我们把整个轴分为五块，分别代表远点，极轴正方向,极轴反方向，极轴以上,极轴以下。
            if (dq.y < -EPS) return 2; //代表极轴下面的的点
            if (dq.y > EPS) return 4; //代表极轴上面的的点
            if (dq.x < -EPS) return 5; //代表极轴相反方向那条线
            if (dq.x > EPS) return 3; //代表极轴方向那条线
            return 1; //代表0点
            //如果我们需要改变排序顺序，则修改对应值即可
        };
        int bha = bh(a), bhb = bh(b); //求出a,b两点对应的编号
        if (bha != bhb) return bha < bhb; //不同块时有限拍块
        auto ls = chacheng(a, b); //同块时内部使用叉乘to_left测试排
        if (abs(ls) <= EPS) return diancheng(a, a) < diancheng(b, b) - EPS; //同一条线上的保证近的先使用
        return ls > EPS;
    }; //用来比较
    int l = 0, r = poly.size(); //l和所有小于l的点的极角序都比dq点小,r和所有大于等于r的点的极角序都大于等于dq
    while (l + 1 < r) {
        //我们在上面进行二分
        int mid = l + r >> 1;
        if (check(poly[mid], dq)) {
            l = mid;
        } else {
            r = mid;
        }
    }
    if (r == 1) {
        //点在线上的情况特判
        if (diancheng(point(poly[r].x-dq.x,poly[r].y-dq.y), point(poly[0].x-dq.x,poly[0].y-dq.y)) <= 0) {
            return 1;
        } else {
            return 0;
        }
    } else if (r <= poly.size() - 1 && r >= 2) {
        //只有在这个范围内才可以
        if (to_left(poly[l], poly[r], dq) >= 0) {
            //使用to_left测试判断是否在扇形区域内
            return 1;
        } else {
            return 0;
        }
    }
    return 0;
}
```



###### 基于Monotone chain,a.k.a. Andrew's 判断

```c++

```

### 切比雪夫距离和曼哈顿距离转换

$$
切比雪夫距离表达式:
\\
A = (a_1, a_2, \dots, a_n) 和 B = (b_1, b_2, \dots, b_n)  
\\
 d_{\infty}(A, B) = \max_{i} \left( |a_i - b_i| \right) 
\\
 d_{\text{Chebyshev}} = \max \left( |a_1 - b_1|,\ |a_2 - b_2|,\ \dots,\ |a_n - b_n| \right) 
\\
当 A = (x_1, y_1)B = (x_2, y_2)
\\
 d = \max \left( |x_1 - x_2|,\ |y_1 - y_2| \right)
$$



$$
曼哈顿距离表达式：
\\
A = (a_1, a_2, \dots, a_n) 和 B = (b_1, b_2, \dots, b_n)
\\
d(A, B) = \sum_{i=1}^{n} |a_i - b_i|
$$
**所以将每一个点 (x,y) 转化为 (x+y, x-y)，新坐标系下的切比雪夫距离即为原坐标系下的曼哈顿距离。**

**所以将每一个点 (x,y) 转化为 ((x+y)/2, (x-y)/2)，新坐标系下的曼哈顿距离即为原坐标系下的切比雪夫距离。**

### 三角形外接圆

```c++
//求三角形外接圆（中垂线交点）
struct Point {
    double x, y;
    Point operator+(const Point &p) const {return {x + p.x, y + p.y};}
    Point operator-(const Point &p) const {return {x - p.x, y - p.y};}
    Point operator*(double _k) const {return {x * _k, y * _k};}
    Point operator/(double _k) const {return {x / _k, y / _k};}
    double operator*(const Point &p) const {return y * p.x - x * p.y;} // cross
};
struct Line {Point p, vec;};
struct Circle {Point p;double r;};
double Dist(Point a, Point b) { return hypot(a.x - b.x, a.y - b.y); }

int dcmp(double x, double y = 0) {
      return fabs(x - y) < eps ? 0 : (x < y ? -1 : 1);
}

Point Intersect(const Line &p1, const Line &p2) {
    double k = (p2.p - p1.p) * p2.vec / (p1.vec * p2.vec);
    return p1.p + p1.vec * k;
}
    
Line MidPerp(const Point &p1, const Point &p2) {
    auto pp = p1 - p2;
    return {(p1 + p2) / 2, {pp.y, -pp.x}};
}

Circle Circum(const Point &p1, const Point &p2, const Point &p3) {//在使用时调用该函数,进行输出
    auto p = Intersect(MidPerp(p1, p2), MidPerp(p2, p3));
    return {p, Dist(p, p1)};
}
```

```c++

```
