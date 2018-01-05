---
title: "Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór"
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
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a751025470b566ef1e735e4ddd192cfd8fc354ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="52995-102">Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór</span><span class="sxs-lookup"><span data-stu-id="52995-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="52995-103">W prosty scenariusz główny szczegółowy, masz z danymi <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="52995-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="52995-104">Oparte na wybór użytkownika, możesz wyświetlić więcej informacji na temat wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="52995-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="52995-105">W tym przykładzie pokazano, jak wdrożyć ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="52995-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52995-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="52995-106">Example</span></span>  
 <span data-ttu-id="52995-107">W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` klasy.</span><span class="sxs-lookup"><span data-stu-id="52995-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="52995-108">To `Person` klasa zawiera trzy właściwości: `FirstName`, `LastName`, i `HomeTown`, wszystkie typu `string`.</span><span class="sxs-lookup"><span data-stu-id="52995-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="52995-109"><xref:System.Windows.Controls.ContentControl> Są używane następujące <xref:System.Windows.DataTemplate> definiuje sposób informacje `Person` przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="52995-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="52995-110">Poniżej przedstawiono przykład tworzy zrzut ekranu.</span><span class="sxs-lookup"><span data-stu-id="52995-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="52995-111"><xref:System.Windows.Controls.ContentControl> Zawiera inne właściwości osoby wybrane.</span><span class="sxs-lookup"><span data-stu-id="52995-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="52995-112">![Tworzenie powiązania z kolekcją](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="52995-112">![Binding to a collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="52995-113">Dostępne są następujące dwie rzeczy Zwróć uwagę, w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="52995-113">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="52995-114"><xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> powiązać z tego samego źródła.</span><span class="sxs-lookup"><span data-stu-id="52995-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="52995-115"><xref:System.Windows.Data.Binding.Path%2A> Nie podano właściwości zarówno powiązania, ponieważ oba formanty są powiązanie z obiektem całą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="52995-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2.  <span data-ttu-id="52995-116">Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` Aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="52995-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="52995-117">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony na <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="52995-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="52995-118">Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera on dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizowane wybór i waluty.</span><span class="sxs-lookup"><span data-stu-id="52995-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="52995-119">Należy pamiętać, że `Person` klasy zastąpienia `ToString` — metoda w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="52995-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="52995-120">Domyślnie <xref:System.Windows.Controls.ListBox> wywołania `ToString` i wyświetla reprezentację ciągu każdego obiektu w powiązanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="52995-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="52995-121">Dlatego każdy `Person` pojawia się jako pierwszej nazwy w <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="52995-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="52995-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52995-122">See Also</span></span>  
 [<span data-ttu-id="52995-123">Używanie wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="52995-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [<span data-ttu-id="52995-124">Używanie wzorca szczegółowego z danymi hierarchicznymi XML</span><span class="sxs-lookup"><span data-stu-id="52995-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [<span data-ttu-id="52995-125">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="52995-125">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="52995-126">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="52995-126">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="52995-127">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="52995-127">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
