# TO-DO-List
基于vue实现的待办列表网站

## 需求实现

1. 添加待办内容

声明add函数，将每个列表项push到数组里，添加后编辑框清空；编辑框内容change后调用add函数。

2. 删除待办内容

声明delItem函数 ，使用splice（index,1)删除数组项；点击删除按钮后将index作为参数传入delItem函数（index是v-for循环渲染li标签时获取的）

3. 修改代办内容

（1）双击文本内容时给父类li添加editing类名（也就是将文本内容变为输入框）;li添加editing类名时需让当前的状态和双击的那个item对应起来，当前需要一个值是和item对应的，所以在data中声明一个属性n初始为空，双击文本内容时将对应的item对象给n;则**添加editing时只需判断n是否等于当前item**

（2）双击后获取焦点：使用自定义指令v-focus(添加条件n=item),update钩子函数中使用el.focus()   

（3）输入框内容修改完成后（change和blur事件都可触发）让属性n再次为空，便于下次修改其他数据

（4）按esc还原数据；添加keydown事件，按下时让属性n为空，为了保存原来文本框的内容，需要给v-model="ietm.txt"添加lazy修饰符（lazy将input事件修改为change事件），因为按下esc没触发change事件，所以内容还原了。

4. 记录未完成的个数

在计算属性中声明一个方法uncompleted获取未完成的数组，数组的长度即未完成的个数，在标签中用模板字符串渲染方法。

5. 全选反选

在计算属性中声明allDone方法，给全选框绑定该方法；allDone方法中设置get，set方法；获取每一个列表项都为真全选框才为真；设置时根据全选框的value值将列表的每一项都设置成和value值一样

6. 清除所有已完成

点击清除按钮时，将todoList列表项等于未完成uncompeted

7. 状态切换

有三种状态，all,uncompleted,completed

（1）点击时切换状态；data中添加type属性，代表三种状态；绑定类名selected时添加条件type='all'或‘completed’。点击事件时令type等于对应的类型。

（2）点击时显示对应列表项

在计算属性中添加filterList方法过滤出对应状态的数组；数据渲染时v-for渲染的不再是todoList，应该修改为filterList,也就是过滤后的数组列表

8. 数据持久化

监听todoList，数据变化时存储到localstorage（转换为json字符串后在进行存储）；data中todoList的属性值是从本地存储取出的数据，当本地存储中没有数据时，属性值是空数组









 
