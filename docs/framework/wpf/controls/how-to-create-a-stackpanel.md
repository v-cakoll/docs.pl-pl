---
title: 'Instrukcje: Tworzenie StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 46b037e3f1626e77a61dca787b705a63ccd28ba0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360448"
---
# <a name="how-to-create-a-stackpanel"></a>Instrukcje: Tworzenie StackPanel
W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Przykład  
 A <xref:System.Windows.Controls.StackPanel> pozwala na stosie elementów w określonym kierunku. Za pomocą właściwości, które są zdefiniowane na <xref:System.Windows.Controls.StackPanel>, zawartość może przepływać zarówno w pionie, co jest ustawieniem domyślnym lub w poziomie.  
  
 Poniższy przykład pionowo stosów pięciu <xref:System.Windows.Controls.TextBlock> kontroluje, każdy z inną <xref:System.Windows.Controls.Border> i <xref:System.Windows.Controls.Border.Background%2A>, za pomocą <xref:System.Windows.Controls.StackPanel>. Elementy podrzędne, które nie istnieją określone <xref:System.Windows.FrameworkElement.Width%2A> Stretch Database w celu wypełnienia okna nadrzędnego; jednak elementy podrzędne, które mają określoną <xref:System.Windows.FrameworkElement.Width%2A>, jest wyśrodkowywana w oknie.  
  
 Domyślny kierunek stosu w <xref:System.Windows.Controls.StackPanel> pionowy. Do zawartości przepływ sterowania w aplikacjach <xref:System.Windows.Controls.StackPanel>, użyj <xref:System.Windows.Controls.StackPanel.Orientation%2A> właściwości. Wyrównanie w poziomie można kontrolować za pomocą <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.StackPanel>
- [Panele — omówienie](panels-overview.md)
- [Tematy z instrukcjami](stackpanel-how-to-topics.md)
