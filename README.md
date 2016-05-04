# bt_torrent
种子清洗的代码，我已经导成了jar包，可以直接使用，将Bt种子的path和path.utf8的名称转化为随机字符串

#说明
这个jar包，是我参考了elcipse插件还有别人的才写出来的，其中使用的时候将torrent-utils-yellowcong.zip里面的torrent-utils-yellowcong-1.0.jar 弄到项目中，就可以使用了，使用非常简单

#核心代码
TOTorrent torrent = TOTorrentFactory.deserialiseFromBEncodedFile(file,null);<br/>
//获取数据
Map<Object,Object> map  = (Map<Object, Object>) torrent.serialiseToMap();<br/>
			
//通过Bencoder获取我们的字节数据<br/>
byte [] date  = BEncoder.encode(map);<br/>
//创建新文件<br/>
newFile = new File(file.getParent(),UUID.randomUUID().toString()+".torrent");<br/>
//写出数据<br/>
FileOutputStream fos = new FileOutputStream(newFile);<br/>
fos.write(date);<br/>
fos.close();<br/>
	        
	        
#使用方法
@Test<br/>
public void testGetNewBt(){<br/>
	String pathname = "C:\\Users\\yellowcong\\Desktop\\onepice.torrent";<br/>
	//返回文件对象<br/>
	File file = BtUtils.newBt(pathname);<br/>
	System.out.println(file.getPath());<br/>	
}<br/>

#结果
##没有处理
<img src="http://yellowcong.qiniudn.com/BT钱.png"/>
##处理后
<img src="http://yellowcong.qiniudn.com/BT清洗后的.png"/>
