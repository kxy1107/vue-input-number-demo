# Vue InputNumber 计数器

> A Vue InputNumber components

## How To Use

将src/components/inputNumber.vue 拷贝到你的项目的组件内(样式什么的自己调整就好)

在需要用的地方引入该组件

import InputNumber from '@/components/inputNumber.vue'

添加组件声明
 components:{
    InputNumber,
  }

在<template> 中使用组件
<input-number></input-number>

# 参数说明

### 可接收的参数
| 参数名称        | 说明           | 类型 | 默认值  |
| :-------------: |:-------------:| :-----:| :-----:|
| value      | 传入输入框的值 | Number | 1 |
| step      | 计数器步长 | Number | 1 |
| max      | 允许设置的最大值 | Number |   99 |
| min       | 允许设置的最小值 | Number |    1 |
| itemIndex     | 传入数组的下标| Number   |  0 |

### 事件
| 事件名称        | 说明           | 返回值  |
| ------------- |:-------------:| -----:|
| subNum      |点击减号时触发 | object {inputNumber:修改后的值， itemIndex:传入的数组下标，标识修改了哪个组件} |
| addNum      |点击加号时触发 | object {inputNumber:修改后的值， itemIndex:传入的数组下标，标识修改了哪个组件} |
| inputChange    |输入框内容变化触发 | object {inputNumber:修改后的值， itemIndex:传入的数组下标，标识修改了哪个组件} |


For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
