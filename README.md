# goml
machine learning (ML) by Go (golang)

开这个项目主要是教育目的，顺便自己熟悉一下`Go`语言。

### 语言考虑

    Python用了十多年了，它也需要备胎啊。
    Rust语言的主要问题是，实在是太复杂。
    Go非常简洁,虽STW垃圾收集难掩其神采。

### 算法选择（初步）

    k-Nearest Neighbor Classifiers
    K-Means Clustering
    Linear Regression
    Logistic Regression
    Principal Component Analysis
    Naive Bayes Classifiers
    Decision Tree
    Regression Tree

### 项目规划（初步）

    线性计算库使用gonum。
    接口参考XGBoost的API， 每个模型至少要实现train和predict。
    底层求解算法尽量通用化、统一化，但不强求。
    算法主要参考李航老师的"统计机器学习"， 但不拘泥于此。
    
### 语言备忘

`Paul Graham`为了解释语言编程能力的不一样，设计了下面的问题：
写一个函数，它能够生成累加器，即这个函数接受一个参数x，然后返回另一个函数，后者接受参数y，然后返回x增加（increment）了y后的值。
(这里说的是增加，而不是n和i的相加（plus）。累加器就是应该完成n的累加)

使用`Go`语言, 我简单的一边Google,一边按自己的想法去写, 很快就完成了(`int`版). 
而使用`Rust`翻了半天书也没编译通过(语法不熟, 且思路之外的细节太多)!

```
package main

import (
    "fmt"
)

func gfunc(x *int) (func (int) int) {
    return func(y int) int {
        *x = *x + y
        return *x
    }
}

func main(){
    x := 12
    f := gfunc(&x);
    y := f(3)

    fmt.Printf("done %v %v!", x, y);
}
```
