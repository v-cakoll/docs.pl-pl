---
title: 'Porady: tworzenie StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 30f24d8dba7c09271a5957822439af6b64e05aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553030"
---
# <a name="how-to-create-a-stackpanel"></a>Porady: tworzenie StackPanel
W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.StackPanel> umożliwia stosu elementów w określonym kierunku. Za pomocą właściwości, które są zdefiniowane na <xref:System.Windows.Controls.StackPanel>, zawartość może przepływać zarówno w pionie, co jest ustawieniem domyślnym lub w poziomie.  
  
 Poniższy przykład pionowo pięć stosów <xref:System.Windows.Controls.TextBlock> steruje każdego z innym <xref:System.Windows.Controls.Border> i <xref:System.Windows.Controls.Border.Background%2A>, za pomocą <xref:System.Windows.Controls.StackPanel>. Elementy podrzędne, które nie istnieją określone <xref:System.Windows.FrameworkElement.Width%2A> rozciągają się, aby wypełnić okno nadrzędne; jednak elementy podrzędne mają określoną <xref:System.Windows.FrameworkElement.Width%2A>, jest wyśrodkowywana w oknie.  
  
 Domyślny kierunek stosu w <xref:System.Windows.Controls.StackPanel> pionowy. Do sterowania przepływem zawartości w <xref:System.Windows.Controls.StackPanel>, użyj <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwości. Wyrównanie w poziomie można kontrolować przy użyciu <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.StackPanel>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
