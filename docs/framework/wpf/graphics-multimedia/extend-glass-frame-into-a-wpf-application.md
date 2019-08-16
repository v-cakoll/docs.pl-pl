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
ms.openlocfilehash: f8d50cb4d0112232f86579542650418a1906bda2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039844"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="3e9a5-102">Rozszerz szklaną klatkę na aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="3e9a5-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="3e9a5-103">W tym temacie pokazano, [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] jak rozciągnąć szklaną ramkę do obszaru klienckiego aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3e9a5-103">This topic demonstrates how to extend the [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="3e9a5-104">Ten przykład będzie działać tylko na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] komputerze z uruchomioną Menedżer okien pulpitu (DWM) z włączoną funkcją Glass.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-104">This example will only work on a [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]<span data-ttu-id="3e9a5-105">Wersja Home Basic nie obsługuje przezroczystego efektu szkła.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-105">Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="3e9a5-106">Obszary, które zwykle są renderowane z przezroczystym efektem szkła w innych [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] wersjach, są renderowane nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-106">Areas that would typically render with the transparent glass effect on other editions of [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="3e9a5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e9a5-107">Example</span></span>

<span data-ttu-id="3e9a5-108">Na poniższej ilustracji przedstawiono szklaną ramkę rozszerzoną na pasku adresu programu Internet Explorer 7:</span><span class="sxs-lookup"><span data-stu-id="3e9a5-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7:</span></span>

![Zrzut ekranu przedstawiający ramkę szkła rozszerzoną za paskiem adresu przeglądarki IE7.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

<span data-ttu-id="3e9a5-110">Aby można było rozwinąć szklaną ramkę w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, wymagany jest dostęp do niezarządzanego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-110">To extend the glass frame on a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, access to unmanaged API is needed.</span></span> <span data-ttu-id="3e9a5-111">Poniższy przykład kodu wykonuje wywołanie platformy (PInvoke) dla dwóch interfejsów API, które są konieczne do rozszerania ramki do obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-111">The following code example does a Platform Invoke (pinvoke) for the two API needed to extend the frame into the client area.</span></span> <span data-ttu-id="3e9a5-112">Każdy z tych interfejsów API jest zadeklarowany w klasie o nazwie **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-112">Each of these API are declared in a class called **NonClientRegionAPI**.</span></span>

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

<span data-ttu-id="3e9a5-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) to funkcja menedżera DWM, która rozszerza ramkę do obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="3e9a5-114">Przyjmuje dwa parametry: uchwyt okna i struktura [marginesów](/windows/win32/api/uxtheme/ns-uxtheme-margins) .</span><span class="sxs-lookup"><span data-stu-id="3e9a5-114">It takes two parameters; a window handle and a [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) structure.</span></span> <span data-ttu-id="3e9a5-115">[Marginesy](/windows/win32/api/uxtheme/ns-uxtheme-margins) są używane do poinformowania menedżera DWM o tym, ile dodatkowej ramki należy rozszerzyć do obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="3e9a5-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e9a5-116">Example</span></span>

<span data-ttu-id="3e9a5-117">Aby można było użyć funkcji [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) , należy uzyskać uchwyt okna.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-117">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="3e9a5-118">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie uchwyt okna można uzyskać <xref:System.Windows.Interop.HwndSource.Handle%2A> z właściwości <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-118">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="3e9a5-119">W poniższym przykładzie ramka zostanie rozszerzona do obszaru klienckiego w <xref:System.Windows.FrameworkElement.Loaded> zdarzeniu okna.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-119">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

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

## <a name="example"></a><span data-ttu-id="3e9a5-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e9a5-120">Example</span></span>

<span data-ttu-id="3e9a5-121">W poniższym przykładzie pokazano proste okno, w którym ramka zostanie rozszerzona do obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-121">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="3e9a5-122">Ramka jest rozszerzona za górną krawędzią, która zawiera <xref:System.Windows.Controls.TextBox> dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="3e9a5-122">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

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

<span data-ttu-id="3e9a5-123">Na poniższej ilustracji przedstawiono szklaną ramkę rozszerzoną [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3e9a5-123">The following image illustrates the glass frame extended into a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application:</span></span>

![Zrzut ekranu przedstawiający ramkę szklaną rozszerzoną do aplikacji WPF.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a><span data-ttu-id="3e9a5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e9a5-125">See also</span></span>

- [<span data-ttu-id="3e9a5-126">Przegląd Menedżer okien pulpitu</span><span class="sxs-lookup"><span data-stu-id="3e9a5-126">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="3e9a5-127">Menedżer okien pulpitu rozmycie — Omówienie</span><span class="sxs-lookup"><span data-stu-id="3e9a5-127">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="3e9a5-128">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="3e9a5-128">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
