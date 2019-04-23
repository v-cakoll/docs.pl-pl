---
title: 'Instrukcje: Zmienianie wyrównania w poziomie kolumny w kontrolce ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 528a711c1cf7992bb32c0aa4d6e81d71744c9f80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102664"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Instrukcje: Zmienianie wyrównania w poziomie kolumny w kontrolce ListView
Domyślnie zawartość każdej kolumny w <xref:System.Windows.Controls.ListViewItem> jest wyrównany do lewej. Można zmienić wyrównanie każdej kolumny, zapewniając <xref:System.Windows.DataTemplate> i ustawienie <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości w elemencie <xref:System.Windows.DataTemplate>. W tym temacie przedstawiono sposób <xref:System.Windows.Controls.ListView> Wyrównuje zawartość domyślnie i jak zmienić wyrównanie jedna kolumna w <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dane w `Title` i `ISBN` kolumn jest wyrównany do lewej.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aby zmienić wyrównanie `ISBN` kolumnę, musisz określić, że <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości każdego <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.HorizontalAlignment.Stretch>, dzięki czemu elementy w każdym <xref:System.Windows.Controls.ListViewItem> może obejmować lub ją wraz z całą szerokość każdej kolumny. Ponieważ <xref:System.Windows.Controls.ListView> jest powiązana ze źródłem danych, musisz utworzyć styl, który ustawia <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Następnie należy użyć <xref:System.Windows.DataTemplate> do wyświetlania zawartości zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości. Aby wyświetlić `ISBN` każdego szablonu <xref:System.Windows.DataTemplate> może tylko zawierać <xref:System.Windows.Controls.TextBlock> zawierający jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwością <xref:System.Windows.HorizontalAlignment.Right>.  
  
 W poniższym przykładzie zdefiniowano styl i <xref:System.Windows.DataTemplate> to niezbędne do zapewnienia `ISBN` wyrównany do prawej kolumny, a zmiany <xref:System.Windows.Controls.GridViewColumn> do odwołania <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../data/data-templating-overview.md)
- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](listview-overview.md)
