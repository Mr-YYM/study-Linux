# iptables

## table

> The `iptables` firewall uses **tables** to organize its rules. These tables classify rules according to the type of decisions they are used to make. For instance, if a rule deals with **network address translation**, it will be put into the `nat` table. If the rule is used to decide **whether to allow the packet to continue to its destination**, it would probably be added to the `filter` table.

使用不同的表组织各种相似的规则

- filter：对数据包进行过滤，根据规则决定是否放心网络包
- NAT：网络地址转换
- mangle：
- raw：

各表匹配顺序：raw -> mangle -> NAT -> filter

## Chain

> Within each `iptables` table, rules are further organized within separate “chains”. While tables are defined by the general aim of the rules they hold, the built-in chains represent the `netfilter` hooks which trigger them. Chains basically determine *when* rules will be evaluated.

链促发规则（表）的执行，链决定了规则什么时候会被执行。

