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
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459703"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Jak przejść do obiektów w danych CollectionView
Widoki umożliwiają wyświetlanie tych samych danych na różne sposoby, w zależności od sortowania, filtrowania lub grupowania. Widoki udostępniają również bieżące koncepcje wskaźnika rekordu i umożliwiają przeniesienie wskaźnika. Ten przykład pokazuje, jak pobrać bieżący obiekt, a także nawigować przez obiekty w kolekcji danych przy użyciu funkcji udostępnionych w klasie <xref:System.Windows.Data.CollectionView>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `myCollectionView` jest obiektem <xref:System.Windows.Data.CollectionView>, który jest widokiem w kolekcji powiązanej.  
  
 W poniższym przykładzie `OnButton` jest program obsługi zdarzeń dla przycisków `Previous` i `Next` w aplikacji, które są przyciskami, które umożliwiają użytkownikowi nawigowanie po kolekcji danych. Należy zauważyć, że właściwości <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> i <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> raportują, czy bieżący wskaźnik rekordu został osiągnięty na początku i na końcu listy, aby <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> i <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> można było odpowiednio wywołać.  
  
 Właściwość <xref:System.Windows.Data.CollectionView.CurrentItem%2A> widoku jest rzutowana jako `Order` do zwrócenia bieżącego elementu Order w kolekcji.  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Sortowanie danych w widoku](how-to-sort-data-in-a-view.md)
- [Filtrowanie danych w widoku](how-to-filter-data-in-a-view.md)
- [Sortowanie i grupowanie danych przy użyciu widoku w XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
