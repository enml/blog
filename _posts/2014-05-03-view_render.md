---
layout: post
title: view传递context的方式
category : python_django
tagline: "Supporting tagline"
tags : [python, django]
---
{% include JB/setup %}
# view传递context的方式
---

** 通过view的render()方法填充template可以有以下方式：**

1.适合于数据量小且静态的数据。在template中直接使用相关键值为标签：
`{{ name }} {{ ship_date }}`

```
def test1(request):
    return render(request,'test/raw.htm',{
                'name':'Enm',
                'age':22,
                'company': 'Outdoor Equipment',
                'ship_date': datetime.datetime.now(),
                'ordered_warranty': False})
```
<!--break-->

2.通过调用属性的方式传递整个dictionary。但在template中必须使用属性方式：\{\{ **person.** name \}\},\{\% for i,k in **dict.** items \%\}

```
def test2():
    person = {  'name':'Enm',
                'age':22,
                'company': 'Outdoor Equipment',
                'ship_date': datetime.datetime.now(),
                'ordered_warranty': False}
    
    dict = {"name":"enm","age":"21","school":"szu"}
    return render(request,'test/raw.htm',{ 'person':person, 'dict':dict})
```

3.使用**locals(),locals()** 是个字典，直接赋值给变量。很明显这种方式更加优雅和便捷，但缺点就是它会把所有的dictionary都传递，也就是说它默认传递的值可能会比你预想中的多。

   template中仍然必须使用属性方式：\{\{ **person.** name \}\},\{\% for i,k in **dict.** items \%\}

```
def test3():
    person = {  'name': 'Enm',
                'age':22,
                'company': 'Outdoor Equipment',
                'ship_date': datetime.datetime.now(),
                'ordered_warranty': False}
    
    dict = {"name":"enm","age":"21","school":"szu"}
    return render(request,'test/raw.htm',locals())
```
