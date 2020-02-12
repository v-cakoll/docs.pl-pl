---
title: Jak ustawić właściwości szerokości elementu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124276"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Jak ustawić właściwości szerokości elementu
## <a name="example"></a>Przykład  
 Ten przykład wizualnie pokazuje różnice w zachowaniu renderowania między właściwościami powiązanymi z szerokością w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Klasa <xref:System.Windows.FrameworkElement> uwidacznia cztery właściwości, które opisują charakterystykę szerokości elementu. Te cztery właściwości mogą powodować konflikt i gdy tak się stanie, wartość, która ma pierwszeństwo, jest określana w następujący sposób: wartość <xref:System.Windows.FrameworkElement.MinWidth%2A> ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.MaxWidth%2A>, która z kolei ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.Width%2A>. Czwarta właściwość, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, jest tylko do odczytu i raportuje rzeczywistą szerokość określoną przez interakcje z procesem układu.  
  
 Poniższe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysują element <xref:System.Windows.Shapes.Rectangle> (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>. Właściwości szerokości <xref:System.Windows.Shapes.Rectangle> można zmienić przy użyciu serii <xref:System.Windows.Controls.ListBox> elementów, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>i <xref:System.Windows.FrameworkElement.Width%2A>. Dzięki temu pierwszeństwo każdej właściwości jest wyświetlane wizualnie.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Poniższe przykłady kodu obsługują zdarzenia zgłoszone przez zdarzenie <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Każda metoda niestandardowa pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i stosuje wartość do określonej właściwości powiązanej z szerokością. Wartości szerokości są również konwertowane na ciąg i zapisywane na różne elementy <xref:System.Windows.Controls.TextBlock> (definicja tych elementów nie jest pokazana w wybranym kodzie XAML).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [przykłady porównania właściwości Width](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Panele — omówienie](panels-overview.md)
- [Ustawianie właściwości wysokości elementu](how-to-set-the-height-properties-of-an-element.md)
- [Przykład porównania właściwości Width](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
