中断向量与非中断向量
X86 - 有中断向量
ARM - 没有中断向量

中断ISR top half 调用disable_irq() 屏蔽中断控制器（GIC）中断响应。  
中断ISR bottom half 调用enable_irq() 使能中断控制器中断（GIC）响应。

disable_irq_nosync() 与 disable_irq()的区别：
- disable_irq_nosync() 立即disable
- disable_irq() 等待执行完再disable， 不能在同一个中断中执行，否则会死锁， 例如， 在5号中断ISR调用 disable_irq(5).