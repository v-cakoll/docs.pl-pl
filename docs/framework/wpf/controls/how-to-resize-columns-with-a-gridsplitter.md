---
title: 'Instrukcje: Zmienianie rozmiaru kolumn przy użyciu GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: f743e9ccf8a984a646a4b8f05ee99162e5bc73ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210441"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Instrukcje: Zmienianie rozmiaru kolumn przy użyciu GridSplitter
W tym przykładzie przedstawiono sposób tworzenia pionowej <xref:System.Windows.Controls.GridSplitter> w celu rozpowszechniania odstęp między kolumnami w <xref:System.Windows.Controls.Grid> bez konieczności zmieniania wymiary <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Przykład  
 **Jak utworzyć GridSplitter nakładany na krawędzi kolumny**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar przyległe kolumny w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Column%2A> dołączona właściwość do jednej z kolumn, które chcesz zmienić. Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jeden wiersz, ustaw <xref:System.Windows.Controls.Grid.RowSpan%2A> dołączona właściwość liczby wierszy. Następnie ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Left> lub <xref:System.Windows.HorizontalAlignment.Right> (wyrównanie, które można ustawić w zależności na dwie kolumny, które chcesz zmienić). Wreszcie, ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwość <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> nie ma swoje własne kolumny mogą być zasłonięte przez inne formanty w czyste <xref:System.Windows.Controls.Grid>. Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [upewnij się, że GridSplitter jest widoczny](how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Jak utworzyć GridSplitter, która zajmuje kolumny**  
  
 Aby określić <xref:System.Windows.Controls.GridSplitter> , zajmuje kolumny <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Column%2A> dołączona właściwość do jednej z kolumn, które chcesz zmienić. Jeśli Twoje Siatka zawiera więcej niż jeden wiersz, ustaw <xref:System.Windows.Controls.Grid.RowSpan%2A> dołączona właściwość liczby wierszy. Następnie ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> do <xref:System.Windows.HorizontalAlignment.Center>ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.VerticalAlignment.Stretch>i ustaw <xref:System.Windows.Controls.ColumnDefinition.Width%2A> kolumny, zawierającej <xref:System.Windows.Controls.GridSplitter> do <xref:System.Windows.GridLength.Auto%2A>.  
  
 Poniższy przykład pokazuje jak zdefiniować pionowej <xref:System.Windows.Controls.GridSplitter> , zajmuje kolumny i zmienia rozmiar kolumn po obu stronach.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.GridSplitter>
- [— Tematy porad](gridsplitter-how-to-topics.md)
