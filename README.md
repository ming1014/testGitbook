

\# 菜鸟thrush流程编排api以及使用文档



\#\#\#\# 简介

  thrush是一个js绘图组件适用于需要在网页中设计/编辑Workflow/BPM流程图、图表、网络图和普通图形的Web应用程序。它包含流程编排引擎（thrush\)以及流程工具（thToolkit）两部分。后期将集成后端程序\(Java\)，更一步组合，方便使用。

  

\#\#\#\# 使用方法

1、引用\`//g.alicdn.com/cn/thrush/0.0.1/js/thToolkit.js\`即可。



2、实例化调用 \`new thToolkit\(\)\`函数即可调出流程图编辑器。





\#\#\# 常用api以及设置



\#\#\#\# new thToolkit\(\)



\* 作用：使用新建对象（必须引入js之后直接调用）



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| containerId     \| 工具面板父容器Id，非必填，画眉工具默认父容器为页面body \|

\| isNeedSideBar        \|是否需要左侧默认资源池面板，默认true，非必填 \|

\| isNeedTopBar        \|是否需要顶部设置栏，默认true，非必填 \|

\| isNeedToolBar        \|是否需要顶部面板工具栏，默认true，非必填 \|

\| isNeedRightFormatSideBar        \|是否需要右侧工具栏，默认true，非必填 \|

\| relativeBasePath        \|开发环境相对资源路径，非必填 \|

\| wordsUrl        \| 文字配置设置，非必填 \|

\| styleUrl        \| 流程图样式配置url，非必填 \|

\| sourceUrl        \|数据来源xml路径，非必填 \|

\| sidebarBarContentConfig        \|左侧工具栏配置，具体设置见下表 \|

\| thToolkitcallback        \|初始化工具之后的回调函数 \|

\| sideBarContent        \| 若需要左侧资源池内容面板，则可配置如下选项\['general','basic','img','advance','misc','arrow','uml','bpmn','flowchart'\]\|



左侧sidebarBarContentConfig常见配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| sidebarTitles     \| 添加的图形是否在下方显示标题，默认为false \|

\| sidebarTitleSize     \| 标题字体大小，单位px，默认9 \|

\| thumbWidth     \| 左侧节点宽度，默认40 \|

\| thumbHeight     \| 左侧节点高度，默认40 \|

\| enableTooltips     \| 结点鼠标上去是否显示提示信息，默认true \|

\| sidebarTitles     \| 添加的图形是否在下方显示标题，默认为false \|





\#\#\#\# addNodeToSource\(\)



\* 作用：自定义节点，新增节点到节点资源池，主要用于根据后端返回的自定义节点数据，生成到节点资源池



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| isExistNode     \| 是否是默认提供的结点，true（原有），false（自定义）\|

\| style     \| 结点样式，多个样式之间以\`\`\`;\`\`\`隔开，如：\`\`\`whiteSpace=wrap;html=1;fillColor=blue;\`\`\`\|

\| container     \| 结点添加到指定的父容器，必填\|

\| title     \| 左侧结点标题，非必填\|

\| width     \| 拖拽到编辑框中的显示宽度，例如100\|

\| height     \| 拖拽到编辑框中的显示高度，例如100\|

\| attribute     \| 附加属性，注意若拖拽到编辑面板使用默认展示，则必须添加useDefaultRender: true\|

\| url     \| 若使用自定义图片添加到资源池子，图片路径\|

\| dropHandlerCallback \| 拖拽到编辑面板落下之前的回调函数，其中会传递四个参数，graph（当前画布上的内容对象），cells（拖拽的结点对象），x（拖拽放开时相对画布左侧顶点x值），y（拖拽放开时相对画布左侧顶点y值），target（拖拽对象），evt（拖拽事件） \|



\#\#\#\# insertVertex\(\)



\* 作用：画布编辑器添加node节点



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| name     \| 节点名称，非必填\|

\| id     \| 结点唯一标识，可不填，默认会自动生成\|

\| startX    \| 起点x坐标，相对与画布编辑器左上角\|

\| startY    \| 起点y坐标，相对与画布编辑器左上角\|

\| width    \| 节点宽度\|

\| height    \| 节点高度\|

\| attribute    \| 节点附加属性\|

\| style    \| 节点样式，例如椭圆：\`\`\`shape=ellipse;perimeter=ellipsePerimeter;\`\`\` 矩形：\`\`\`rounded;strokeColor=yellow;fillColor=yellow;\`\`\`\|





\#\#\#\# insertEdge\(\)



\* 作用：画布编辑器添加连接线



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| name     \| 连接线名称\|

\| value     \| 连接线value\|

\| from     \| 起点节点对象\|

\| to     \| 终点节点对象\|

\| attribute     \| 附加属性\|

\| style     \| 配置样式，如：直线连接 \`\`\`strokeWidth=3;labelBackgroundColor=none;fontStyle=1\`\`\`； 直角线连接\`\`\`edgeStyle=orthogonalEdgeStyle;strokeWidth=1;labelBackgroundColor=white;color=\#666;rounded=false\`\`\`； 虚线连接\`\`\`edgeStyle=elbowEdgeStyle;elbow=horizontal;orthogonal=0;entryPerimeter=1\`\`\`\|



\#\#\#\# eventCallback\(node,eventType,callback,attribute\)



\* 作用：事件函数勾子



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| node     \| 结点对象\|

\| eventType     \| 事件类型\|

\| callback     \|回调函数\|

\| 结点属性     \|回调函数\|





\#\#\#\# setCellStyles\(key,value,obj\)



\* 作用：是指节点Cell样式



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| key     \| 设置样式种类，如：插入图片：\`\`\`thConstants.STYLE\_IMAGE\`\`\`\|

\| value     \| 样式值，如：插入的图片路径：\`\`\`image;image=./images/test2.png;\`\`\`\|

\| obj     \| 设置样式的节点对象数组\|



\#\#\#\# addListener\(event,callback\)



\* 作用：添加事件监听以及回调



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| event     \| 监听事件名称，如：节点移动事件：\`\`\`thEvent.MOVE\_CELLS\`\`\`；点击事件：\`\`\`thEvent.CLICK\`\`\`\|

\| callback     \| 事件的回调函数，两个参数：第一个参数为事件源对象，第二个为事件对象\|







\#\#\#\# getXml\(func\)



\* 作用：获取编辑面板内容xml数据



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| func     \| 函数对象，第一个参数xml数值\|





\#\#\#\# zoomIn\(\)



\* 作用：编辑面板以及内容放大，每次放大25%



\* 配置参数：无





\#\#\#\# zoomOut\(\)



\* 作用：编辑面板以及内容缩小，每次缩小25%



\* 配置参数：无





\#\#\#\# undo\(\)



\* 作用：撤销



\* 配置参数：无





\#\#\#\# groupCells\(group, border, groupCells\)



\* 作用：将cells添加分组



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| group     \| 组对象\|

\| border     \| border对象\|

\| groupCells     \| 节点数组\|



\#\#\#\# ungroupCells\(Cells\)



\* 作用：将cells撤销分组



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| cells     \| 同一组的cell对象数组\|







\#\#\#\# zoom\(ration,isBasedCenter,isBasedPrev\)



\* 作用：缩放



\* 配置参数



\| 参数配置        \|  说明   \|

\| --------   \| -----  \|

\| ration     \| 数字，缩放比例，默认为1（0.5表示缩小一倍，2表示放大一倍）\|

\| isBasedCenter     \| 是否基于中心点缩放，非必传，默认true，若设置为false，则基于画布左上角位置进行缩放\|

\| isBasedPrev     \| 是否基于原来的缩放比例再缩放，非必传，默认为false\|



























  





 

















