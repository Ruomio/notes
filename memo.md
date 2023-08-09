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


# Last Error
Aug 09 11:42:43 Archlinux kernel: pcieport 0000:00:1d.4: AER: Corrected error received: 0000:00:1d.4
Aug 09 11:42:43 Archlinux kernel: pcieport 0000:00:1d.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Aug 09 11:42:43 Archlinux kernel: pcieport 0000:00:1d.4:   device [8086:a334] error status/mask=00000001/00000000
Aug 09 11:42:43 Archlinux kernel: pcieport 0000:00:1d.4:    [ 0] RxErr                  (First)
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: wlp7s0: Trying to associate with fc:73:fb:62:72:d0 (SSID='TBStest_guest' freq=5300 MHz)
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.1064] device (wlp7s0): supplicant interface state: scanning -> associating
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: wlp7s0: Associated with fc:73:fb:62:72:d0
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: wlp7s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.2707] device (wlp7s0): supplicant interface state: associating -> 4way_handshake
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: wlp7s0: WPA: Key negotiation completed with fc:73:fb:62:72:d0 [PTK=CCMP GTK=CCMP]
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: wlp7s0: CTRL-EVENT-CONNECTED - Connection to fc:73:fb:62:72:d0 completed [id=0 id_str=]
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: bgscan simple: Failed to enable signal strength monitoring
Aug 09 11:42:46 Archlinux dhcpcd[538]: wlp7s0: carrier acquired
Aug 09 11:42:46 Archlinux kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0: link becomes ready
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.2772] device (wlp7s0): supplicant interface state: 4way_handshake -> completed
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.2773] device (wlp7s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful. Connected to wireless network "TBStest_guest"
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.2776] device (wlp7s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.2785] dhcp4 (wlp7s0): activation: beginning transaction (timeout in 45 seconds)
Aug 09 11:42:46 Archlinux dhcpcd[538]: wlp7s0: IAID 68:67:5c:6d
Aug 09 11:42:46 Archlinux dhcpcd[538]: wlp7s0: adding address fe80::3059:c223:b0a:5bab
Aug 09 11:42:46 Archlinux wpa_supplicant[657]: wlp7s0: WPA: Group rekeying completed with fc:73:fb:62:72:d0 [GTK=CCMP]
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3033] dhcp4 (wlp7s0): state changed new lease, address=10.8.74.156
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3036] policy: set 'TBStest_guest' (wlp7s0) as default for IPv4 routing and DNS
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3256] device (wlp7s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3269] device (wlp7s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3270] device (wlp7s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3272] manager: NetworkManager state is now CONNECTED_SITE
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.3275] device (wlp7s0): Activation: successful, device activated.
Aug 09 11:42:46 Archlinux dhcpcd[538]: wlp7s0: soliciting a DHCP lease
Aug 09 11:42:46 Archlinux NetworkManager[566]: <info>  [1691552566.9529] manager: NetworkManager state is now CONNECTED_GLOBAL
Aug 09 11:42:47 Archlinux dhcpcd[538]: wlp7s0: soliciting an IPv6 router
Aug 09 11:42:50 Archlinux systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Aug 09 11:42:59 Archlinux dhcpcd[538]: wlp7s0: no IPv6 Routers available
Aug 09 11:43:12 Archlinux kernel: pcieport 0000:00:1d.4: AER: Multiple Corrected error received: 0000:00:1d.4
Aug 09 11:43:12 Archlinux kernel: pcieport 0000:00:1d.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Transmitter ID)
Aug 09 11:43:12 Archlinux kernel: pcieport 0000:00:1d.4:   device [8086:a334] error status/mask=00001001/00000000
Aug 09 11:43:12 Archlinux kernel: pcieport 0000:00:1d.4:    [ 0] RxErr                  (First)
Aug 09 11:43:12 Archlinux kernel: pcieport 0000:00:1d.4:    [12] Timeout
Aug 09 11:43:29 Archlinux kernel: pcieport 0000:00:1d.4: AER: Multiple Corrected error received: 0000:00:1d.4
Aug 09 11:43:29 Archlinux kernel: pcieport 0000:00:1d.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Transmitter ID)
Aug 09 11:43:29 Archlinux kernel: pcieport 0000:00:1d.4:   device [8086:a334] error status/mask=00001001/00000000
Aug 09 11:43:29 Archlinux kernel: pcieport 0000:00:1d.4:    [ 0] RxErr                  (First)
Aug 09 11:43:29 Archlinux kernel: pcieport 0000:00:1d.4:    [12] Timeout

