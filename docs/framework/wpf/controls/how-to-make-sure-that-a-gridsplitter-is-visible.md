---
title: 'Instrukcje: Upewnianie się, że kontrolka GridSplitter jest widoczna'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 2085ac5cec206d8692a1267acf132688f0aa9082
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663318"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Instrukcje: Upewnianie się, że kontrolka GridSplitter jest widoczna
W tym przykładzie pokazano, jak upewnić się, że <xref:System.Windows.Controls.GridSplitter> kontrolki nie jest ukryty przez inne formanty w <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Panel.Children%2A> z <xref:System.Windows.Controls.Grid> kontroli — zostaną zrenderowane w kolejności, że są zdefiniowane w znaczników lub innego kodu. <xref:System.Windows.Controls.GridSplitter> Formanty może być ukryte przez inne formanty, jeżeli nie zdefiniujesz jako ostatnie elementy <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lub jeśli musisz udzielić inne kontrolki wyższe <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Aby zapobiec ukryte <xref:System.Windows.Controls.GridSplitter> formantów, wykonaj jedną z następujących czynności.  
  
- Upewnij się, że <xref:System.Windows.Controls.GridSplitter> formanty są ostatniego <xref:System.Windows.Controls.Panel.Children%2A> dodane do <xref:System.Windows.Controls.Grid>. W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.GridSplitter> jako po ostatnim elemencie w <xref:System.Windows.Controls.Panel.Children%2A> zbiór <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
- Ustaw <xref:System.Windows.Controls.Panel.ZIndexProperty> na <xref:System.Windows.Controls.GridSplitter> większe niż kontrolki, które w przeciwnym razie spowoduje ukrycie. Poniższy przykład daje <xref:System.Windows.Controls.GridSplitter> kontrolować wyższe <xref:System.Windows.Controls.Panel.ZIndexProperty> niż <xref:System.Windows.Controls.Button> kontroli.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
- Ustaw marginesy kontrolki, które w przeciwnym razie spowoduje ukrycie <xref:System.Windows.Controls.GridSplitter> tak, aby <xref:System.Windows.Controls.GridSplitter> jest widoczna. W poniższym przykładzie ustawiono marginesów zaznaczania kontrolki, które w przeciwnym razie mogłyby nakładki i Ukryj <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.GridSplitter>
- [Tematy z instrukcjami](gridsplitter-how-to-topics.md)
