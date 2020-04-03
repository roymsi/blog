### 搭建自己的博客

#### 只要0元哦

***

#### 教程开始

##### 第一步：注册 Github 账号，[注册地址](https://github.com/join)

输入用户名、邮箱、密码，然后点击验证按钮，在图片中点击左/右旋转图片，直到图片方向为正，点击完成，然后点击 Select a plan。

![sign up](https://github.com/roymsi/blog/raw/master/res/signup.png)

随后选择 个人（团队），计划选择 $0 计划，点击 Choose Free（团队选择 Choose Team for Open Source）

![welcome](https://raw.githubusercontent.com/roymsi/blog/master/res/setup.png)

然后这里随便填，或者直接点 Skip this step。

![welcome](https://raw.githubusercontent.com/roymsi/blog/master/res/verify.png)

在这里点击 Verify email address，然后会自动转跳到 Create a new repository 页面

![welcome](https://raw.githubusercontent.com/roymsi/blog/master/res/new.png)

输入 Repository name ，其他不变，点击 Create repository 创建。

Github账户创建完成，进入下一步

***

##### 第二步：创建 Cloudflare 账户，[注册地址](workers.dev)

![workers sign up](https://raw.githubusercontent.com/roymsi/blog/master/res/cfsignup.png)

点击 Sign up 注册

![cf register](https://raw.githubusercontent.com/roymsi/blog/master/res/cfreg.png)

输入邮箱和密码，点击 Create Account

![cf verify](https://raw.githubusercontent.com/roymsi/blog/master/res/cfverify.png)

点击链接验证邮箱

![cf home](https://raw.githubusercontent.com/roymsi/blog/master/res/cfhome.png)

点击右侧 Workers

![cf create](https://raw.githubusercontent.com/roymsi/blog/master/res/cfcreate.png)

输入子域后点击 设置

![cf plan](https://raw.githubusercontent.com/roymsi/blog/master/res/cfplan.png)

选择 继续使用 Free 计划

![cf new](https://raw.githubusercontent.com/roymsi/blog/master/res/cfnew.png)

点击 创建 Workers

把以下代码复制到页面左侧的编辑框中，修改 github_base 变量为 自己的Github用户名+“/”+创建的Repository name，site_name和site_desc修改为自己想要的，保存三个资源文件到自己的Repository中并修改链接。

[代码](https://raw.githubusercontent.com/roymsi/blog/master/workers.js)

现在打开右侧的预览框，你会看见一个空空如也的首页。

点击 保存并部署 ，点击 返回 ，重命名博客为想要的名称。

***

##### 第三步：编写博客

在前面创建的 Repository 里点击 Create a new file ，命名为 list.json​，输入以下内容，并修改 title 为博客的标题， time 为博客的创建时间，file 里的xxx为任意名字（不要有空格和中文，只有大小写字母和数字）。

由于 json​ 对格式要求很严格，添加时注意缩进和括号、引号、逗号。

```json
[
    {
        "title": "",
        "time": "",
        "file": "/post/xxx.md"
    }
]
```

在 Repository 点击 Create a new file ，在命名时先输入 post/ ，按下回车，再输入前面修改的 xxx.md ，在文件内容里输入想要的内容。

.json 文件语法：[语法](https://www.w3school.com.cn/js/js_json_syntax.asp)

.md 文件编辑器：[Typora](https://www.typora.io/) .md文件语法：[语法](https://www.runoob.com/markdown/md-tutorial.html) 

再打开你刚才重命名的博客，就能看到前面的博客了。

如果打开博客页面为以下错误页面，请检查json格式。
