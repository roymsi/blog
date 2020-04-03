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

```javascript
/**
 *
 *  TWSP Blog
 *
 *  https://github.com/roymsi/blog
 *
 */

// 定义 Github 项目，文章会从这里读取
const github_base = "roymsi/blog";

// 站点名称
const site_name = "TWSP Blog (by CloudFlare Workers)";

// 站点介绍
const site_desc = "TWSP (TecWeb Software Project) 官方博客";

// 资源文件
const highlight_css = "https://raw.githubusercontent.com/roymsi/blog/master/github.css";
const highlight_pack = "https://github.com/roymsi/blog/blob/master/highlight.pack.js";
const highlight_main = "https://raw.githubusercontent.com/roymsi/blog/master/highlight.min.js";

// Copyright
const copyright = `&copy; 2020 ${site_name} | <a href="https://github.com/roymsi/blog" target="_blank">Github</a>`;

/* 配置到此结束 */

addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

var header = `
<html>
	<head>
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
		<meta http-equiv="X-UA-Compatible" content="IE=11">
		<meta name="application-name" content="${site_name}">
		<meta name="msapplication-TileColor" content="#F1F1F1">
		<meta name="description" content="${site_desc}">
		<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" crossorigin="anonymous">
		<link rel="stylesheet" href="https://netdna.bootstrapcdn.com/font-awesome/4.6.0/css/font-awesome.min.css">
		<link rel="stylesheet" href="${highlight_css}">
		<title>${site_name}</title>
		<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
		<script src="https://cdnjs.cloudflare.com/ajax/libs/showdown/1.9.0/showdown.min.js" type="text/javascript"></script>
		<script src="https://cdn.jsdelivr.net/npm/showdown-table@1.0.1/dist/showdown-table.min.js" type="text/javascript"></script>
		<script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" crossorigin="anonymous"></script>
		<script src="${highlight_main}"></script>
		<script src="${highlight_pack}"></script>
		<style type="text/css">.post-a {color: #000;text-decoration: none ! important;}.post-box {padding: 12px 20px 12px 20px;border-bottom: 1px solid rgba(0,0,0,0.07);cursor: pointer;border-left: 0px solid rgba(66, 66, 66, 0);transition-duration: 0.3s;}.post-box:hover {transition-duration: 0.3s;border-left: 5px solid rgba(66, 66, 66, 0.15);}.thread h2 {border-bottom: 1px solid rgb(238,238,238);padding-bottom: 10px;}.editor-preview pre, .editor-preview-side pre{padding: 0.5em;}.hljs{background: unset ! important;padding: 0px;}.CodeMirror{height: calc(100% - 320px);min-height: 360px;}.msgid{font-family:Consolas;}.tooltip {word-break: break-all;}h2 a{font-weight: 400;}body{font-family: '-apple-system','BlinkMacSystemFont','Segoe UI','Helvetica','Arial','sans-serif','Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol' ! important;font-weight: 400;}h2 a{color: #000;} h2 a:hover{color: #000; text-decoration: none;}.full-width{width: 100%;}.thread img{vertical-align:text-bottom ! important;max-width:100% ! important;margin-top:8px;margin-bottom:8px;}.thread table{display:block;width:100%;overflow:auto;margin-bottom:8px;}.thread table tr{background-color:#fff;border-top:1px solid #c6cbd1;}.thread table tr:nth-child(2n){background-color:#f6f8fa;}.thread table th,.thread table td{padding:6px 13px;border:1px solid #dfe2e5;font-size:14px;}.thread pre{margin-bottom:16px;}pre{border:none ! important;}blockquote{font-size:15px ! important;}</style>
	</head>
  <body>
    <div class="container">
      <div class="row">
        <div class="col-sm-2"></div>
        <div class="col-sm-8">
          <h2><a href="/" class="post-a">${site_name}</a></h2>
          <p>${site_desc}</p>
          <hr>
          <div class="thread">
`;

function getRequestParams(str) {
  var index = str.indexOf("?");
  str = str.substring(index + 1, str.length);
  console.log(str);
  if(typeof(str) == "string"){
      u = str.split("&");
      var get = {};
      for(var i in u){
          var j = u[i].split("=");
          get[j[0]] = j[1];
      }
      return get;
  } else {
      return {};
  }
}

async function bloghandle(request) {
  var $_GET = getRequestParams(request.url);
  var data = header;
  if($_GET['p'] == undefined) {
    var url = "https://raw.githubusercontent.com/" + github_base + "/master/list.json";
    const init = {
      method: "GET"
    };
    const response = await fetch(url, init);
    var resptxt = await response.text();
    var json = JSON.parse(resptxt);
    console.log(json);
    data += `<p>所有文章</p>`;
    for(var i = 0;i <= json.length;i++) {
      try {
        var filename = encodeURIComponent(json[i].file.replace(/"/g, ""));
        var time = json[i].time;
        var title = json[i].title;
        data += `<a href="?p=${filename}" class="post-a">
						<div class="post-box">
							<h4>${title}</h4>
							<p>发表于 ${time}</p>
						</div>
					</a>`;
      } catch(e) {
        // 收声
      }
    }
    if(json.length == 0) {
      data += `<p><blockquote>暂时没有文章！</blockquote></p>`
    }
    data += `
            <br>
            <p class="text-right">${copyright}</p>
          </div>
    `;
  } else {
    data += `
          </div>
          <script type="text/javascript">
            var textcontent = \`
`;
    var url = "https://raw.githubusercontent.com/" + github_base + "/master/" + $_GET['p'];
    const init = {
      method: "GET"
    };
    const response = await fetch(url, init);
    if(response.status == 200) {
      var resptxt = await response.text();
      data += resptxt.replace(/`/g, "\\`");
    } else {
      data += `
### Erroe 404 Blog Not Found
您所访问的文章不存在。      
`;
    }
    data += `
            \`;
          </script>
          <hr>
          <p class="text-right">${copyright}</p>
    `;
  }
  data += `
        </div>
      </div>
    </div>
    <script type="text/javascript">
      hljs.initHighlightingOnLoad();//对 hljs 进行初始化
      var md = new showdown.Converter({extensions: ['table']}); // 引入 showdown 并加载 table 插件
      md.setOption('simplifiedAutoLink', true); // 自动识别链接
      md.setOption('simpleLineBreaks', true); // 自动换行
      md.setOption('openLinksInNewWindow', true); // 新标签页打开链接
      window.onload = function() {
        $(".thread").html(md.makeHtml(textcontent));
        document.querySelectorAll('pre code').forEach(function(e) {
          hljs.highlightBlock(e);//渲染代码块，执行高亮操作
        });
      }
    </script>
  </body>
</html>
`;
  return data;
}

/**
 * Respond to the request
 * @param {Request} request
 */
async function handleRequest(request) {
  var resp = new Response(await bloghandle(request), {"Content-type": "text/html;charset=UTF-8", status: 200});
  resp.headers.set("Content-Type", "text/html");
  return resp;
}

```

现在打开右侧的预览框，你会看见一个空空如也的首页。

点击 保存并部署 ，点击 返回 ，重命名博客为想要的名称。

***
