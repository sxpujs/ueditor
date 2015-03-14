# ueditor
Baidu ueditor对应的java源码做了修改，兼容Spring MVC  

Baidu ueditor源码地址为：https://github.com/fex-team/ueditor. 通过controller.jsp加载config.json与后端交互。
这样的实现无法兼容Spring MVC。因此现在将此源代码修改一下适配Spring MVC。  

新建了两个类com.baidu.ueditor.MyActionEnter和com.baidu.ueditor.MyConfigManager，来分别替换相同包名下的ActionEnter和ConfigManager。

主要的改进点在于将ActionEnter的构造方法 ( HttpServletRequest request, String rootPath )中第二个参数rootPath修改为InputStream，这样在Controller直接传入一个文件输入流即可，不再与config.json文件的路径耦合在一起，相对好一些。
