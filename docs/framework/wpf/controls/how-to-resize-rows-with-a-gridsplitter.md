---
title: Jak zmienić rozmiar wierszy przy użyciu GridSplitter
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 9bd7b073237fa995ac67fe23b616cd54980fbec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554888"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Jak zmienić rozmiar wierszy przy użyciu GridSplitter
Ten przykład przedstawia sposób użycia poziomym <xref:System.Windows.Controls.GridSplitter> ponowne przydzielenie miejsca między wierszami w <xref:System.Windows.Controls.Grid> bez zmieniania wymiary <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Przykład  
 **Jak utworzyć GridSplitter nakładany na krawędzi wiersza**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar wierszy sąsiadujących ze sobą w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Row%2A> dołączona właściwość do jednego z wierszy, które chcesz zmienić. Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jedną kolumnę, ustaw <xref:System.Windows.Controls.Grid.ColumnSpan%2A> dołączona właściwość, aby określić liczbę kolumn. Następnie ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do <xref:System.Windows.VerticalAlignment.Top> lub <xref:System.Windows.VerticalAlignment.Bottom> (wyrównanie, które można ustawić zależy od na dwa wiersze, które chcesz zmienić). Wreszcie, ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 Poniższy przykład przedstawia sposób definiowania poziomej <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar wierszy sąsiadujących ze sobą.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> który nie zajmują swój własny wiersz mogą przesłaniać przez inne formanty <xref:System.Windows.Controls.Grid>. Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Sure upewnij, że GridSplitter jest widoczny](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Jak utworzyć GridSplitter, która zajmuje wiersza**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> który zajmuje wiersza w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Row%2A> dołączona właściwość do jednego z wierszy, które chcesz zmienić. Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jedną kolumnę, ustaw <xref:System.Windows.Controls.Grid.ColumnSpan%2A> dołączona właściwość do liczby kolumn. Następnie ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> do <xref:System.Windows.VerticalAlignment.Center>ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Stretch>i ustaw <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersza, który zawiera <xref:System.Windows.Controls.GridSplitter> do <xref:System.Windows.GridLength.Auto%2A>.  
  
 Poniższy przykład przedstawia sposób definiowania poziomej <xref:System.Windows.Controls.GridSplitter> zajmuje wiersza i zmienia rozmiar wierszy na każdej stronie.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridSplitter>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
