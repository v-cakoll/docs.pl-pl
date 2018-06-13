---
title: Jak sortować dane w widoku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 5c79261983fcf6200120bcfbf180d155aca3c3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556760"
---
# <a name="how-to-sort-data-in-a-view"></a>Jak sortować dane w widoku
W tym przykładzie przedstawiono sposób sortowania danych w widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy prosty <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obsługi zdarzeń przycisku zawiera logikę do sortowania elementów w <xref:System.Windows.Controls.ListBox> w kolejności malejącej. Można to zrobić, ponieważ dodawanie elementów do <xref:System.Windows.Controls.ListBox> w ten sposób dodanie ich do <xref:System.Windows.Controls.ItemCollection> z <xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.ItemCollection> pochodną <xref:System.Windows.Data.CollectionView> klasy. Są wiązane z <xref:System.Windows.Controls.ListBox> do kolekcji przy użyciu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości, tę samą metodę można użyć do sortowania.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Istnieje odwołanie do obiektu widoku używasz tę samą metodę sortowania zawartości z innymi widokami kolekcji. Na przykład sposobu uzyskiwania widoku zobacz [uzyskać widok domyślny zbierania danych](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Na przykład innego, zobacz [sortowania w widoku GridView kolumny po kliknięciu nagłówka](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Aby uzyskać więcej informacji o widokach, zobacz powiązania do kolekcji w [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Przykład sposobu zastosował logikę sortowania [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], zobacz [sortowania i grupy danych przy użyciu widoku w języku XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [Sortowanie kolumny GridView po kliknięciu nagłówka](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Filtrowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
