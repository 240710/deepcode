用Python编写函数：输⼊变量n，输出形如{1:1, … ,n: n*n} 的字典。例如当n=8时，输出{1: 1，2: 4, 3: 9, 4: 16, 5:25, 6: 36, 7: 49, 8: 64}

~~~python
print('请输入一个数字：')
n=int(input())
d=dict()#利用dict（）函数创建一个字典
for i in range(1,n+1):#利用range（）函数设定范围，并确定for循环的循环次数
    d[i]=i*i#使得字典输出{1:1, … ,n: n*n}的效果

print(d)
~~~

