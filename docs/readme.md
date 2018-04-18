

## django documents


##
{{}} 变量
{%%}标签
{{|}}过滤器
{%include%}  包含
{%extends%}  继承


Include在我们学习当中叫做包含，将指定页原封不动的加载或包含到本页，我们不用修改任何地方，直接包含过来，但是这个跟include不同的是，我我们加载的模板可以根据定义的块，我们开始再base页里定义了一个块叫做ddd，那么我们在indexb.html里边写上ddd块，然后加一个hello world:

而extends，则是用于模板，我们用block 来替换模板里的内容
比如如下配置，这里我们使用content_template.html，将模板里{% block title %} {% endblock %}的内容替换为了New Acount addition.

```

{% extends 'content_template.html' %}


{% block title %}
         New Acount addition.
{% endblock %}
```