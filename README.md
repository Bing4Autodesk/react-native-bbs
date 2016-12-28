# React Native V0.37
>版本号：0.37<br>
>开始日期：2016.10.10<br>
>每天一个组件/API,附带Demo(Code区注释不能少)<br>
>💗💗💗💗

####微信公众号：Domeday
![](https://raw.githubusercontent.com/TrustTheBoy/imagesGithub/master/WeChat/publick/WeChatCode.jpg)

##React Native BBS目录结构区/Dome标记区

## 项目过程中遇到的 RN 初级问题记录区

#### React Native平台适配:
	1.Android中图片放在android\app\src\main\res下(文件夹名:drawable-xxhdpi),并且图片名都是小写
	2.Ios中进入ios\MobileCampus\下,删除Images.xcassets文件夹下的东西,复制你的图片
#### 使用Navigator跳转下一页时的切换特效:
切换时body需要设置backgroundColor/flex,没有backgroundColor/flex时切换时可以看见切换前的页面渐隐效果,体验不好

	例如:View style={{flex:1,backgroundColor:'#fff'}}
	
####<font style="">react native USB真机调试报错</font>
#####<font style="color:red">error:</font>
>FAILURE: Build failed with an exception.<br>
What went wrong:<br>
 Execution failed for task ' : app:installDebug'.<br>
 com.android.builder.testing.api.DeviceException: com.android.ddmlib.InstallException: Unable to upload some APKs

解决方法: [USB调试真机调试>>](http://csbun.github.io/blog/2015/12/starting-react-native-with-android/)

####解决安卓多个真机调试报错问题:
	Debug模式多台真机调试,没换一次手机,都需要给手机重新下载配置文件

####React Native Reload不更新
	解决方案:
	例如:E:\Study\node_modules\react-native\packager\react-packager\src\node-haste\FileWatcher\index.js
<font style="color:green;font-weight：bold;font-size:18;">找到并更改为:</font>
<pre><div style="display:inline-block;marginBottom:50px;height:30px;">const MAX_WAIT_TIME = 360000;</div>
_createWatcher(rootConfig) {
    const watcher = new WatcherClass(rootConfig.dir, {
      glob: rootConfig.globs,
      dot: false,
    });
    return new Promise((resolve, reject) => {
      const rejectTimeout = setTimeout(
        () => reject(new Error([
            'Watcher took too long to load',
            'Try running `watchman version` from your terminal',
            'https://facebook.github.io/watchman/docs/troubleshooting.html',
          ].join('\n'))),
        MAX_WAIT_TIME
      );
      watcher.once('ready', () => {
        clearTimeout(rejectTimeout);
        resolve(watcher);
      });
    });
  }
</pre> 
####listView组件更新机制:[Github](https://github.com/changfuguo/react-native/blob/master/listview.md);
####ListView不滑动问题
	解决方法：listview自身和它的父容器都要加flex：1,哪层断了都不行

	相关解决方法:[stackoverflow](http://stackoverflow.com/questions/32874559/listview-fails-to-scroll);

####JPush-react-native:极光推送
>测试时推送建议消息：建议集成SDK时加上统计代码以评估推送效果;
  
#####解决方式按照提示内容找到

>X:xxx porject\node_modules\react-native\local-cli\link\__fixtures__\android\0.17\下的MainActivity.java文件，
搜索onPesume()，在此方法中加入:JPushInterface.onResume();就不会推送显示此消息

####JPush-react-native:react-native run-android报错：Unknown named module: jpush-react-native'
	rnpm link jpush-react-native 导入模块时出了问题
	
>相关issue提问：[@jpush-react-native:107](https://github.com/jpush/jpush-react-native/issues/107)
