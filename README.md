# static-hook
作用：
该项目主要提供一种方案，在android编译期实现对java类中的方法注入hook能力，用于控制该方法的真实调用逻辑或者修改里面的参数等等；同时不同于aspectJ需要代码侵入，该项目可以在开发过程中完全无感知；

支持范围：
java类方法，内部类方法，匿名内部类方法，jar包方法，aar包方法；


技术方案：
注解+ASM+AOP

原理:
通过收集注解中标识需要注入的类方法，在android编译过程中，插入自定义的gradle任务，在该任务中完成对类方法的定位，通过ASM字节码修改技术，引入AOP面向切面的方案，插入切面，将方法处理引入切面控制类，最终由注册进入切面控制类的观察者进行真实逻辑处理；
