---
title: Poszerzanie szklanej ramki do aplikacji WPF
titleSuffix: ''
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
ms.openlocfilehash: b78547aa8b414c585bb2e5c9c6680ed159731bc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746535"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Rozszerz szklaną klatkę na aplikację WPF

W tym temacie pokazano, jak zwiększyć ramkę szkła systemu Windows Vista do obszaru klienckiego aplikacji Windows Presentation Foundation (WPF).

> [!NOTE]
> Ten przykład działa tylko na komputerze z systemem Windows Vista z uruchomioną Menedżer okien pulpitu (DWM) z włączoną opcją Glass. System Windows Vista Home Basic nie obsługuje przezroczystego efektu szkła. Obszary, które zwykle są renderowane z przezroczystym efektem szkła w innych wersjach systemu Windows Vista, są renderowane nieprzezroczyste.

## <a name="example"></a>Przykład

Na poniższej ilustracji przedstawiono szklaną ramkę rozszerzoną na pasku adresu programu Internet Explorer 7:

![Zrzut ekranu przedstawiający ramkę szkła rozszerzoną za paskiem adresu przeglądarki IE7.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

Aby można było rozwinąć szklaną ramkę w aplikacji WPF, wymagany jest dostęp do niezarządzanego interfejsu API. Poniższy przykład kodu wykonuje wywołanie platformy (PInvoke) dla dwóch interfejsów API, które są konieczne do rozszerania ramki do obszaru klienckiego. Każdy z tych interfejsów API jest zadeklarowany w klasie o nazwie **NonClientRegionAPI**.

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

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) to funkcja menedżera DWM, która rozszerza ramkę do obszaru klienckiego. Przyjmuje dwa parametry: uchwyt okna i struktura [marginesów](/windows/win32/api/uxtheme/ns-uxtheme-margins) . [Marginesy](/windows/win32/api/uxtheme/ns-uxtheme-margins) są używane do poinformowania menedżera DWM o tym, ile dodatkowej ramki należy rozszerzyć do obszaru klienckiego.

## <a name="example"></a>Przykład

Aby można było użyć funkcji [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) , należy uzyskać uchwyt okna. W WPF, uchwyt okna można uzyskać z właściwości <xref:System.Windows.Interop.HwndSource.Handle%2A> <xref:System.Windows.Interop.HwndSource>. W poniższym przykładzie ramka zostanie rozszerzona do obszaru klienckiego w <xref:System.Windows.FrameworkElement.Loaded> zdarzeniu okna.

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

W poniższym przykładzie pokazano proste okno, w którym ramka zostanie rozszerzona do obszaru klienckiego. Ramka jest rozszerzona za górną krawędzią, która zawiera dwa obiekty <xref:System.Windows.Controls.TextBox>.

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

Na poniższej ilustracji przedstawiono szklaną ramkę rozszerzoną do aplikacji WPF:

![Zrzut ekranu przedstawiający ramkę szklaną rozszerzoną do aplikacji WPF.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a>Zobacz także

- [Przegląd Menedżer okien pulpitu](/windows/desktop/dwm/dwm-overview)
- [Menedżer okien pulpitu rozmycie — Omówienie](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
