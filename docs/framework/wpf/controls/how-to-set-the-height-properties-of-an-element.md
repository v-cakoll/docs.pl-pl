---
title: 'Instrukcje: Ustawianie właściwości wysokości elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: fb655630336c3b69afdc726a2e3c5a2cb8838667
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024420"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Instrukcje: Ustawianie właściwości wysokości elementu
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie między cztery właściwości związane z wysokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują właściwości wysokości elementu. Te cztery właściwości mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określany w następujący sposób: <xref:System.Windows.FrameworkElement.MinHeight%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxHeight%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Height%2A> wartość. Czwarty właściwość <xref:System.Windows.FrameworkElement.ActualHeight%2A>, jest tylko do odczytu i raporty rzeczywiste wysokość zgodnie z ustaleniami interakcji z procesem układu.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Rysowanie przykłady <xref:System.Windows.Shapes.Rectangle> — element (`rect1`) jako element podrzędny elementu <xref:System.Windows.Controls.Canvas>. Można zmienić właściwości wysokości <xref:System.Windows.Shapes.Rectangle> przy użyciu szeregu <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, i <xref:System.Windows.FrameworkElement.Height%2A>. W ten sposób priorytet każdej właściwości jest wyświetlana wizualnie.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Poniższe przykłady związane z kodem obsługi zdarzeń, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> wywołuje zdarzenia. Każdy program obsługi przyjmuje dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związane z wysokość. Wartość wysokości są również konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład właściwości wysokości](https://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Ustawianie właściwości szerokości elementu](how-to-set-the-width-properties-of-an-element.md)
- [Panele — omówienie](panels-overview.md)
- [Przykład właściwości wysokości](https://go.microsoft.com/fwlink/?LinkID=159993)
