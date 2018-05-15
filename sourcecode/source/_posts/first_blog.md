---
title: 第一篇博文
date: 2018-5-12 16:49
categories:
- 日常
- C++
tags:
- 自学
- 心情
- C++
---
刚刚学会用hexo搭建网站 来写第一篇博文 激励自己以后再实践中多多记录下自己遇到的困难 希望往后的自己能不断吸收大牛的经验 整理总结实践中遇到的问题对应的得到的解决方法 并根据自己的兴趣多多看书 多敲代码

{% codeblock lang:C 使用 CFile 的子类 CStdioFile 的注意事项 %}
CString strPath;
CString strRead;
TCHAR PathPro[256] = {0};
GetCurrentDirectoryW(256,PathPro);				//PathPro: current dir path
strPath = CString(PathPro)+_T("\\") + SCRIPT_FILE_NAME;         //SCRIPT_FILE_NAME: "User_Script.txt"

CStdioFile f;  
CFileException e;  
if(!f.Open(strPath,CFile::modeRead) )
	return FALSE;  
while(f.ReadString(strRead))	//如果文件未读完，返回true，否则返回false。
{
	CString strTemp;
	strTemp.Format(_T("%s\n"),strRead);    //检测是否成功读出每行数据
	LogToFiles(strTemp,0);
}
f.Close();
{% endcodeblock %}