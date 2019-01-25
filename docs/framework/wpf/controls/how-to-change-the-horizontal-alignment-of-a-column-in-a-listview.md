---
title: 'Instrukcje: Zmień wyrównanie w poziomie kolumny w ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 07d5fd0830f98032e76b963cb32b35fd18b50475
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605230"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Instrukcje: Zmień wyrównanie w poziomie kolumny w ListView
Domyślnie zawartość każdej kolumny w <xref:System.Windows.Controls.ListViewItem> jest wyrównany do lewej. Można zmienić wyrównanie każdej kolumny, zapewniając <xref:System.Windows.DataTemplate> i ustawienie <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości w elemencie <xref:System.Windows.DataTemplate>. W tym temacie przedstawiono sposób <xref:System.Windows.Controls.ListView> Wyrównuje zawartość domyślnie i jak zmienić wyrównanie jedna kolumna w <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dane w `Title` i `ISBN` kolumn jest wyrównany do lewej.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aby zmienić wyrównanie `ISBN` kolumnę, musisz określić, że <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości każdego <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.HorizontalAlignment.Stretch>, dzięki czemu elementy w każdym <xref:System.Windows.Controls.ListViewItem> może obejmować lub ją wraz z całą szerokość każdej kolumny. Ponieważ <xref:System.Windows.Controls.ListView> jest powiązana ze źródłem danych, musisz utworzyć styl, który ustawia <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Następnie należy użyć <xref:System.Windows.DataTemplate> do wyświetlania zawartości zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości. Aby wyświetlić `ISBN` każdego szablonu <xref:System.Windows.DataTemplate> może tylko zawierać <xref:System.Windows.Controls.TextBlock> zawierający jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwością <xref:System.Windows.HorizontalAlignment.Right>.  
  
 W poniższym przykładzie zdefiniowano styl i <xref:System.Windows.DataTemplate> to niezbędne do zapewnienia `ISBN` wyrównany do prawej kolumny, a zmiany <xref:System.Windows.Controls.GridViewColumn> do odwołania <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Szablonowanie danych — omówienie](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)
