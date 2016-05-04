# bt_torrent
种子清洗的代码，我已经导成了jar包，可以直接使用，将Bt种子的path和path.utf8的名称转化为随机字符串

#核心代码
TOTorrent torrent = TOTorrentFactory.deserialiseFromBEncodedFile(file,
					null);
//获取数据
Map<Object,Object> map  = (Map<Object, Object>) torrent.serialiseToMap();
			
//通过Bencoder获取我们的字节数据
byte [] date  = BEncoder.encode(map);
//创建新文件
newFile = new File(file.getParent(),UUID.randomUUID().toString()+".torrent");
//写出数据
FileOutputStream fos = new FileOutputStream(newFile);
fos.write(date);
fos.close();
	        
	        
#使用方法
@Test
	public void testGetNewBt(){
		String pathname = "C:\\Users\\yellowcong\\Desktop\\onepice.torrent";
		//返回文件对象
		File file = BtUtils.newBt(pathname);
		System.out.println(file.getPath());	
	}

#结果
##没有处理
<img src="http://yellowcong.qiniudn.com/BT钱.png"/>
##处理后
<img src="http://yellowcong.qiniudn.com/BT清洗后的.png"/>
