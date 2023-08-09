# Memo

## linux 花屏问题
很可能是内存问题


> wifi: "*\*\*\*\*\*"
>
> password: 8046431**

400+80+335=815
吃饭：335+221=556

**二区：**内蒙古、广西、海南、贵州、云南、西藏、甘肃、青海、宁夏、新疆等10省(区)。

B区院校：

内蒙古：内蒙古大学，广西：广西大学，海南：海南大学，贵州：贵州大学，云南：云南大学，西藏：西藏大学，新疆：新疆大学、石河子大学。全。

## wsl 2
netsh winsock reset

查看wsl:`wsl --list --verbose`
关闭: wsl -t <wslname>
开启: power中 bash

## HMCl

方块传说服务器ip：mcfkcs.com:12345

# EduTest
## AITest的测试结果保存
```C++
int CLogwrite::WriteLogData(IUXLogData* pLogData){

    if (m hwrite == INVALID_HANDLE_VALUE)
        return 0;
    
    int writesize = pLogData->GetBinSize();
    DWORD nWritten;
    if (((m_nIndex + writesize) >= BUFMAX) && (m_nIndex > 0)) {
        ::WriteFile(m_hwrite, m_pBuf, m_nIndex, &nwritten, NULL);
        m_nIndex = 0;
    }
    if(writesize > BUFMAX){
        unsigned char* pdata = (unsigned char*)malloc(writesize);
        pLogData->WriteMemory(pdata);
    
        ::WriteFile(m_hwrite, pdata, writesize, &nwritten， NULL);
        ::free(pdata);
        m_nIndex = 0:
    }
    else {
        pLogData->WriteMemory(m_pBuf + m_nIndex);
        m_nIndex += writesize;
    }
    return writesize;
}
```

## RTDF_View无法读取问题
原因：[Header] 信息没有
### AITest导出结果 [Header]
``` txt
    [Header]
    operator: 
    device_name: devicename
    tester_type: T800
    exec_type: AITest
    exec_version: x32 build-10 [20230105101104]
    program_name: 74AC299_ppz.uxo
    program_version: 2.4.0
    lot_id: logname
    sublot_id: sublotname
    handler_setup: 
    test_code: A
    sites_count: 1
    test_temperature: 
    start_time: 2023/04/23 09:33:11
    end_time: 2023/04/23 09:33:11
    product_group_name: 
    test_center: 
    program_dir: 
    program_path: 
    test_stage: 
    lot_size: 
    qa_enable: 
    low_yield_protect: 
    data_path: 
    upload_path: 
    file_name: 
```
### PwrTest导出结果 [Header]
```txt
    [Header]
    operator: 
    device_name: 
    tester_type: 
    exec_type: 
    exec_version: 
    program_name: 
    program_version: 
    lot_id: 
    sublot_id: 
    handler_setup: 
    test_code:  
    sites_count: 0
    test_temperature: 
    start_time: 1970/01/01 08:00:00
    end_time: 1970/01/01 08:00:00
    product_group_name: 
    test_center: 
    program_dir: 
    program_path: 
    test_stage: 
    lot_size: 
    qa_enable: 
    low_yield_protect: 
    data_path: 
    upload_path: 
    file_name: 
```

原因是PwrTest保存rtdf时只保存了测试结果数据。故用格式转换工具正常，但是rtdf_view无法加载（缺少以上信息）


devenv.exe /Command "File.NewProject" /useenv /project "D:\Al_code" /projecttype "Win32" /language "C++" /template "AITest_Prog"
devenv.exe /Command "File.NewProject" /useenv /project "D:\Al_code\Test" /template "AITest_Prog"
devenv.exe /newproject "D:\Al_code\projectnameTest" /ProjectType C++ /Platform x86

D:\Program Files\Microsoft Visual Studio\2022\Professional\Common7\IDE\devenv.exe

## 需要修改的项目名
C++ WxFlow&UXO .sln .vcxproj .filters .user 





# 论文问题
1. 引用顺序
2. 国内外研究现状 要有参考文献引用
3. 每一章分页符
4. 英文文献 D J M 多类型
5. 英文大小写
6. 图名和图序
7. 代码核心的部分就行
8. 日期
9. 三方面摘要 why how what 
10. 图表要用三线表， 下一页要续表
11. 总结展望 不要第一人称
12. 每一个章节至少两页
13. 两端对齐
14. 公式后边要加公式名顺序

# PwrTest 问题
## rtdf
+ 原因：header信息头不完整


int main() {
    using namespace std;
    int * num_ptr = function1(1,2);
    cout << *num_ptr << " "<< num_ptr[1]<< endl;   // 输出num_prt的内容
    cout << num_ptr << endl;
    // 出内存地处
    delete[] num_ptr;
    return 0;
}
int *function1(int num1, int num2){
    using namespace std;
    int num[]= {num1,num2};
    int *ptr = new int[2];
    for (inti=0;i<2;i++)
        ptr[i]=num[i];
    return ptr;
}

