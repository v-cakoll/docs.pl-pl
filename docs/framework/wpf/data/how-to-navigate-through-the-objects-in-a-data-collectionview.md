---
title: Jak przejść do obiektów w danych CollectionView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: ec78b7350d23364cfb0eaa9a0611be8449073cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Jak przejść do obiektów w danych CollectionView
Widoki zezwolić tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od sortowania, filtrowania lub grupowania. Widoki również podać pojęcie bieżącego rekordu wskaźnik i włączyć, przesuń wskaźnik. W tym przykładzie pokazano, jak pobrać bieżący obiekt, a także przejdź do obiektów w kolekcji danych, korzystając z funkcji dostępnych w <xref:System.Windows.Data.CollectionView> klasy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `myCollectionView` jest <xref:System.Windows.Data.CollectionView> obiekt, który jest widokiem za pośrednictwem powiązanej kolekcji.  
  
 W poniższym przykładzie `OnButton` jest program obsługi zdarzeń dla `Previous` i `Next` przycisków w aplikacji, które są przyciski, który umożliwia użytkownikowi nawigację zbierania danych. Należy pamiętać, że <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> i <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> właściwości raportu, czy bieżący wskaźnik rekordów do trybu na początku i na końcu listy odpowiednio tak że <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> i <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> można wywołać jako odpowiednio.  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> Właściwości widoku jest rzutowany jako `Order` aby powrócić do bieżącego elementu kolejności w kolekcji.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Sortowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Filtrowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Sortowanie i grupowanie danych przy użyciu widoku w XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
