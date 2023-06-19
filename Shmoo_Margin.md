# Shmoo

## 代码解释

### ShmooControl.h

```markdown
该代码定义了一个名为CShmooControl的类，该类是从CWnd类派生而来的，用于创建一个绘制图形的控件。

代码中的主要成员函数包括：

Create：创建控件并指定其样式、位置等属性。
CalRange：计算绘制图形的范围。
Reset：重置控件的状态。
GetXMarkValue、GetYMarkValue、GetZMarkValue：根据给定的数值返回相应的字符串表示。
DrawBackground：绘制控件的背景。
DrawAxis：绘制坐标轴。
DrawShmooContent：绘制Shmoo内容。
DrawSearchContent：绘制搜索内容。
DrawCurrentSearchResult：绘制当前搜索结果。
DrawProgrammedValue：绘制已编程的值。
ClearData：清除数据。
StoreAssumeData、StoreData：存储数据。
Save：保存数据到文件。
Print：打印数据。
ReDraw：重新绘制控件。
SelectDut：选择DUT（Device Under Test）。
SetMergeMode：设置合并模式。
SetUnit：设置单位。
SetPlotType：设置绘图类型。
GetPlotType：获取绘图类型。
PreSubclassWindow：在子窗口创建前执行的操作。
析构函数。
该类还包含一些成员变量，用于存储控件的状态和数据。其中包括绘制所需的各种参数和选项，以及存储的数据结构。

此外，代码还定义了一些消息处理函数，用于处理控件的各种事件，如绘制、鼠标操作等。

整体上，该代码实现了一个用于绘制图形的自定义控件，并提供了一系列功能用于操作和显示数据。
```

### ShmooControl.cpp

```markdowm
这段代码是一个ShmooControl类的实现。该类是一个自定义的控件，用于显示Shmoo图形。

代码的功能包括：

定义了一些颜色常量，如NOTEST_BRUSH、ASSUME_FAIL_BRUSH等。

定义了一个名为"round"的内联函数，用于将浮点数四舍五入为整数。

实现了CShmooControl类的构造函数和析构函数。

实现了RegisterWindowClass()函数，用于注册窗口类。

定义了消息映射表，包括对窗口绘制、擦除背景、大小变化和鼠标事件的处理函数。

实现了OnEraseBkgnd()函数，用于处理擦除背景的消息。

实现了PreSubclassWindow()函数，用于在子类化窗口之前执行一些操作。

实现了Create()函数，用于创建控件。

实现了OnPaint()函数，用于处理绘制消息。

实现了CalRange()函数，用于计算绘图范围。

实现了OnSize()函数，用于处理窗口大小变化的消息。

实现了ReDraw()函数，用于重新绘制控件。

实现了Reset()函数，用于重置控件。

实现了SelectDut()函数，用于选择测试器件。

实现了一些辅助函数，如GetXMarkValue()、GetYMarkValue()和GetZMarkValue()，用于获取坐标轴上的刻度值。

实现了DrawBackground()函数，用于绘制控件的背景。

实现了DrawAxis()函数，用于绘制坐标轴。

函数DrawProgrammedValue用于绘制一个编程值（programmed value）。函数接受一个CDC（Device Context）对象指针pDC和一个布尔值bProcess作为参数。首先，根据给定的范围和网格大小计算x和y的间隔。然后，根据原始的x和y值计算出对应的索引xindex和yindex，如果索引越界，则直接返回。接下来，根据bProcess的值选择绘制的样式：如果为真，则使用黑色画笔和无刷子（填充颜色为空），绘制一个椭圆形；如果为假，则使用白色画笔和无刷子，绘制一个椭圆形。最后，将画笔设置为无画笔状态。

函数DrawShmooContent用于绘制Shmoo图的内容。首先检查网站数量是否为0，如果是则直接返回。然后根据是否处于合并模式进行相应的处理。如果处于合并模式，首先计算合并数据，然后检查网格大小和合并结果的大小是否匹配，如果不匹配则返回。接下来创建字体和画笔对象，设置文本颜色和背景模式。然后遍历每个网格，并根据合并结果的值设置相应的颜色，绘制矩形和文本。最后恢复原来的字体对象。

函数DrawSearchContent用于绘制搜索图的内容。首先检查网格大小和所选DUT的范围，如果不满足条件则直接返回。然后根据序列类型选择相应的绘制方式。如果是X-First类型，则遍历每个数据点，根据原点的位置计算坐标，并根据左右结果的值选择相应的颜色，绘制矩形。如果是Y-First类型，则也是类似的操作，只是计算坐标的方式不同。



函数DrawSearchContent用于绘制搜索内容，接收一个CDC*类型的指针参数pDC，表示绘图设备的上下文。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，m_SelDut在有效范围内），则执行绘图操作。否则，函数提前返回。

接下来，定义了一些用于绘制图形的画刷（CBrush）对象，分别代表通过（brPass）、失败（brFail）、绿色（brGreen）和红色（brRed）。

根据条件判断和计算，使用SelectObject方法选择不同的画刷对象，并调用Rectangle方法绘制矩形图形。具体绘制的形状和颜色根据不同的条件分支来确定。

函数DrawCurrentSearchResult用于绘制当前的搜索结果，接收一个DBL_POING类型的引用参数dbl_point，表示搜索结果的坐标和状态。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，m_SelDut在有效范围内），则执行绘图操作。否则，函数提前返回。

与上一个函数类似，根据条件判断和计算，使用SelectObject方法选择不同的画刷对象，并调用Rectangle方法绘制矩形图形。

函数CalculateMergeData用于计算合并后的数据。

首先创建了一个大小为m_nX*m_nY的整型向量m_vMergeResult，并初始化所有元素为0。

然后，通过遍历m_dblPoint中的数据，根据条件进行计数操作，将计数结果存储在m_vMergeResult中。

函数StoreAssumeData用于存储假设数据。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，坐标在有效范围内），则执行数据存储和绘图操作。

根据传入的数据参数和循环遍历的当前位置，创建一个SHMOODATA对象shm，并设置其坐标和结果。

接着，根据m_dut数组的位运算，判断当前位置的m_Data中的数据是否需要存储。

根据数据的结果值，选择合适的画刷对象，并使用SelectObject方法选择画刷对象，绘制矩形图形。

函数StoreData用于存储数据。

首先进行一些判断，如果满足条件（m_nX和m_nY都不为0，坐标在有效范围内，并且传入.

Print()函数用于打印Shmoo图形，它的主要步骤如下：

创建字体对象并设置字体属性。
创建打印对话框，并显示对话框，获取打印设备上下文（hDC）。
如果打印设备上下文不存在，则返回。
创建设备上下文对象（CDC）并将其附加到打印设备上下文。
开始打印文档，并开始打印页面。
选择之前创建的字体对象。
设置地图模式和窗口、视口的大小。
根据绘图类型（m_PlotType）选择绘制Shmoo内容或搜索内容。
绘制编程值。
恢复原始字体对象。
结束打印页面和文档。
释放设备上下文对象。
分离设备上下文和打印设备上下文。
删除设备上下文对象。
OnShmoo()函数是一个消息处理函数，用于处理Shmoo消息。它接收WPARAM和LPARAM参数，其中WPARAM参数传递了一个指向数据的指针，LPARAM参数没有使用。函数根据消息的类型执行不同的操作，包括错误消息、全局变量、范围、Shmoo数据、结束Shmoo、假设结果、旧的xy值、单元定义和保存结果文件等。

具体的操作包括：

错误消息：通过SendMessage发送错误消息给主窗口。
全局变量：从字符串中解析出各种全局变量的值。
范围：解析字符串并清除数据，设置新的范围，并调用CalRange()、Reset()和Invalidate()进行重新绘制。
Shmoo数据：将数据存储到内部数据结构中，并调用DrawProgrammedValue()和Invalidate()重新绘制。
结束Shmoo：重新绘制并发送消息给父窗口和主窗口。
假设结果：将假设数据存储到内部数据结构中。
旧的xy值：从字符串中解析出原始xy值，并重新绘制。
单元定义：从字符串中解析出xstop和ystop，并调用SetUnit()设置单位。
保存结果文件：将结果保存到文件。
其他消息类型：不执行任何操作。
这些函数是CShmooControl类的成员函数，用于处理Shmoo图形控件的打印和消息处理相关的功能。

OnLButtonDown：鼠标左键按下事件处理函数。根据鼠标点击的位置计算出对应的数据点的索引，并根据当前的显示模式（PF mode、Fail Count、Fail Address）设置要显示的信息，并在窗口上绘制出对应的文本。
OnLButtonUp：鼠标左键释放事件处理函数。根据鼠标释放的位置确定选择的数据点的索引。
OnMouseMove：鼠标移动事件处理函数。根据鼠标的移动绘制出一个矩形框，并在窗口上绘制出该矩形框。
OnMenuShmoo：响应菜单项"Shmoo"的函数。向父窗口发送一个自定义消息UWM_MENU_SHMOO。
SetUnit：设置单位函数。根据传入的字符串参数设置X轴、Y轴、Z轴的单位。
OnRButtonDown：鼠标右键按下事件处理函数。根据鼠标点击的位置显示一个设置菜单。
OnSettingProgramPoint：响应设置菜单中的"Setting"菜单项的函数。根据点击的位置确定选择的数据点的索引，并根据该索引设置新的数据点的值。
SetPlotType：设置绘图类型的函数。传入一个整数参数来设置绘图类型。
GetPlotType：获取当前绘图类型的函数。返回一个整数值表示当前的绘图类型。
make_search_test_data：生成搜索测试数据的函数。可能是用于生成一些测试数据以进行搜索相关的功能测试。
```

### ShmooExecDlg.h

```markdown
该代码定义了一个名为CShmooExecDlg的对话框类，它是从CDialog类派生而来的。

代码中的主要成员函数包括：

构造函数 CShmooExecDlg：用于创建对话框实例，并初始化一些成员变量。
析构函数 ~CShmooExecDlg：用于清理资源。
DoDataExchange：用于数据的传递和验证。
OnInitDialog：对话框初始化的处理函数。
OnBnClickedOk：当用户单击对话框上的确定按钮时触发的处理函数。
OnBnClickedButtonMdut07、OnBnClickedButtonMdut815、OnBnClickedButtonMdut1623、OnBnClickedButtonMdut2431：当用户单击相应的按钮时触发的处理函数。
OnBnClickedCheckDut1：当用户勾选或取消勾选DUT 1时触发的处理函数。
该类还包含一些成员变量，用于存储对话框的状态和数据。其中包括：

m_nTestDUT：存储测试DUT的数组。
m_strMeasSignal：存储测量信号的字符串。
m_bStepByStep：表示是否逐步执行的布尔值。
m_nAlgorythm：存储算法的整数值。
此外，代码还定义了一些消息映射函数，用于处理对话框中的控件事件，如按钮点击和复选框勾选等。

总体而言，该代码实现了一个用于显示和设置Shmoo执行参数的对话框，包含了一些按钮、复选框和文本框等控件，用于与用户交互获取参数。

```

### ShmooExecDlg.cpp

```markdowm
这段代码是实现了 CShmooExecDlg 类的成员函数的定义，包括构造函数、析构函数、数据交换函数和消息映射函数。

构造函数 CShmooExecDlg::CShmooExecDlg 初始化了类的成员变量 m_nAlgorythm、m_strMeasSignal 和 m_bStepByStep。

数据交换函数 CShmooExecDlg::DoDataExchange 使用宏 DDX_Text 和 DDX_Check 将对话框上的文本框和复选框控件与类的成员变量进行关联。

消息映射函数 BEGIN_MESSAGE_MAP 和 ON_BN_CLICKED 定义了对话框中控件事件的响应函数，包括按钮点击事件和复选框勾选事件。

函数 CShmooExecDlg::OnInitDialog 在对话框初始化时被调用，根据条件设置对话框上的控件状态。根据变量 IS_JOBLOADED 的值，如果已加载作业，会根据 gxShared->TotalSite 的值来设置对应的复选框和按钮的状态。

函数 CShmooExecDlg::OnBnClickedButtonMdut07、OnBnClickedButtonMdut815、OnBnClickedButtonMdut1623、OnBnClickedButtonMdut2431 分别响应对应按钮的点击事件，根据 m_nAlgorythm 的值对一组复选框进行勾选或取消勾选。

函数 CShmooExecDlg::OnBnClickedOk 响应确定按钮的点击事件，将对话框中的选中状态更新到 m_nTestDUT 数组中，然后调用 OnOK 函数。

函数 CShmooExecDlg::OnBnClickedCheckDut1 响应复选框勾选事件，根据选中的复选框的ID，将其他复选框的勾选状态取消，并将当前复选框勾选。

这些函数的具体实现逻辑根据业务需求和对话框中控件的交互逻辑而定，上述代码片段提供了对这些函数的框架和大致思路的理解。
```

### ShmooWindow.h

```markdown
这段代码定义了一个名为 CShmooWindow 的类，该类是从 CWindowDialog 类派生而来，并包含了一些成员变量和函数。

CShmooWindow 类的构造函数和析构函数用于创建和销毁对象。

CShmooWindow 类包含了许多成员函数，用于实现各种功能，例如连接和断开连接、调整控件大小、加载和卸载页面、暂停页面、启用和禁用项目等。这些函数根据具体的业务需求来实现对话框的交互逻辑。

CShmooWindow 类的私有成员变量包括布尔型变量 m_bAlwaysOnTop 和图标句柄 m_hIcon，以及其他用于存储设置数据的变量。

CShmooWindow 类还定义了一些私有函数，用于读取和保存轴设置信息、将数据转换为参数形式、设置不同的模式等。

CShmooWindow 类还包含一些消息响应函数，例如窗口命令、绘图、鼠标拖动图标等。这些函数根据消息的类型和具体需求来实现相应的功能。

最后，CShmooWindow 类的消息映射函数 DECLARE_MESSAGE_MAP 声明了该类的消息映射表，用于将消息与相应的消息处理函数关联起来。

总体而言，这段代码定义了一个用于控制 Shmoo 窗口的类 CShmooWindow，其中包含了与窗口交互、控件操作、消息处理等相关的函数和成员变量。
```

### ShmooWindow.cpp

```markdown
#include：包含所需的头文件。
IMPLEMENT_DYNAMIC：用于实现动态创建对话框类的宏。
CShmooWindow::CShmooWindow：构造函数，用于初始化成员变量。
CShmooWindow::~CShmooWindow：析构函数。
CShmooWindow::DoDataExchange：用于在对话框和成员变量之间进行数据交换。
CShmooWindow::OnInitDialog：初始化对话框，包括设置图标、工具栏、菜单、控件等。
CShmooWindow::OnDestroy：对话框销毁时的处理，包括保存对话框位置。
CShmooWindow::OnSysCommand：处理系统菜单命令，包括处理"Always on top"选项。
CShmooWindow::OnPaint：绘制对话框。
CShmooWindow::OnQueryDragIcon：获取拖动对话框时的光标图标。
CShmooWindow::PreTranslateMessage：在消息被翻译并分派之前的预处理，用于处理按键消息。
CShmooWindow::OnSize：处理对话框大小改变事件，调整控件大小。
CShmooWindow::PostNcDestroy：在窗口销毁后的处理，发送消息给父窗口。
CShmooWindow::OnSetFocus：处理对话框获取焦点事件。
CShmooWindow::OnClose：关闭对话框的处理，保存对话框状态。
CShmooWindow::ResizeControls：调整控件的大小和位置。
CShmooWindow::Connect：连接到GUI。
CShmooWindow::Disconnect：断开与GUI的连接。
CShmooWindow::LoadedPage：加载页面时的处理。
CShmooWindow::UnloadedPage：卸载页面时的处理。
CShmooWindow::PausedPage：暂停页面时的处理。
CShmooWindow::OnUpdateAlwaysOnTop：更新"Always on top"菜单项的状态。
CShmooWindow::OnUpdatePlotShmoo：更新"Plot Shmoo"按钮的状态。
CShmooWindow::OnUpdateStopShmoo：更新"Stop Shmoo"按钮的状态。
CShmooWindow::OnAlwaysOnTop：处理"Always on top"菜单项的点击事件，切换窗口置顶状态。
OnBnClickedButtonPrint(): 在点击“打印”按钮时调用m_Shmoo对象的Print()方法。m_Shmoo是该窗口类的成员变量。

OnBnClickedButtonSave(): 在点击“保存”按钮时调用m_Shmoo对象的Save()方法。首先创建一个文件对话框，然后获取所选择的文件名，并检查该文件是否已存在。如果文件已存在，弹出一个消息框询问用户是否覆盖原有文件，如果用户选择是，则调用m_Shmoo的Save()方法保存数据。

OnShmooMessage(): 该函数是在接收到自定义消息时调用的。根据传递的参数进行条件判断，当flag为0时表示Shmoo测试开始，为1时表示Shmoo测试结束。在Shmoo测试开始时，禁用IDC_BUTTON_SHMOO按钮，然后获取X轴和Y轴的一些信息并保存在m_AxisData数组中，最后在下拉菜单m_comboTDUT中添加一些选项并设置默认选择项。在Shmoo测试结束时，填充当前选项卡的信息并在m_comboTDUT中添加一个合并选项。

OnShmooMenu(): 该函数是在接收到自定义菜单消息时调用的。根据选定的Shmoo图区域的起始和结束索引计算相应的起始和结束数值，并更新X轴和Y轴的一些信息。然后根据当前选项卡的选择，调用FillTabInfo()函数填充选项卡信息，并调用OnBnClickedButtonShmoo()函数。

SaveCurrentTabInfo(): 将当前选项卡中的设置信息保存到m_AxisData数组中。

OnTcnSelchangeTabAxis(): 该函数在选项卡切换时被调用。调用SaveCurrentTabInfo()函数保存当前选项卡的设置信息，根据选项卡的选择填充相应的信息。

OnCbnDropdownComboXsetname(): 在下拉列表m_comboXSetName展开时调用。获取charsetup文件夹下的所有json文件名，并将它们添加到下拉列表中。

OnCbnDropdownComboYsetname(): 在下拉列表m_comboYSetName展开时调用。获取charsetup文件夹下的所有json文件名，并将它们添加到下拉列表中。

ReadAxisSet(): 根据给定的轴索引和名称，读取相应的设置信息。

FillTabInfo(int naxis): 根据给定的轴索引 naxis 填充选项卡的信息。根据当前轴的类型，选择相应的模式并设置控件的状态。

OnCbnSelchangeComboXsetname(): 当 X 轴设置名称的下拉列表发生变化时调用。根据所选名称，调用 ReadAxisSet() 函数读取相应的设置信息，并根据当前选项卡的选择调用 FillTabInfo() 函数填充选项卡信息。

OnCbnSelchangeComboYsetname(): 当 Y 轴设置名称的下拉列表发生变化时调用。根据所选名称，调用 ReadAxisSet() 函数读取相应的设置信息，并根据当前选项卡的选择调用 FillTabInfo() 函数填充选项卡信息。

OnCbnSelchangeComboType(): 当类型选择的下拉列表发生变化时调用。根据所选的类型，调用相应的模式设置函数，并根据选择的类型重置时间设置的下拉列表内容。

OnCbnSelchangeComboSelectDut(): 当选择DUT的下拉列表发生变化时调用。根据所选的选项，调用 m_Shmoo 对象的相应方法。

OnBnClickedButtonCondition(): 当"ButtonCondition"按钮被点击时调用。首先检查是否加载了作业，如果没有加载则直接返回。然后保存当前选项卡的信息。接下来，根据当前轴的选择，获取X轴或Y轴设置名称的下拉列表中的当前选择，并将其存储在name变量中。然后弹出一个对话框，要求用户输入一个标题名字，并将用户输入的内容存储在name变量中。然后构造一个文件路径，并将一些设置信息保存到一个JSON文件中。如果写入文件失败，则弹出一个消息框显示错误信息。

SetTimesetMode(): 设置时间设置模式。首先检查是否加载了作业，如果没有加载则直接返回。然后重置时间设置的下拉列表内容，并根据当前共享数据中的时间组信息，填充时间设置的下拉列表。

SetACVariableMode(): 设置交流变量模式。首先检查是否加载了作业，如果没有加载则直接返回。然后根据当前共享数据中的模式执行跟踪信息，填充时间设置的下拉列表。

SetDCVariableMode(): 设置直流变量模式。首先检查是否加载了作业，如果没有加载则直接返回。然后重置时间设置的下拉列表内容，并根据当前共享数据中的直流执行跟踪信息，填充时间设置的下拉列表。

OnCbnSelchangeComboAlgorithmShmoo(): 当"ComboAlgorithmShmoo"下拉框的选择改变时调用。首先通过UpdateData(TRUE)将用户界面的数据更新到对应的成员变量中。然后根据当前选择的算法类型进行不同的操作。如果选择的算法类型为2，则将m_nMode和m_nSkip设置为0，并禁用"ComboModeShmoo"和"EditSkip"控件。否则，启用这两个控件。最后通过UpdateData(FALSE)将成员变量的值更新到用户界面上。
```
