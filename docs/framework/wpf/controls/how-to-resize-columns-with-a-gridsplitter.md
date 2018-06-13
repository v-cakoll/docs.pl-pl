---
title: Jak zmienić rozmiar kolumn przy użyciu GridSplitter
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: b4652c06cfe6f048f6c75a11b9447d70d6820e4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556153"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Jak zmienić rozmiar kolumn przy użyciu GridSplitter
W tym przykładzie przedstawiono sposób tworzenia pionowym <xref:System.Windows.Controls.GridSplitter> Aby ponownie rozesłać odstęp między kolumnami w <xref:System.Windows.Controls.Grid> bez zmieniania wymiary <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Przykład  
 **Jak utworzyć GridSplitter nakładany na krawędzi kolumny**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar kolumn sąsiadujących ze sobą w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Column%2A> dołączona właściwość do jednej z kolumn, które chcesz zmienić. Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jeden wiersz, ustaw <xref:System.Windows.Controls.Grid.RowSpan%2A> dołączona właściwość liczby wierszy. Następnie ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Left> lub <xref:System.Windows.HorizontalAlignment.Right> (wyrównanie, które można ustawić zależy od na dwie kolumny, które chcesz zmienić). Wreszcie, ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> , która nie ma kolumny może być zasłonięty przez inne formanty w <xref:System.Windows.Controls.Grid>. Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Sure upewnij, że GridSplitter jest widoczny](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Jak utworzyć GridSplitter, która zajmuje kolumny**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> który zajmuje kolumny w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Column%2A> dołączona właściwość do jednej z kolumn, które chcesz zmienić. Jeśli siatka ma więcej niż jeden wiersz, ustaw <xref:System.Windows.Controls.Grid.RowSpan%2A> dołączona właściwość liczby wierszy. Następnie ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> do <xref:System.Windows.HorizontalAlignment.Center>ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.VerticalAlignment.Stretch>i ustaw <xref:System.Windows.Controls.ColumnDefinition.Width%2A> kolumny, która zawiera <xref:System.Windows.Controls.GridSplitter> do <xref:System.Windows.GridLength.Auto%2A>.  
  
 Poniższy przykład przedstawia sposób definiowania pionowym <xref:System.Windows.Controls.GridSplitter> zajmuje kolumny i zmienia rozmiar kolumn po obu stronach.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridSplitter>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
