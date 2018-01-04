---
title: "Jak pobrać domyślny widok kolekcji danych"
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
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebb74e1db2e63269f70a13ef8520ab1383ecae08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="f8d54-102">Jak pobrać domyślny widok kolekcji danych</span><span class="sxs-lookup"><span data-stu-id="f8d54-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="f8d54-103">Widoki zezwolić tej samej kolekcji danych do wyświetlenia na różne sposoby, w zależności od sortowania, filtrowania lub kryteria grupowania.</span><span class="sxs-lookup"><span data-stu-id="f8d54-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="f8d54-104">Każdy kolekcja zawiera jeden widok domyślny udostępnionego, który jest używany jako źródło rzeczywistego powiązania, gdy powiązanie Określa kolekcję jako źródło.</span><span class="sxs-lookup"><span data-stu-id="f8d54-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="f8d54-105">W tym przykładzie przedstawiono sposób wyświetlania domyślnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f8d54-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8d54-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8d54-106">Example</span></span>  
 <span data-ttu-id="f8d54-107">Aby utworzyć widok, należy odwołanie do obiektu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f8d54-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="f8d54-108">Ten obiekt danych można uzyskać za pomocą odwołań do własnego obiektu związane z kodem, pobierając kontekstu danych przez pobieranie właściwości źródła danych lub pobieranie właściwości powiązania.</span><span class="sxs-lookup"><span data-stu-id="f8d54-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="f8d54-109">W tym przykładzie pokazano, jak pobrać <xref:System.Windows.FrameworkElement.DataContext%2A> obiekt danych i użyj go bezpośrednio uzyskać domyślnej kolekcji wyświetlania dla tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f8d54-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="f8d54-110">W tym przykładzie jest elementem głównym <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="f8d54-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="f8d54-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Ustawiono *myDataSource*, które odwołuje się do dostawcy danych, który jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z *kolejności* obiektów.</span><span class="sxs-lookup"><span data-stu-id="f8d54-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="f8d54-112">Alternatywnie można utworzyć wystąpienia i powiąż własnych kolekcji widoku przy użyciu <xref:System.Windows.Data.CollectionViewSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="f8d54-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="f8d54-113">Ten widok kolekcji jest udostępniany tylko przez formanty, które wiążą się do niego bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f8d54-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="f8d54-114">Na przykład zobacz sposób tworzenia widoku w sekcji [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f8d54-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="f8d54-115">Aby uzyskać przykłady pokazujące funkcje udostępniane przez widok kolekcji, zobacz [sortowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), i [przejdź do obiektów w danych widoku CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="f8d54-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d54-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8d54-116">See Also</span></span>  
 [<span data-ttu-id="f8d54-117">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="f8d54-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="f8d54-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f8d54-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
