开发环境：
  【1】Web服务器：Tomcat7.0
  【2】jdk：1.8
  【3】开发工具：Eclipse
  【4】数据库：MySQL5.8
  【5】项目搭建：Maven
  【6】框架使用：Spring、SpringMVC、MyBatis、Log4j
  【7】前端界面：Jquery、Bootstrap
  
 功能模块：
  【1】用户登录
        用户登录过程首先要验证用户名和密码是否正确，如果正确，可以登录系统，反之，则在登录界面给出错误提示信息
  【2】用户登录拦截器
        创建一个拦截器类并实现 HandlerInterceptor 接口，首先通过 preHandle() 方法获取用户 URL 请求，然后通过请求判断是否为用户登录，只有对用户登录的请求才不进行拦截，之后获取 Session 对象及其所带的用户信息，若 Session 中的用户信息不为空则表示用户已经登录，不进行拦截，反之系统将会转发登录界面，并提示用户登录
  【3】用户登出
        用户通过点击按钮的时候，会提交登出的请求，通过在 Controller 中所编写的退出登录方法，清除 Session 中的用户信息并在退出登录后返回到登录界面
  【4】客户管理
        客户管理是系统的核心部分，该模块实现了对客户的查询、添加、修改和删除功能
        ① 查询：
              分为条件查询和分页查询，条件查询是根据客户姓名、来源、所属行业、级别等相关条件进行查询，通过表单提交所需要的条件，传到 Controller 类中作条件查询，若存在将该用户的信息封装成对象传回页面，使用JSTL标签进行遍历。分页查询则是通过分页组件将所有的客户信息传回界面进行遍历。
        ② 添加：
              添加功能由弹出窗口实现，通过表单提交相关填写的客户信息，点击提交按钮传回 Controller 类中，通过 @ResponseBody 注解和 HttpMessageConverter转换为json格式直接写入Response对象中，后通过相关方法达到实现客户添加功能
        ③ 修改：
              修改功能也是由弹出窗口实现，首先获取获取该用户的所有信息，并显示到修改信息的窗口上，通过 Ajax 的方式获取所需要修改的客户信息，后台主要通过客户的 id 来获取客户信息和更新客户信息
        ④ 删除：
              删除功能会通过 Ajax 的方式发送一个删除的请求，该请求会将所要删除的客户 id 传入到后台处理方法中，通过数据库中所受影响的行数来判断是否删除成功
    
