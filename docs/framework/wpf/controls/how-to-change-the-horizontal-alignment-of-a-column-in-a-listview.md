---
title: Jak zmienić wyrównanie w poziomie kolumny w ListView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 5447f1a73b008b2ed4f345eba00f4d631e11e257
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458608"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Jak zmienić wyrównanie w poziomie kolumny w ListView
Domyślnie zawartość każdej kolumny w <xref:System.Windows.Controls.ListViewItem> jest wyrównana do lewej. Można zmienić wyrównanie każdej kolumny, dostarczając <xref:System.Windows.DataTemplate> i ustawiając właściwość <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> dla elementu w <xref:System.Windows.DataTemplate>. W tym temacie pokazano, jak <xref:System.Windows.Controls.ListView> domyślnie wyrównuje swoją zawartość oraz jak zmienić wyrównanie jednej kolumny w <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dane w `Title` i `ISBN` kolumny są wyrównane do lewej.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aby zmienić wyrównanie kolumny `ISBN`, należy określić, że właściwość <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> każdej <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.HorizontalAlignment.Stretch>, tak aby elementy w każdym <xref:System.Windows.Controls.ListViewItem> mogły obejmować lub być rozmieszczone wzdłuż całej szerokości każdej kolumny. Ponieważ <xref:System.Windows.Controls.ListView> jest powiązany ze źródłem danych, należy utworzyć styl ustawiający <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Następnie należy użyć <xref:System.Windows.DataTemplate>, aby wyświetlić zawartość zamiast używać właściwości <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>. Aby wyświetlić `ISBN` każdego szablonu, <xref:System.Windows.DataTemplate> może zawierać <xref:System.Windows.Controls.TextBlock>, który ma właściwość <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ustawioną na <xref:System.Windows.HorizontalAlignment.Right>.  
  
 W poniższym przykładzie zdefiniowano styl i <xref:System.Windows.DataTemplate> konieczne, aby kolumna `ISBN` była wyrównana do prawej strony, i zmieni <xref:System.Windows.Controls.GridViewColumn>, aby odwoływała się do <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](listview-overview.md)
