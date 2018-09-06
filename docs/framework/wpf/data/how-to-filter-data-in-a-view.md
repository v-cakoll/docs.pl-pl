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
ms.openlocfilehash: b972da093fc50563c5db93e61aeb8421f9bf20b2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785859"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="297b4-102">Jak filtrować dane w widoku</span><span class="sxs-lookup"><span data-stu-id="297b4-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="297b4-103">Ten przykład przedstawia sposób filtrowania danych w widoku.</span><span class="sxs-lookup"><span data-stu-id="297b4-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="297b4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="297b4-104">Example</span></span>  
 <span data-ttu-id="297b4-105">Aby utworzyć filtr, należy zdefiniować metodę, która udostępnia logikę filtrowania.</span><span class="sxs-lookup"><span data-stu-id="297b4-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="297b4-106">Metoda jest używana jako wywołanie zwrotne i akceptuje parametr typu `object`.</span><span class="sxs-lookup"><span data-stu-id="297b4-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="297b4-107">Poniższa metoda zwraca wszystkie `Order` obiekty z `filled` właściwość ustawioną na "No" filtrowanie pozostałymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="297b4-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="297b4-108">Można użyć filtru, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="297b4-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="297b4-109">W tym przykładzie `myCollectionView` jest <xref:System.Windows.Data.ListCollectionView> obiektu.</span><span class="sxs-lookup"><span data-stu-id="297b4-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="297b4-110">Aby cofnąć filtrowanie, możesz ustawić <xref:System.Windows.Data.CollectionView.Filter%2A> właściwości `null`:</span><span class="sxs-lookup"><span data-stu-id="297b4-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="297b4-111">Aby uzyskać informacje o tym, jak utworzyć lub uzyskać widok, zobacz [widok domyślny zbiór danych](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="297b4-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="297b4-112">Aby uzyskać kompletny przykład, zobacz [sortowanie i filtrowanie elementów w przykładzie widok](https://go.microsoft.com/fwlink/?LinkID=160040).</span><span class="sxs-lookup"><span data-stu-id="297b4-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="297b4-113">Jeśli obiekt widoku pochodzi z <xref:System.Windows.Data.CollectionViewSource> obiekt i zastosować logikę filtrowania przez ustawienie programu obsługi zdarzeń dla <xref:System.Windows.Data.CollectionViewSource.Filter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="297b4-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="297b4-114">W poniższym przykładzie `listingDataView` jest wystąpieniem <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="297b4-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="297b4-115">Poniżej pokazano implementacja przykładu `ShowOnlyBargainsFilter` procedury obsługi zdarzeń filtra.</span><span class="sxs-lookup"><span data-stu-id="297b4-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="297b4-116">Ta procedura obsługi zdarzeń używa <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> właściwości, aby odfiltrować `AuctionItem` obiektów, które mają `CurrentPrice` 25 USD lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="297b4-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="297b4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="297b4-117">See Also</span></span>  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [<span data-ttu-id="297b4-118">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="297b4-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="297b4-119">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="297b4-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="297b4-120">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="297b4-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
