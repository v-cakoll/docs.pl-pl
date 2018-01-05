---
title: "Rozszerz szklaną klatkę na aplikację WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aad070bca408fc608eb000948c1b942d08f02018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Rozszerz szklaną klatkę na aplikację WPF
W tym temacie przedstawiono sposób rozszerzyć [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] szkła ramki do obszaru klienckiego [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji.  
  
> [!NOTE]
>  W tym przykładzie będzie działać tylko na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] maszyny z systemem Menedżera okien pulpitu (DWM) z szkła włączone. [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]Home edition podstawowa nie obsługuje efekt szkła przezroczysty. Obszary, które zwykle pozbawia efekt szkła przezroczysty na inne wersje [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] są renderowane przezroczystości.  
  
## <a name="example"></a>Przykład  
 Na poniższym obrazie przedstawiono szkła ramki rozszerzony do adresu pasek programu Internet Explorer 7.  
  
 **Program Internet Explorer z rozszerzonego szkła ramki za paska adresu.**  
  
 ![IE7 szkła ramki rozszerzony poza pasek adresu. ] (../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 Aby rozszerzyć szkła ramki na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, dostęp do niezarządzanego [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] jest wymagana. Poniższy przykładowy kod jest wywołanie platformy (pinvoke) dla dwóch [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] spełnić w celu rozszerzenia ramki do obszaru klienckiego. Każdy z tych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] został zadeklarowany w klasie o nazwie **NonClientRegionAPI**.  
  
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
  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) jest funkcja Menedżera okien pulpitu, rozszerzający ramki do obszaru klienckiego. Trwa dwóch parametrów; uchwyt okna i [MARGINESY](https://msdn.microsoft.com/library/bb773244.aspx) struktury. [MARGINESY](https://msdn.microsoft.com/library/bb773244.aspx) informuje Menedżera okien pulpitu, ile bardzo ramki powinien zostać rozszerzony do obszaru klienckiego.  
  
## <a name="example"></a>Przykład  
 Aby użyć [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) funkcji, należy uzyskać uchwytu okna. W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można uzyskać uchwytu okna <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwość <xref:System.Windows.Interop.HwndSource>. W poniższym przykładzie ramki jest rozszerzony do obszaru klienckiego na <xref:System.Windows.FrameworkElement.Loaded> zdarzenia okna.  
  
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
 W poniższym przykładzie przedstawiono prosty okna, w którym ramki jest rozszerzony do obszaru klienckiego. Ramki jest rozszerzona za górnej krawędzi, która zawiera dwa <xref:System.Windows.Controls.TextBox> obiektów.  
  
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
  
 Na poniższym obrazie przedstawiono szkła ramki rozszerzone do postaci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 **Szkła ramki rozszerzone do postaci**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**aplikacji.**   
  
 ![Szkła ramki rozszerzonych w aplikacji WPF. ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Menedżera okien pulpitu](https://msdn.microsoft.com/library/aa969540.aspx)  
 [Omówienie rozmycia Menedżera okien pulpitu](https://msdn.microsoft.com/library/aa969537.aspx)  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx)
