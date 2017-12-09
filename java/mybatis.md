### org.mybatis.spring.MyBatisSystemException: nested exception is org.apache.ibatis.executor.result.ResultMapException: Error attempting to get column 'id' from result set.  Cause: org.apache.ibatis.executor.result.ResultMapException: Error attempting to get column 'id' from result set.  Cause: java.sql.SQLException: Invalid value for getInt() - '0101ec91b186468aa53f08e6fa14e1ee'] with root cause
java.sql.SQLException: Invalid value for getInt() - '0101ec91b186468aa53f08e6fa14e1ee'

说明：Mybatis默认接收的参数类型为int,需要显示的指定参数类型为String, 如果你使用了mybatis的级联查询(collection标签)，如下：
``` xml
<!--column="{strategyId=id}"表示把当前对象的id属性这个参数赋值给名为strategyId的参数-->
<collection select="strategyRulesListByStrategyId"
                    property="strategyRulesList"
                    column="{strategyId=id}"
                    ofType="com.harmazing.openbridge.monitor.entity.StrategyRules">
</collection>
<!--引用时，要显示的声明上面strategyId属性所在此class名称-->
<select id="strategyRulesListByStrategyId" parameterType="com.harmazing.openbridge.monitor.entity.StrategyRulesRelation" resultMap="strategyRulesMap0">
            SELECT a.*
            FROM t_strategy_rules AS a
            WHERE a.id
            in (
            SELECT rule_id  FROM t_strategy_rules_relation
            WHERE strategy_id= #{strategyId})
</select>
```
其实还有一种写法：
``` xml
<!--将ofType该为当前对象的class，这样Strategy.id已经将数据和类型自动的赋值给strategyId参数-->
<collection select="strategyRulesListByStrategyId"
                    property="strategyRulesList"
                    column="{strategyId=id}"
                    ofType="com.harmazing.openbridge.monitor.entity.Strategy">
</collection>
<!--引用时，strategyId会默认引用上面Strategy.id的类型-->
<select id="strategyRulesListByStrategyId" resultMap="strategyRulesMap0">
            SELECT a.*
            FROM t_strategy_rules AS a
            WHERE a.id
            in (
            SELECT rule_id  FROM t_strategy_rules_relation
            WHERE strategy_id= #{strategyId})
</select>
```

