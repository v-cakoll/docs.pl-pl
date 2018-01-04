---
title: "Jak zmienić rozmiar wierszy przy użyciu GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d4cf06a86a1da7bb34074623f8f19f4bda7a724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
