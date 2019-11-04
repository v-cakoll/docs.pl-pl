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
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="3c92d-102">Jak przejść do obiektów w danych CollectionView</span><span class="sxs-lookup"><span data-stu-id="3c92d-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="3c92d-103">Widoki umożliwiają wyświetlanie tych samych danych na różne sposoby, w zależności od sortowania, filtrowania lub grupowania.</span><span class="sxs-lookup"><span data-stu-id="3c92d-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="3c92d-104">Widoki udostępniają również bieżące koncepcje wskaźnika rekordu i umożliwiają przeniesienie wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="3c92d-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="3c92d-105">Ten przykład pokazuje, jak pobrać bieżący obiekt, a także nawigować przez obiekty w kolekcji danych przy użyciu funkcji udostępnionych w klasie <xref:System.Windows.Data.CollectionView>.</span><span class="sxs-lookup"><span data-stu-id="3c92d-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c92d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c92d-106">Example</span></span>  
 <span data-ttu-id="3c92d-107">W tym przykładzie `myCollectionView` jest obiektem <xref:System.Windows.Data.CollectionView>, który jest widokiem w kolekcji powiązanej.</span><span class="sxs-lookup"><span data-stu-id="3c92d-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="3c92d-108">W poniższym przykładzie `OnButton` jest program obsługi zdarzeń dla przycisków `Previous` i `Next` w aplikacji, które są przyciskami, które umożliwiają użytkownikowi nawigowanie po kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="3c92d-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="3c92d-109">Należy zauważyć, że właściwości <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> i <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> raportują, czy bieżący wskaźnik rekordu został osiągnięty na początku i na końcu listy, aby <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> i <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> można było odpowiednio wywołać.</span><span class="sxs-lookup"><span data-stu-id="3c92d-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="3c92d-110">Właściwość <xref:System.Windows.Data.CollectionView.CurrentItem%2A> widoku jest rzutowana jako `Order` do zwrócenia bieżącego elementu Order w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3c92d-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="3c92d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c92d-111">See also</span></span>

- [<span data-ttu-id="3c92d-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="3c92d-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3c92d-113">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="3c92d-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="3c92d-114">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="3c92d-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="3c92d-115">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="3c92d-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="3c92d-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3c92d-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
