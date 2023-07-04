# DeciLS-PBO
a new local search algorithm for PBO

论文：DeciLS-PBO: an Effective Local Search Method for Pseudo-Boolean Optimization (Frontiers of Computer Science)

运行方式同LS-PBO：

make

./DeciLS-PBO [xxx.wecnf] [cutoff time]


相对于LS-PBO的主要改动：

1.单元传播作为新的初始化-两种新定义的单元子句参与up过程

代码与论文的对应情况：（位于deci.h的assign函数中）
1-of-all generalized unit clause:  即if (clause_sum_lit_weight[c]-clause_max_lit_weight[c] < clause_cardinality[c])
all-of-all generalized unit clause：即 if (clause_sum_lit_weight[c] <= clause_cardinality[c])

2.加入一个对子句的启发式 新的指标care值

代码与论文的对应情况：care值对应pms.h中新加入的数组unsat_count[]，增加一个新的函数update_hardunsatcount()在filp函数中调用以更新每个子句care值。新的启发式Care-FC scheme的代码位于pms.h，在pick_var函数中做了相应更改。

进一步调参与后续优化正在进行中...

论文更多细节详见：https://arxiv.org/abs/2301.12251

引用本文：

Luyu JIANG, Dantong OUYANG, Qi ZHANG, Liming ZHANG. DeciLS-PBO: an Effective Local Search Method for Pseudo-Boolean Optimization. Front. Comput. Sci., https://doi.org/10.1007/s11704-023-3018-8
