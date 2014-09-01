# android 数据变化时notifyDataSetChanged 无效的解决方案(未解决)
[原地址](http://ningtukun.blog.163.com/blog/static/18654144520142725053404/)

假定你的数据集合体为data，如果有新的数据加入或需要把旧数据全部更换，应采用追加的方式，保留data的原引用

1. 如data是个ArrayList，应使用add或先clear再addALL

2. 否则你用data = 一个新的数据集合体，这时调用notifyDataSetChanged 是无效的

之所以这样做是因为adapter初始化时就绑定了数据集合的地址，所以adapter只关心原地址所指向的数据有没有改变，只有原地址所指向的数据发生变化，调用notifyDataSetChanged 才有效。

第二种做法显然让data 的引用指向了一个新的引用，原地址的数据并没有发生变化