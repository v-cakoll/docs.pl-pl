---
title: "Jak przejść do obiektów w danych CollectionView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f20881ed452f1ec78381d17a32b4cc2c77305e0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="43d17-102">Jak przejść do obiektów w danych CollectionView</span><span class="sxs-lookup"><span data-stu-id="43d17-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="43d17-103">Widoki zezwolić tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od sortowania, filtrowania lub grupowania.</span><span class="sxs-lookup"><span data-stu-id="43d17-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="43d17-104">Widoki również podać pojęcie bieżącego rekordu wskaźnik i włączyć, przesuń wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="43d17-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="43d17-105">W tym przykładzie pokazano, jak pobrać bieżący obiekt, a także przejdź do obiektów w kolekcji danych, korzystając z funkcji dostępnych w <xref:System.Windows.Data.CollectionView> klasy.</span><span class="sxs-lookup"><span data-stu-id="43d17-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43d17-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="43d17-106">Example</span></span>  
 <span data-ttu-id="43d17-107">W tym przykładzie `myCollectionView` jest <xref:System.Windows.Data.CollectionView> obiekt, który jest widokiem za pośrednictwem powiązanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="43d17-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="43d17-108">W poniższym przykładzie `OnButton` jest program obsługi zdarzeń dla `Previous` i `Next` przycisków w aplikacji, które są przyciski, który umożliwia użytkownikowi nawigację zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="43d17-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="43d17-109">Należy pamiętać, że <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> i <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> właściwości raportu, czy bieżący wskaźnik rekordów do trybu na początku i na końcu listy odpowiednio tak że <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> i <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> można wywołać jako odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="43d17-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="43d17-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A> Właściwości widoku jest rzutowany jako `Order` aby powrócić do bieżącego elementu kolejności w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="43d17-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="43d17-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43d17-111">See Also</span></span>  
 [<span data-ttu-id="43d17-112">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="43d17-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="43d17-113">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="43d17-113">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="43d17-114">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="43d17-114">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="43d17-115">Sortowanie i grupowanie danych przy użyciu widoku w języku XAML</span><span class="sxs-lookup"><span data-stu-id="43d17-115">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="43d17-116">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="43d17-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
