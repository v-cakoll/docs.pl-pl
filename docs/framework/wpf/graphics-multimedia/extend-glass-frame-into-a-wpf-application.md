---
title: Rozszerz szklaną klatkę na aplikację WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: 9df6adbf9208ee58044b0ba6ef606d693c9dca7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705826"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="96843-102">Rozszerz szklaną klatkę na aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="96843-102">Extend Glass Frame Into a WPF Application</span></span>
<span data-ttu-id="96843-103">W tym temacie pokazano, jak rozszerzyć [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] szklaną klatkę do obszaru klienckiego aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="96843-103">This topic demonstrates how to extend the [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96843-104">W tym przykładzie będą działać tylko na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] maszyny z systemem Menedżera okien pulpitu (DWM) przy użyciu szkła włączone.</span><span class="sxs-lookup"><span data-stu-id="96843-104">This example will only work on a [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] <span data-ttu-id="96843-105">Macierzysty wersji podstawowa nie obsługuje efekt szkła przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="96843-105">Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="96843-106">Obszary, które zazwyczaj będzie renderowania przy użyciu efektu szkła przezroczyste w innych wersjach [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] — zostaną zrenderowane nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="96843-106">Areas that would typically render with the transparent glass effect on other editions of [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] are rendered opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96843-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="96843-107">Example</span></span>  
 <span data-ttu-id="96843-108">Na poniższym obrazie przedstawiono szklaną klatkę rozszerzony do adresu pasek w programie Internet Explorer 7.</span><span class="sxs-lookup"><span data-stu-id="96843-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="96843-109">**Internet Explorer przy użyciu rozszerzonych szklaną klatkę poza pasek adresu.**</span><span class="sxs-lookup"><span data-stu-id="96843-109">**Internet Explorer with extended glass frame behind address bar.**</span></span>  
  
 <span data-ttu-id="96843-110">![IE7 ramki szkła rozszerzony poza pasek adresu. ](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")</span><span class="sxs-lookup"><span data-stu-id="96843-110">![IE7 with glass frame extended behind address bar.](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")</span></span>  
  
 <span data-ttu-id="96843-111">Aby rozszerzyć szklaną klatkę na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, dostęp do niezarządzanego [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="96843-111">To extend the glass frame on a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, access to unmanaged [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] is needed.</span></span> <span data-ttu-id="96843-112">Poniższy przykład kodu jest wywołanie platformy (funkcja pinvoke) dla dwóch [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] spełnić w celu rozszerzenia ramki do obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="96843-112">The following code example does a Platform Invoke (pinvoke) for the two [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] needed to extend the frame into the client area.</span></span> <span data-ttu-id="96843-113">Każda z tych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] są zadeklarowane w klasie o nazwie **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="96843-113">Each of these [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] are declared in a class called **NonClientRegionAPI**.</span></span>  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MARGINS  
{  
    public int cxLeftWidth;      // width of left border that retains its size  
    public int cxRightWidth;     // width of right border that retains its size  
    public int cyTopHeight;      // height of top border that retains its size  
    public int cyBottomHeight;   // height of bottom border that retains its size  
};  
  
[DllImport("DwmApi.dll")]  
public static extern int DwmExtendFrameIntoClientArea(  
    IntPtr hwnd,  
    ref MARGINS pMarInset);  
```  
  
```vb  
<StructLayout(LayoutKind.Sequential)>  
        Public Structure MARGINS  
            Public cxLeftWidth As Integer ' width of left border that retains its size  
            Public cxRightWidth As Integer ' width of right border that retains its size  
            Public cyTopHeight As Integer ' height of top border that retains its size  
            Public cyBottomHeight As Integer ' height of bottom border that retains its size  
        End Structure  
  
        <DllImport("DwmApi.dll")>  
        Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer  
        End Function  
```  
  
 <span data-ttu-id="96843-114">[Dwmextendframeintoclientarea —](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) jest funkcją Menedżera okien pulpitu, która obejmuje ramki obszaru klienta.</span><span class="sxs-lookup"><span data-stu-id="96843-114">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="96843-115">Trwa dwóch parametrów; uchwyt okna i [MARGINESY](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) struktury.</span><span class="sxs-lookup"><span data-stu-id="96843-115">It takes two parameters; a window handle and a [MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) structure.</span></span> <span data-ttu-id="96843-116">[MARGINESY](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) informuje Menedżera okien pulpitu, ile dodatkowych ramki powinien zostać rozszerzony do obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="96843-116">[MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96843-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="96843-117">Example</span></span>  
 <span data-ttu-id="96843-118">Aby użyć [dwmextendframeintoclientarea —](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) funkcji, należy uzyskać uchwyt okna.</span><span class="sxs-lookup"><span data-stu-id="96843-118">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="96843-119">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], uchwyt okna można uzyskać z <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwość <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="96843-119">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="96843-120">W poniższym przykładzie ramki jest rozszerzany do obszaru klienckiego na <xref:System.Windows.FrameworkElement.Loaded> zdarzeń okna.</span><span class="sxs-lookup"><span data-stu-id="96843-120">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>  
  
```csharp  
void OnLoaded(object sender, RoutedEventArgs e)  
{  
   try  
   {  
      // Obtain the window handle for WPF application  
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;  
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);  
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);  
  
      // Get System Dpi  
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);  
      float DesktopDpiX = desktop.DpiX;  
      float DesktopDpiY = desktop.DpiY;  
  
      // Set Margins  
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();  
  
      // Extend glass frame into client area  
      // Note that the default desktop Dpi is 96dpi. The  margins are  
      // adjusted for the system Dpi.  
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));  
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));  
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));  
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));  
  
      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);  
      //  
      if (hr < 0)  
      {  
         //DwmExtendFrameIntoClientArea Failed  
      }  
   }  
   // If not Vista, paint background white.  
   catch (DllNotFoundException)  
   {  
      Application.Current.MainWindow.Background = Brushes.White;  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="96843-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="96843-121">Example</span></span>  
 <span data-ttu-id="96843-122">Proste okno, w którym ramki jest rozszerzony do obszaru klienckiego można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="96843-122">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="96843-123">Ramki jest rozszerzona za górne krawędzie, który zawiera dwa <xref:System.Windows.Controls.TextBox> obiektów.</span><span class="sxs-lookup"><span data-stu-id="96843-123">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>  
  
```xaml  
<Window x:Class="SDKSample.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Extended Glass in WPF" Height="300" Width="400"   
    Loaded="OnLoaded" Background="Transparent"  
    >  
  <Grid ShowGridLines="True">  
    <DockPanel Name="mainDock">  
      <!-- The border is used to compute the rendered height with margins.  
           topBar contents will be displayed on the extended glass frame.-->  
      <Border Name="topBar" DockPanel.Dock="Top" >  
        <Grid Name="grid">  
          <Grid.ColumnDefinitions>  
            <ColumnDefinition MinWidth="100" Width="*"/>  
            <ColumnDefinition Width="Auto"/>  
          </Grid.ColumnDefinitions>  
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>  
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>  
        </Grid>  
      </Border>  
      <Grid DockPanel.Dock="Top" >  
        <Grid.ColumnDefinitions>  
          <ColumnDefinition/>  
        </Grid.ColumnDefinitions>  
        <TextBox Grid.Column="0" AcceptsReturn="True"/>  
      </Grid>  
    </DockPanel>  
  </Grid>  
</Window>  
```  
  
 <span data-ttu-id="96843-124">Na poniższym obrazie przedstawiono szklaną klatkę rozszerzone do postaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96843-124">The following image illustrates the glass frame extended into a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application.</span></span>  
  
 <span data-ttu-id="96843-125">**Ramki szkła rozszerzone do postaci**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="96843-125">**Glass Frame Extended into a**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **Application.**</span></span>  
  
 <span data-ttu-id="96843-126">![Szkła ramki rozszerzone do postaci aplikacji WPF. ](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span><span class="sxs-lookup"><span data-stu-id="96843-126">![Glass Frame Extended into a WPF application.](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96843-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96843-127">See also</span></span>
- [<span data-ttu-id="96843-128">Omówienie Menedżera okien pulpitu</span><span class="sxs-lookup"><span data-stu-id="96843-128">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="96843-129">Omówienie Rozmycie Menedżera okien pulpitu</span><span class="sxs-lookup"><span data-stu-id="96843-129">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="96843-130">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="96843-130">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
