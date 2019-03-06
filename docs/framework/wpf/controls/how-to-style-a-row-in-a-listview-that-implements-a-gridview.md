---
title: 'Instrukcje: Nadaj styl wierszowi w ListView, który implementuje GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 0c8806c399959fdc1466e0839ba469881718092b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361632"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Instrukcje: Nadaj styl wierszowi w ListView, który implementuje GridView
W tym przykładzie pokazano, jak styl wierszowi w <xref:System.Windows.Controls.ListView> formant, który implementuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> trybu.  
  
## <a name="example"></a>Przykład  
 Można styl wierszowi w <xref:System.Windows.Controls.ListView> kontroli przez ustawienie <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na <xref:System.Windows.Controls.ListView> kontroli. Ustaw styl dla jego elementów, które są reprezentowane jako <xref:System.Windows.Controls.ListViewItem> obiektów. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odwołania <xref:System.Windows.Controls.ControlTemplate> obiekty, które są używane do wyświetlania zawartości wiersza.  
  
 Pełny przykład, poniższe przykłady są wyodrębniane z, wyświetla zbiór informacji utworu, która jest przechowywana w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bazy danych. Każdy utwór w bazie danych znajduje się pole klasyfikacji i wartość tego pola określa sposób wyświetlania wiersz utworu informacji.  
  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> dla <xref:System.Windows.Controls.ListViewItem> obiekty reprezentujące utworów muzycznych w kolekcji utworu. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odwołania <xref:System.Windows.Controls.ControlTemplate> obiekty, które określają sposób wyświetlania wiersz utworu informacji.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.ControlTemplate> dodająca ciąg tekstowy `"Strongly Recommended"` do wiersza. Ten szablon jest przywoływany w <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> i wyświetla gdy utwór ocena ma wartość 5 (pięć). <xref:System.Windows.Controls.ControlTemplate> Obejmuje <xref:System.Windows.Controls.GridViewRowPresenter> obiekt, który układa zawartość wiersza w kolumnach, zgodnie z definicją <xref:System.Windows.Controls.GridView> trybu wyświetlania.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Tematy z instrukcjami](listview-how-to-topics.md)
- [ListView — omówienie](listview-overview.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
