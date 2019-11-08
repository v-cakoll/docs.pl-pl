---
title: Jak nadać styl wierszowi w ListView, który implementuje GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: ce79899d5c8e825ecb39e14ae8af4e0c33f13db3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733543"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Jak nadać styl wierszowi w ListView, który implementuje GridView
Ten przykład pokazuje, jak stylować wiersz w kontrolce <xref:System.Windows.Controls.ListView> implementującej tryb <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>.  
  
## <a name="example"></a>Przykład  
 Aby określić styl wiersza w kontrolce <xref:System.Windows.Controls.ListView>, należy ustawić <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> kontrolki <xref:System.Windows.Controls.ListView>. Ustaw styl dla elementów, które są reprezentowane jako obiekty <xref:System.Windows.Controls.ListViewItem>. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> odwołuje się do obiektów <xref:System.Windows.Controls.ControlTemplate>, które są używane do wyświetlania zawartości wiersza.  
  
 Kompletny przykład, w którym następujące przykłady są wyodrębniane z programu, wyświetla kolekcję informacji o utworze, które są przechowywane w bazie danych XML. Każdy utwór w bazie danych ma pole Rating i wartość tego pola określa sposób wyświetlania wiersza informacji o utworze.  
  
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
