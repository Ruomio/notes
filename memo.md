# Memo

> wifi: "*\*\*\*\*\*"
>
> password: 8046431**

400+80+335=815
吃饭：335+221=556

**二区：**内蒙古、广西、海南、贵州、云南、西藏、甘肃、青海、宁夏、新疆等10省(区)。

B区院校：

内蒙古：内蒙古大学，广西：广西大学，海南：海南大学，贵州：贵州大学，云南：云南大学，西藏：西藏大学，新疆：新疆大学、石河子大学。全。



## HMCl

方块传说服务器ip：mcfkcs.com:12345


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
