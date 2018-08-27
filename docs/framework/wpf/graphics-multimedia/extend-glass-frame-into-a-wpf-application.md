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
ms.openlocfilehash: 93eda6d6a13d6a510f2aeb06ab1c66d0cd40927f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931543"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Rozszerz szklaną klatkę na aplikację WPF
W tym temacie pokazano, jak rozszerzyć [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] szklaną klatkę do obszaru klienckiego aplikacji Windows Presentation Foundation (WPF).  
  
> [!NOTE]
>  W tym przykładzie będą działać tylko na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] maszyny z systemem Menedżera okien pulpitu (DWM) przy użyciu szkła włączone. [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Macierzysty wersji podstawowa nie obsługuje efekt szkła przezroczysty. Obszary, które zazwyczaj będzie renderowania przy użyciu efektu szkła przezroczyste w innych wersjach [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] — zostaną zrenderowane nieprzezroczystości.  
  
## <a name="example"></a>Przykład  
 Na poniższym obrazie przedstawiono szklaną klatkę rozszerzony do adresu pasek w programie Internet Explorer 7.  
  
 **Internet Explorer przy użyciu rozszerzonych szklaną klatkę poza pasek adresu.**  
  
 ![IE7 ramki szkła rozszerzony poza pasek adresu. ](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 Aby rozszerzyć szklaną klatkę na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, dostęp do niezarządzanego [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] jest wymagana. Poniższy przykład kodu jest wywołanie platformy (funkcja pinvoke) dla dwóch [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] spełnić w celu rozszerzenia ramki do obszaru klienckiego. Każda z tych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] są zadeklarowane w klasie o nazwie **NonClientRegionAPI**.  
  
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
  
 [Dwmextendframeintoclientarea —](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) jest funkcją Menedżera okien pulpitu, która obejmuje ramki obszaru klienta. Trwa dwóch parametrów; uchwyt okna i [MARGINESY](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) struktury. [MARGINESY](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) informuje Menedżera okien pulpitu, ile dodatkowych ramki powinien zostać rozszerzony do obszaru klienckiego.  
  
## <a name="example"></a>Przykład  
 Aby użyć [dwmextendframeintoclientarea —](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) funkcji, należy uzyskać uchwyt okna. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], uchwyt okna można uzyskać z <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwość <xref:System.Windows.Interop.HwndSource>. W poniższym przykładzie ramki jest rozszerzany do obszaru klienckiego na <xref:System.Windows.FrameworkElement.Loaded> zdarzeń okna.  
  
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
  
## <a name="example"></a>Przykład  
 Proste okno, w którym ramki jest rozszerzony do obszaru klienckiego można znaleźć w poniższym przykładzie. Ramki jest rozszerzona za górne krawędzie, który zawiera dwa <xref:System.Windows.Controls.TextBox> obiektów.  
  
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
  
 Na poniższym obrazie przedstawiono szklaną klatkę rozszerzone do postaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 **Ramki szkła rozszerzone do postaci**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**aplikacji.**   
  
 ![Szkła ramki rozszerzone do postaci aplikacji WPF. ](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Menedżera okien pulpitu](/windows/desktop/dwm/dwm-overview)  
 [Omówienie Rozmycie Menedżera okien pulpitu](/windows/desktop/dwm/blur-ovw)  
 [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
