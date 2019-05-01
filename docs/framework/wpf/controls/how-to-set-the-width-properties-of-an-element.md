---
title: 'Instrukcje: Ustawianie właściwości szerokości elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: a5ed67ba20176398a863a1e9826b1eab71b182f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052043"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Instrukcje: Ustawianie właściwości szerokości elementu
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie między cztery właściwości związane z szerokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują właściwości szerokości elementu. Te cztery właściwości mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określany w następujący sposób: <xref:System.Windows.FrameworkElement.MinWidth%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxWidth%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Width%2A> wartość. Czwarty właściwość <xref:System.Windows.FrameworkElement.ActualWidth%2A>, jest tylko do odczytu i zgłasza rzeczywista szerokość zgodnie z ustaleniami interakcji z procesem układu.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Rysowanie przykłady <xref:System.Windows.Shapes.Rectangle> — element (`rect1`) jako element podrzędny elementu <xref:System.Windows.Controls.Canvas>. Można zmienić właściwości szerokości <xref:System.Windows.Shapes.Rectangle> przy użyciu szeregu <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, i <xref:System.Windows.FrameworkElement.Width%2A>. W ten sposób priorytet każdej właściwości jest wyświetlana wizualnie.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Poniższe przykłady związane z kodem obsługi zdarzeń, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> wywołuje zdarzenia. Każda metoda niestandardowego pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związane z szerokości. Wartości szerokości również jest konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład porównania właściwości szerokości](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Panele — omówienie](panels-overview.md)
- [Ustawianie właściwości wysokości elementu](how-to-set-the-height-properties-of-an-element.md)
- [Przykładowe porównanie właściwości szerokości](https://go.microsoft.com/fwlink/?LinkID=160050)
