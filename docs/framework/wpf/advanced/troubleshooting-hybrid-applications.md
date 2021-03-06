---
title: 混合应用程序疑难解答
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: 878761c030d4950e53ee24b76f7e29101584143a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549028"
---
# <a name="troubleshooting-hybrid-applications"></a>混合应用程序疑难解答
<a name="introduction"></a>本主题列出了在创作同时使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]技术的混合应用程序时可能发生的一些常见问题。  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>重叠控件  
 控件可能不按预期的方式重叠。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]为每个控件使用单独的 HWND。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 为一个页面上的所有内容使用一个 HWND。 这一实现差异会导致意外的重叠行为。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中承载的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件总是出现在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内容之上。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内容宿主在<xref:System.Windows.Forms.Integration.ElementHost>控件显示在 z 顺序<xref:System.Windows.Forms.Integration.ElementHost>控件。 可以重叠<xref:System.Windows.Forms.Integration.ElementHost>控件，但将托管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内容不会合并或进行交互。  
  
<a name="child_property"></a>   
## <a name="child-property"></a>子属性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>类只能承载只有单个子控件或元素。 若要承载多个控件或元素，则必须使用容器作为子内容。 例如，可以添加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]按钮和复选框的控件<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>控制，，然后将分配到面板<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>属性。 但是，不能添加按钮和复选框控件单独到同一个<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件。  
  
<a name="scaling"></a>   
## <a name="scaling"></a>缩放  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]具有不同的缩放模型。 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 缩放变换对于 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件是有意义的，但其他变换是无意义的。 例如，将 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件缩放到 0 是可行的，但如果尝试将同一控件重新缩放回非零值，该控件的大小仍然为 0。 有关详细信息，请参阅 [WindowsFormsHost 元素的布局注意事项](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="adapter"></a>   
## <a name="adapter"></a>适配器  
 在处理时可能会发生混乱<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>类，因为它们包括隐藏的容器。 同时<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>类具有名为的隐藏的容器*适配器*，它用来承载内容。 有关<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，该适配器将派生自<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>类。 有关<xref:System.Windows.Forms.Integration.ElementHost>控件，该适配器将派生自<xref:System.Windows.Controls.DockPanel>元素。 如果你发现其他互操作主题中提到了适配器，那么所讨论的就是此容器。  
  
<a name="nesting"></a>   
## <a name="nesting"></a>嵌套  
 嵌套<xref:System.Windows.Forms.Integration.WindowsFormsHost>内的元素<xref:System.Windows.Forms.Integration.ElementHost>控件不支持。 嵌套<xref:System.Windows.Forms.Integration.ElementHost>控件内部<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素也不支持。  
  
<a name="focus"></a>   
## <a name="focus"></a>焦点  
 焦点在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中的工作方式是不同的，这意味着混合应用程序中可能发生焦点问题。 例如，如果内部具有焦点<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，并且你是最小化和还原页或显示模式对话框，在焦点<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素可能会丢失。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素仍具有焦点，但其内部控件可能不包括。  
  
 焦点还会影响数据验证。 验证适用于<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，但它不能按选项卡上外<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，或两个不同<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素。  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>属性映射  
 某些属性映射需要先进行大量的转译，才能将 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]技术之间不同的实现桥接起来。 属性映射可使代码对字体、颜色和其他属性的更改做出反应。 通常，属性映射的工作方式是侦听 *Property*Changed 事件或 On*Property* 调用，然后在子控件或其适配器上设置适当的属性。 有关详细信息，请参阅 [Windows 窗体和 WPF 属性映射](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>所承载内容上的布局相关属性  
 当<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>分配属性，将自动设置多个布局相关的属性上所承载的内容。 更改这些内容属性可能会导致意外的布局行为。  
  
 所承载的内容停靠以填充<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>父。 为了启用此填充行为，在设置子属性时，将设置多个属性。 下表列出了哪些内容属性设置通过<xref:System.Windows.Forms.Integration.ElementHost>和<xref:System.Windows.Forms.Integration.WindowsFormsHost>类。  
  
|宿主类|内容属性|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 请勿在所承载的内容上直接设置这些属性。 有关详细信息，请参阅 [WindowsFormsHost 元素的布局注意事项](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>导航应用程序  
 导航应用程序不能保持用户状态。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素重新创建其控件，在导航应用程序中使用时。 当用户导航离开页面承载重新创建子控件时发生<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，然后又返回到它。 用户已经键入的所有内容都将丢失。  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>消息循环互操作  
 在使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]消息循环时，可能无法按照预期方式处理消息。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>方法由调用<xref:System.Windows.Forms.Integration.WindowsFormsHost>构造函数。 此方法将向 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 消息循环中添加消息筛选器。 此筛选器调用<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>方法如果<xref:System.Windows.Forms.Control?displayProperty=nameWithType>的目标的消息并且转换/调度消息。  
  
 如果你显示<xref:System.Windows.Window>中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]消息循环中的使用<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>，您不能键入任何内容，除非调用<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法。 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法采用<xref:System.Windows.Window>并添加<xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>，其中，则重新确定密钥相关消息添加到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]消息循环。 有关详细信息，请参阅 [Windows 窗体和 WPF 互操作性输入体系结构](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)。  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>不透明度和分层  
 <xref:System.Windows.Interop.HwndHost>类不支持分层。 这意味着该设置<xref:System.Windows.UIElement.Opacity%2A>属性<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素没有任何影响，且没有混合会发生与其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]窗口产生<xref:System.Windows.Window.AllowsTransparency%2A>设置为`true`。  
  
<a name="dispose"></a>   
## <a name="dispose"></a>释放  
 未正确释放类可能会泄漏资源。 在混合应用程序，请确保<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>释放类，或你可能会泄漏资源。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 释放<xref:System.Windows.Forms.Integration.ElementHost>控制其非模式<xref:System.Windows.Forms.Form>父级关闭。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 释放<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素在你的应用程序关闭时。 可以显示<xref:System.Windows.Forms.Integration.WindowsFormsHost>中的元素<xref:System.Windows.Window>中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]消息循环。 在这种情况下，代码可能不会收到应用程序正在关闭的通知。  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>启用视觉样式  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件上的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 视觉样式可能未启用。 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法调用中的模板[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]应用程序。 尽管默认情况下不会调用此方法，但如果使用 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 创建项目，并且 Comctl32.dll 版本 6.0 可用，将会获得控件的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 视觉样式。 必须调用<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法之前在线程上创建句柄。 有关详细信息，请参阅[如何：在混合应用程序中启用视觉样式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)。  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>授权控件  
 授权的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件会在消息框中向用户显示许可信息，对于混合应用程序，这可能会导致意外行为。 某些授权控件会显示一个对话框来响应创建句柄的操作。 例如，授权控件可能会通知用户需要许可证，或者用户还可以试用该控件三次。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素派生自<xref:System.Windows.Interop.HwndHost>类，并且子控件的句柄在内创建<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法。 <xref:System.Windows.Interop.HwndHost>类不允许将邮件中要处理<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法，但显示一个对话框会导致消息发送。 若要启用此授权方案，调用<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>然后再将其作为分配控件上的方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的子级。  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF 设计器  
 可以使用 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 设计你的 WPF 内容。 以下部分列出了在使用 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 创作混合应用程序时可能发生的一些常见问题。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>在设计时忽略 BackColorTransparent  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>属性可能无法按预期方式在设计时。  
  
 如果 WPF 控件不可见的父中，WPF 运行时将忽略<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>值。 原因，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>可能会忽略是因为<xref:System.Windows.Forms.Integration.ElementHost>对象创建在单独<xref:System.AppDomain>。 但是，当你运行该应用程序，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>未按预期方式工作。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>删除 obj 文件夹时出现设计时错误列表  
 如果删除 obj 文件夹，会出现设计时错误列表。  
  
 当您设计使用<xref:System.Windows.Forms.Integration.ElementHost>，Windows 窗体设计器使用你的项目的 obj 文件夹中的 Debug 或 Release 文件夹中生成的文件。 如果删除这些文件，将出现设计时错误列表。 若要解决此问题，请重新生成项目。 有关详细信息，请参阅 [Windows 窗体设计器中的设计时错误](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)。  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost 和 IME  
 中承载 WPF 控件<xref:System.Windows.Forms.Integration.ElementHost>目前不支持<xref:System.Windows.Forms.Control.ImeMode%2A>属性。 更改为<xref:System.Windows.Forms.Control.ImeMode%2A>将忽略所承载的控件。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [在 WPF 设计器中的互操作性](http://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Windows 窗体和 WPF 互操作性输入体系结构](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [如何：在混合应用程序中启用视觉对象样式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [WindowsFormsHost 元素的布局注意事项](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Windows 窗体和 WPF 属性映射](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Windows 窗体设计器中的设计时错误](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [迁移和互操作性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
