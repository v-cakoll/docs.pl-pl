---
title: Jak filtrować dane w widoku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: ea49897ca5e9cb6b639cf7d98ff05bd287c51761
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453484"
---
# <a name="how-to-filter-data-in-a-view"></a>Jak filtrować dane w widoku
Ten przykład przedstawia sposób filtrowania danych w widoku.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć filtr, zdefiniuj metodę, która udostępnia logikę filtrowania. Metoda jest używana jako wywołanie zwrotne i akceptuje parametr typu `object`. Poniższa metoda zwraca wszystkie obiekty `Order` z właściwością `filled` ustawioną na wartość "No", filtrując pozostałe obiekty.  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Następnie można zastosować filtr, jak pokazano w poniższym przykładzie. W tym przykładzie `myCollectionView` jest obiektem <xref:System.Windows.Data.ListCollectionView>.  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Aby cofnąć filtrowanie, można ustawić właściwość <xref:System.Windows.Data.CollectionView.Filter%2A> na `null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Aby uzyskać informacje na temat sposobu tworzenia lub uzyskiwania widoku, zobacz temat [pobieranie widoku domyślnego kolekcji danych](how-to-get-the-default-view-of-a-data-collection.md). Aby zapoznać się z kompletnym przykładem, zobacz [Sortowanie i Filtrowanie elementów w przykładowym widoku](https://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Jeśli obiekt widoku pochodzi z obiektu <xref:System.Windows.Data.CollectionViewSource>, należy zastosować logikę filtrowania, ustawiając procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Data.CollectionViewSource.Filter>. W poniższym przykładzie `listingDataView` jest wystąpieniem <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Poniżej przedstawiono implementację przykładu procedury obsługi zdarzeń filtru `ShowOnlyBargainsFilter`. Ten program obsługi zdarzeń używa właściwości <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> do odfiltrowania `AuctionItem` obiektów, które mają `CurrentPrice` $25 lub więcej.  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Sortowanie danych w widoku](how-to-sort-data-in-a-view.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
