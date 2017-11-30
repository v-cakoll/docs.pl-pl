---
title: "Jak zmienić wyrównanie w poziomie kolumny w ListView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ed163de9a5b01a3ddab8ef42d21f38d35f48519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Jak zmienić wyrównanie w poziomie kolumny w ListView
Domyślnie, zawartości każdej kolumny w <xref:System.Windows.Controls.ListViewItem> jest wyrównany. Wyrównanie każdej kolumny można zmienić, zapewniając <xref:System.Windows.DataTemplate> i ustawienie <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości w elemencie <xref:System.Windows.DataTemplate>. W tym temacie przedstawiono sposób <xref:System.Windows.Controls.ListView> Wyrównuje zawartość domyślnie i jak zmienić wyrównania jednej kolumny w <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie danych w `Title` i `ISBN` kolumn jest wyrównany.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Aby zmienić wyrównania `ISBN` kolumny, należy określić, że <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> właściwości każdego <xref:System.Windows.Controls.ListViewItem> jest <xref:System.Windows.HorizontalAlignment.Stretch>, tak aby elementy w każdym <xref:System.Windows.Controls.ListViewItem> może obejmować lub ją wzdłuż całego szerokość każdej kolumny. Ponieważ <xref:System.Windows.Controls.ListView> jest powiązany ze źródłem danych, należy utworzyć styl, który ustawia <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Następnie należy użyć <xref:System.Windows.DataTemplate> do wyświetlania zawartości zamiast <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> właściwości. Aby wyświetlić `ISBN` każdego szablonu <xref:System.Windows.DataTemplate> może zawierać tylko <xref:System.Windows.Controls.TextBlock> mający jego <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ustawioną właściwość <xref:System.Windows.HorizontalAlignment.Right>.  
  
 W poniższym przykładzie zdefiniowano styl i <xref:System.Windows.DataTemplate> dokonanie `ISBN` kolumny wyrównany do prawej, a zmiany <xref:System.Windows.Controls.GridViewColumn> do odwołania <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Powiązania danych XML przy użyciu XMLDataProvider i kwerendy XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)
