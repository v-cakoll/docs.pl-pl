---
title: Jak nadać styl wierszowi w ListView, który implementuje GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459321"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Jak nadać styl wierszowi w ListView, który implementuje GridView
Ten przykład pokazuje, jak stylować wiersz w kontrolce <xref:System.Windows.Controls.ListView> implementującej tryb <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>.  
  
## <a name="example"></a>Przykład  
 Aby określić styl wiersza w kontrolce <xref:System.Windows.Controls.ListView>, należy ustawić <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> kontrolki <xref:System.Windows.Controls.ListView>. Ustaw styl dla elementów, które są reprezentowane jako obiekty <xref:System.Windows.Controls.ListViewItem>. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> odwołuje się do obiektów <xref:System.Windows.Controls.ControlTemplate>, które są używane do wyświetlania zawartości wiersza.  
  
 Kompletny przykład, w którym następujące przykłady są wyodrębniane z programu, zawiera kolekcję informacji o utworze, które są przechowywane w bazie danych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Każdy utwór w bazie danych ma pole Rating i wartość tego pola określa sposób wyświetlania wiersza informacji o utworze.  
  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla obiektów <xref:System.Windows.Controls.ListViewItem>, które reprezentują utwory w kolekcji Song. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> odwołuje się do obiektów <xref:System.Windows.Controls.ControlTemplate>, które określają sposób wyświetlania wiersza informacji o utworze.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Poniższy przykład pokazuje <xref:System.Windows.Controls.ControlTemplate>, który dodaje ciąg tekstowy `"Strongly Recommended"` do wiersza. Ten szablon jest przywoływany w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> i wyświetla, gdy klasyfikacja utworu ma wartość 5 (pięć). <xref:System.Windows.Controls.ControlTemplate> zawiera <xref:System.Windows.Controls.GridViewRowPresenter> obiekt, który określa zawartość wiersza w kolumnach, zgodnie z definicją w trybie widoku <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tematy z instrukcjami](listview-how-to-topics.md)
- [ListView — omówienie](listview-overview.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
