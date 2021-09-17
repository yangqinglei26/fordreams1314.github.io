---
title: idea相关使用
date: 2021-09-13 16:30:06
tags:	
  - java
category:
  - java
---

## 配置注释

```java
/**
  * @author yql
  * @date ${DATE}
  * @desc
  */

- 类注释

/**
  * @author yql
  * @date $DATE$
  * @desc
  */
- 方法注释
/**
  * @author yql
  * @date $DATE$
  * @desc
  $params$
  * @return $return$
  */
```

```groovy
groovyScript("def result=''; def params=\"${_1}\".replaceAll('[\\\\[|\\\\]|\\\\s]', '').split(',').toList(); for(i = 0; i < params.size(); i++) {result+='* @param ' + params[i] + ((i < params.size() - 1) ? '\\r\\n' : '')}; return result", methodParameters())
```

```groovy
groovyScript("def result=''; def params=\"${_1}\".replaceAll('[\\\\[|\\\\]|\\\\s]', '').split('<').toList(); for(i = 0; i < params.size(); i++) {if(i!=0){result+='<';};  def p1=params[i].split(',').toList();  for(i2 = 0; i2 < p1.size(); i2++) { def p2=p1[i2].split('\\\\.').toList();  result+=p2[p2.size()-1]; if(i2!=p1.size()-1){result+=','}  } ;  };  return result", methodReturnType())
```

