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
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454825"
---
# <a name="how-to-sort-data-in-a-view"></a>Jak sortować dane w widoku
W tym przykładzie opisano sposób sortowania danych w widoku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy proste <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 Procedura obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> przycisku zawiera logikę do sortowania elementów w <xref:System.Windows.Controls.ListBox> w kolejności malejącej. Można to zrobić, ponieważ dodawanie elementów do <xref:System.Windows.Controls.ListBox> w ten sposób dodaje je do <xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.ItemCollection> pochodzi od klasy <xref:System.Windows.Data.CollectionView>. Jeśli powiążesz <xref:System.Windows.Controls.ListBox> z kolekcją przy użyciu właściwości <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, możesz użyć tej samej techniki do sortowania.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Tak długo, jak masz odwołanie do obiektu widoku, możesz użyć tej samej techniki, aby posortować zawartość innych widoków kolekcji. Aby zapoznać się z przykładem, jak uzyskać widok, zobacz temat [pobieranie widoku domyślnego kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md). Aby uzyskać inny przykład, zobacz [Sortowanie kolumny GridView po kliknięciu nagłówka](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Aby uzyskać więcej informacji o widokach, zobacz powiązanie z kolekcjami w temacie [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Aby zapoznać się z przykładem zastosowania logiki sortowania w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], zobacz [Sortowanie i grupowanie danych przy użyciu widoku w języku XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Sortowanie kolumny GridView po kliknięciu nagłówka](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Filtrowanie danych w widoku](how-to-filter-data-in-a-view.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
