---
title: 'Instrukcje: Przejdź do obiektów w danych CollectionView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 9272a2f635a62abdac2746f2c8cce515812706f6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355782"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="8ee7d-102">Instrukcje: Przejdź do obiektów w danych CollectionView</span><span class="sxs-lookup"><span data-stu-id="8ee7d-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="8ee7d-103">Widoki zezwala na tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od tego, czy sortowanie, filtrowanie i grupowanie.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="8ee7d-104">Widoki również zapewnić bieżącej koncepcję rekordów wskaźnika i włączyć, przesuwając wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="8ee7d-105">W tym przykładzie pokazano, jak uzyskać bieżący obiekt, a także przechodzenie do obiektów w zbieraniu danych, korzystając z funkcji podawany <xref:System.Windows.Data.CollectionView> klasy.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee7d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ee7d-106">Example</span></span>  
 <span data-ttu-id="8ee7d-107">W tym przykładzie `myCollectionView` jest <xref:System.Windows.Data.CollectionView> obiekt, który znajduje się za pośrednictwem powiązanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="8ee7d-108">W poniższym przykładzie `OnButton` jest program obsługi zdarzeń dla `Previous` i `Next` przycisków w aplikacji, które są przyciski, który umożliwia użytkownikowi Przejdź zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="8ee7d-109">Należy pamiętać, że <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> i <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> właściwości raportu, czy bieżący wskaźnik rekordów doszła do początku i końca listy odpowiednio tak, <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> i <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> mogą być wywoływane jako odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="8ee7d-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A> Właściwości widoku jest rzutowany jako `Order` do zwrócenia z aktualnym elementem zamówienia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8ee7d-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="8ee7d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ee7d-111">See also</span></span>
- [<span data-ttu-id="8ee7d-112">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="8ee7d-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="8ee7d-113">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="8ee7d-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="8ee7d-114">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="8ee7d-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="8ee7d-115">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="8ee7d-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="8ee7d-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8ee7d-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
