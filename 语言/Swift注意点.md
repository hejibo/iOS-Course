该篇文章为我在日常coding过程中使用OC进行了一些骚操作或者被虐得很惨的记录，持续更新中.....

1. `Array<[String : String]>`的取key和value问题。

 背景：最近在上编译原理的课，第一个实验为编写一个词法分析器，原本我的想法是使用Qt来完成，写C/C++。但是突然一闪，哈！这是使用Swift进行开发的好时机！因此，我就开始了......省略五千字，详细见[这篇文章](../macOS/macOS开发（词法分析器）.md)

 在开发词法分析器的过程中，我遇到了这么个问题，知道词法分析的同学都能明白，在词法分析阶段需要一个tokens二元组接收词法分析后的结果，因此我还是用了OC中的那套思想，可以用一个`NSMutableArray`，其中装一个个的字典，其实也有相关放的是弄个二维数组，但是觉得套个字典数组可能比较好吧。

 但也就是这个“可能比较好吧”的想法，直接导致了这么个坑的出现，发现不管怎么搞，都没法使用自己之前已掌握的能力去筛选出数组中每个字典的key和value。搞到最后，发现如果各位同学也是跟我一样，有`Array<String : String>`这个格式数据的需求，想要遍历出数组中每个元素的key和value，那么就可以参考下边这种做法：

 ```Swift
 // 给NSTextField刷新上key，row为当前数组的下标，先获取到所有keys，然后取第一个，虽然实际上只有一个
 textField.stringValue = Array(tokenArray[row].keys)[0]

 //给NSTextField刷新上value
 textField.stringValue = Array(tokenArray[row].values)[0]

 ```

 2. Swift中的！和？（解包实在是太恶心的一件事了）[http://www.jb51.net/article/100382.htm](http://www.jb51.net/article/100382.htm)，感觉这篇文章是抄的，但是写的内容还算明了。

3. Swift中的值类型和引用类型。[https://www.jianshu.com/p/ba12b64f6350](https://www.jianshu.com/p/ba12b64f6350)

4. Swift中的属性相关。神奇的set和get。[https://www.jianshu.com/p/071024b38a8b](https://www.jianshu.com/p/071024b38a8b)

5. **继承**。对于自定义的类而言，Objective-C的类，不能继承自Swift的类，即要混编的OC类不能是Swift类的子类。反过来，需要混编的Swift类可以继承自OC的类。
