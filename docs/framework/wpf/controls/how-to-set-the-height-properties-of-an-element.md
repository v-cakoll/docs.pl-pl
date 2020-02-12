---
title: Jak ustawić właściwości wysokości elementu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124289"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Jak ustawić właściwości wysokości elementu
## <a name="example"></a>Przykład  
 Ten przykład wizualnie pokazuje różnice między zachowaniem renderowania a czterema właściwościami dotyczącymi wysokości w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Klasa <xref:System.Windows.FrameworkElement> uwidacznia cztery właściwości, które opisują charakterystykę wysokości elementu. Te cztery właściwości mogą powodować konflikt i gdy tak się stanie, wartość, która ma pierwszeństwo, jest określana w następujący sposób: wartość <xref:System.Windows.FrameworkElement.MinHeight%2A> ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.MaxHeight%2A>, która z kolei ma pierwszeństwo przed wartością <xref:System.Windows.FrameworkElement.Height%2A>. Czwarta właściwość, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, jest tylko do odczytu i raportuje rzeczywistą wysokość ustaloną przez interakcje z procesem układu.  
  
 Poniższe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysują element <xref:System.Windows.Shapes.Rectangle> (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>. Właściwości wysokości <xref:System.Windows.Shapes.Rectangle> można zmienić przy użyciu serii <xref:System.Windows.Controls.ListBox> elementów, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>i <xref:System.Windows.FrameworkElement.Height%2A>. Dzięki temu pierwszeństwo każdej właściwości jest wyświetlane wizualnie.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Poniższe przykłady kodu obsługują zdarzenia zgłoszone przez zdarzenie <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Każdy program obsługi pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i stosuje wartość do określonej właściwości powiązanej z wysokością. Wartości wysokości są również konwertowane na ciąg i zapisywane w różnych elementach <xref:System.Windows.Controls.TextBlock> (definicja tych elementów nie jest pokazana w wybranym kodzie XAML).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Aby uzyskać kompletny przykład, zobacz [przykład właściwości Height](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Ustawianie właściwości szerokości elementu](how-to-set-the-width-properties-of-an-element.md)
- [Panele — omówienie](panels-overview.md)
- [Przykład właściwości Height](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
