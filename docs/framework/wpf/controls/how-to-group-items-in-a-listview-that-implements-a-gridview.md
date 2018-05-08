---
title: Jak grupować elementy w ListView, który implementuje GridView
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: 76074449d4ea1454689c51ecad54d7c495f00872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Jak grupować elementy w ListView, który implementuje GridView
W tym przykładzie przedstawiono sposób wyświetlania grup elementów w <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> formantu.  
  
## <a name="example"></a>Przykład  
 Aby wyświetlić grupy elementów w <xref:System.Windows.Controls.ListView>, zdefiniuj <xref:System.Windows.Data.CollectionViewSource>. W poniższym przykładzie przedstawiono <xref:System.Windows.Data.CollectionViewSource> który grupuje elementy danych zgodnie z wartością `Catalog` pola danych.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 W poniższym przykładzie <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.ListView> do <xref:System.Windows.Data.CollectionViewSource> definiujący w poprzednim przykładzie. Definiuje również przykładzie <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> implementującej <xref:System.Windows.Controls.Expander> formantu.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView — omówienie](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView — omówienie](../../../../docs/framework/wpf/controls/gridview-overview.md)
