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
ms.openlocfilehash: 467cd57c728be015fb9eb9b974ca6e81e4fd7754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554862"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Jak ustawić właściwości wysokości elementu
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie spośród czterech właściwości związanych z wysokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują cechy wysokość elementu. Te właściwości cztery mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określane w następujący sposób: <xref:System.Windows.FrameworkElement.MinHeight%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxHeight%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Height%2A> wartość. Właściwość czwarty <xref:System.Windows.FrameworkElement.ActualHeight%2A>, jest tylko do odczytu i raporty rzeczywista wysokość ustalany na podstawie interakcji z procesem układu.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysowania <xref:System.Windows.Shapes.Rectangle> elementu (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>. Można zmienić właściwości wysokość <xref:System.Windows.Shapes.Rectangle> przy użyciu serii <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, i <xref:System.Windows.FrameworkElement.Height%2A>. W ten sposób pierwszeństwo każdej właściwości wizualnie jest wyświetlany.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 W poniższych przykładach kodu powiązanego obsługiwać zdarzenia który <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zgłasza zdarzenie. Każdy program obsługi pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związanych z wysokość. Wysokość wartości są również konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Pełny przykład, zobacz [przykład właściwości wysokość](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [Ustawianie właściwości szerokości elementu](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Przykład właściwości Height](http://go.microsoft.com/fwlink/?LinkID=159993)
