---
title: 'Instrukcje: Pobierz domyślny widok kolekcji danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: 386c25998c85de2f674200fe7d269ae2fdabd72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588408"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Instrukcje: Pobierz domyślny widok kolekcji danych
Widoki zezwala na tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od tego, czy sortowanie, filtrowanie lub kryteria grupowania. Każda kolekcja ma jeden udostępnionego widok domyślny, jest używany jako źródło faktycznego wiązania, gdy powiązanie Określa kolekcję jako źródło. Ten przykład pokazuje, jak pobrać domyślny widok kolekcji.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć widok, konieczne jest odwołanie do obiektu w kolekcji. Ten obiekt danych można uzyskać, odwołując się do własnego obiektu związanego z kodem, uzyskując kontekst danych, pobieranie właściwości źródła danych lub pobieranie właściwości powiązania. W tym przykładzie pokazano, jak uzyskać <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu danych i użyć go bezpośrednio uzyskać domyślnej kolekcji wyświetlić dla tej kolekcji.  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 W tym przykładzie jest głównym elementem <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> Ustawiono *myDataSource*, która odnosi się do dostawcy danych, który jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z *kolejności* obiektów.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternatywnie możesz utworzyć wystąpienia i powiązać z własną kolekcję widoku przy użyciu <xref:System.Windows.Data.CollectionViewSource> klasy. Ten widok kolekcji jest udostępniany tylko przez formanty, które należy powiązać go bezpośrednio. Aby uzyskać przykład, zobacz, jak do utworzenia widoku w temacie [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Przykłady funkcje udostępniane przez widok kolekcji, zobacz [sortowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrować dane w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), i [przejdź do obiektów w danych CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Sortowanie i grupowanie danych przy użyciu widoku w XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
