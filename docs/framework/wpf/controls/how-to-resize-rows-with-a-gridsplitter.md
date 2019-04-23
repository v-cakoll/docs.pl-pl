---
title: 'Instrukcje: Zmienianie rozmiaru wierszy przy użyciu GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 6760a7a691af4f666294556cae3bc95a4299730a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074277"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Instrukcje: Zmienianie rozmiaru wierszy przy użyciu GridSplitter
W tym przykładzie pokazano, jak używać poziomej <xref:System.Windows.Controls.GridSplitter> Redystrybucja odstęp między dwa wiersze w <xref:System.Windows.Controls.Grid> bez konieczności zmieniania wymiary <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Przykład  
 **Jak utworzyć GridSplitter nakładany na krawędzi wiersza**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar sąsiadujących wierszy w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Row%2A> dołączona właściwość do jednej z tych wierszy, które chcesz zmienić. Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jedną kolumnę, ustaw <xref:System.Windows.Controls.Grid.ColumnSpan%2A> dołączonych właściwości w celu określenia liczby kolumn. Następnie ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do <xref:System.Windows.VerticalAlignment.Top> lub <xref:System.Windows.VerticalAlignment.Bottom> (wyrównanie, które można ustawić w zależności na dwa wiersze, które chcesz zmienić). Wreszcie, ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwość <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 Poniższy przykład pokazuje jak zdefiniować poziomy <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar sąsiadujących wierszy.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> , nie zajmują swój własny wiersz mogą być zasłonięte przez inne formanty w czyste <xref:System.Windows.Controls.Grid>. Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [upewnij się, że GridSplitter jest widoczny](how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Jak utworzyć GridSplitter, która zajmuje wiersz**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> , zajmuje wiersza w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Row%2A> dołączona właściwość do jednej z tych wierszy, które chcesz zmienić. Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jedną kolumnę, ustaw <xref:System.Windows.Controls.Grid.ColumnSpan%2A> dołączona właściwość do liczby kolumn. Następnie ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do <xref:System.Windows.VerticalAlignment.Center>ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Stretch>i ustaw <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersza, który zawiera <xref:System.Windows.Controls.GridSplitter> do <xref:System.Windows.GridLength.Auto%2A>.  
  
 Poniższy przykład pokazuje jak zdefiniować poziomy <xref:System.Windows.Controls.GridSplitter> , zajmuje wiersza i zmienia rozmiar wierszy po obu stronach.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.GridSplitter>
- [Tematy z instrukcjami](gridsplitter-how-to-topics.md)
