## mysql

### 语句
* case when 当结果满足某一个条件的时候执行对应的result
  ```
    case colume
        when condition then result
        when condition then result
        when condition then result
    else
        resule
    end
        new_column_name
  ```
  1. 当满足某一提条件的时候,执行result,把结果放到new_column_name中
  2. __case when 用在select语句中,新的字段可以用来排序,但是不能用在where中__

* DATE_ADD 加减一段时间和当前时间比较情况
  > DATE_ADD(date,INTERVAL expr type)
  指定的时间  expr(时间间隔,负值加上-)  type(时间间隔单位)

  `SELECT OrderId,DATE_ADD(OrderDate,INTERVAL 7 DAY) AS OrderPayDate FROM Orders`