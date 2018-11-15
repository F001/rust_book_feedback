# rust_book_feedback

这个项目用于记录《深入浅出Rust》的勘误以及读者反馈。深入浅出Rust读者交流群 497531779。

## 勘误表

* P8
  代码 `use std::prelude::*;` 应改为 `use std::prelude::v1::*;`

* P18
  第三块代码中
  ```rust
  let var6 = 12usize; // i6变量是usize类型
  let var7 = 0x_ff_u8;  // i7变量是u8"类型
  ```
  注释应该分别为 `var6` 变量和 `var7` 变量。

* P27
  tuple、struct、struct tuple 起的作用都是把几个不同类型的成员打包组合成一个类型

  应改为

  tuple、struct、tuple struct 起的作用都是把几个不同类型的成员打包组合成一个类型

* P39
  `fn func(i: i32) -> bool` 函数函数签名和函数体类型不匹配，函数参数名字与内部变量名字也不匹配。可以修正为以下代码：

  ```rust
  fn func(i: i32) -> std::cmp::Ordering {
      if i < 0 {
          std::cmp::Ordering::Less
      } else if i > 0 {
          std::cmp::Ordering::Greater
      } else {
          std::cmp::Ordering::Equal
      }
  }
  ```

* P41
  最下面那段代码，`println!("{}", v);`应该改为`println!("{:?}", v);`：
  ```rust
  fn main() {
    let v = loop{};
    println!("{:?}", v);
  }
  ```

* P48
  这个函数的返回类型可以是任何一个满足 Termination trait 约束的类型，其中 `()`、bool、Result 都是满足这个约束的

  应改为

  这个函数的返回类型可以是任何一个满足 Termination trait 约束的类型，比如 `()`、`Result<(), E>` 等类型就是满足这个约束的

* P89
  倒数第二段代码，`while let` 应该改为 `if let`:
  ```rust
  if let A(x) | B(x) = expr {
      do_something(x);
  }
  ```

* P159
  代码中的 `vdata.set(10);` 应改为 `data.set(10);`

* P161
  绝对不可能让用户有机会通过 `&Cetl<T>` 获得 `&T` 或者 `&mut T`

  其中，`&Cetl<T>` 应改为 `&Cell<T>`

* P187
  ……避免了Arc的运行效率损失, 是非常有用的scoped函数与spawn函数的区别就在于……

  应改为

  ……避免了Arc的运行效率损失, 是非常有用的。scoped函数与spawn函数的区别就在于……

  本页最后一句，只要用户有可能在不使用 unsafe 构造出内存安全

  应改为

  只要用户有可能在不使用 unsafe 构造出内存不安全

* P210
  究竟准是准的子类型

  应改为

  究竟谁是谁的子类型

* P211
  类型 `fn(T)->U` 对于泛型参数`T`具备协变关系

  应改为

  类型 `fn(T)->U` 对于泛型参数`T`具备逆变关系

  类型 `fn(T)->U` 对于泛型参数`U`具备逆变关系

  应改为

  类型 `fn(T)->U` 对于泛型参数`T`具备协变关系

* P212
  `PhantomData<'aT>` 应该改为 `PhantomData<&'a T>`

* P257
  其次尝试选择 `fn call_mut(&self, args:Args)`

  应改为

  其次尝试选择 `fn call_mut(&mut self, args:Args)`

* P279
  图片内箭头指向位置错乱了

