---
title: 'Instrukcje: Grupowanie elementów w kontrolce ListView z implementacją GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], grouping items with GridViews
- grouping items in ListViews implementing GridViews [WPF]
- GridView controls [WPF], grouping items
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
ms.openlocfilehash: b3dd6891976a942b299c87fca25e430e9ee59a51
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177674"
---
# <a name="how-to-group-items-in-a-listview-that-implements-a-gridview"></a>Instrukcje: Grupowanie elementów w kontrolce ListView z implementacją GridView
W tym przykładzie przedstawiono sposób wyświetlania grup elementów na liście <xref:System.Windows.Controls.GridView> tryb widoku <xref:System.Windows.Controls.ListView> kontroli.  
  
## <a name="example"></a>Przykład  
 Aby wyświetlić grupy elementów na liście <xref:System.Windows.Controls.ListView>, zdefiniuj <xref:System.Windows.Data.CollectionViewSource>. W poniższym przykładzie przedstawiono <xref:System.Windows.Data.CollectionViewSource> która grupuje elementy danych zgodnie z wartością `Catalog` pola danych.  
  
 [!code-xaml[GridViewWithGroups#GroupingCollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 Poniższy przykład ustawia <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.ListView> do <xref:System.Windows.Data.CollectionViewSource> definiujący w poprzednim przykładzie. Przykładzie zdefiniowano też <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> implementującej <xref:System.Windows.Controls.Expander> kontroli.  
  
 [!code-xaml[GridViewWithGroups#ListViewGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xaml[GridViewWithGroups#ListViewEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [— Tematy porad](listview-how-to-topics.md)
- [ListView — Przegląd](listview-overview.md)
- [GridView — Przegląd](gridview-overview.md)
