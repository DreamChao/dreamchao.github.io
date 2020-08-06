如果一个环境是动态的，那么是不是确定性的其实没有多大用处。不确定性与动态性紧密相连， 因此，之前算法可能就是这样，给定环境初试状态的描述，agent可以根据可用的操作及其效果，以及目标状态，将会生成一个计划。 但是，这种规划算法隐含着 agent 执行的环境可能是静态的，除非是通过 agent 的 action 进行了改变。    

the most complex general class of environments are those that are inaccessible, non-deterministic, dynamic, and continuous. Environments that have these properties are often referred to as open。 
因此最复杂的一类环境是那些不可获取的、不确定的、动态的和连续的，具有这些环境的agent 通常称为 open(开放的)   

