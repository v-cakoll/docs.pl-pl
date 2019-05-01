---
title: 'Instrukcje: Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: bb7d4c89e63982a3052857dcb50d04d36d9517dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967946"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="07dd3-102">Instrukcje: Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="07dd3-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="07dd3-103">W prostym scenariuszu wzorzec / szczegół mają powiązane z danymi <xref:System.Windows.Controls.ItemsControl> takich jak <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="07dd3-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="07dd3-104">Na podstawie wyboru użytkownik możesz wyświetlić więcej informacji na temat wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="07dd3-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="07dd3-105">W tym przykładzie pokazano, jak wdrożyć ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="07dd3-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07dd3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="07dd3-106">Example</span></span>  
 <span data-ttu-id="07dd3-107">W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` klasy.</span><span class="sxs-lookup"><span data-stu-id="07dd3-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="07dd3-108">To `Person` klasa zawiera trzy właściwości: `FirstName`, `LastName`, i `HomeTown`, typ `string`.</span><span class="sxs-lookup"><span data-stu-id="07dd3-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="07dd3-109"><xref:System.Windows.Controls.ContentControl> Korzysta z następujących <xref:System.Windows.DataTemplate> definiuje sposób informacje o `Person` zobaczy:</span><span class="sxs-lookup"><span data-stu-id="07dd3-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="07dd3-110">Poniżej przedstawiono zrzut ekranu przedstawiający przykład generuje.</span><span class="sxs-lookup"><span data-stu-id="07dd3-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="07dd3-111"><xref:System.Windows.Controls.ContentControl> Pokazuje właściwości osoby wybrane.</span><span class="sxs-lookup"><span data-stu-id="07dd3-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="07dd3-112">![Tworzenie powiązania z kolekcją](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="07dd3-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="07dd3-113">Dostępne są następujące dwie czynności należy zwrócić uwagę, w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="07dd3-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="07dd3-114"><xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> powiązania z tym samym źródłem.</span><span class="sxs-lookup"><span data-stu-id="07dd3-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="07dd3-115"><xref:System.Windows.Data.Binding.Path%2A> Właściwości zarówno powiązania nie są określone, ponieważ obie kontrolki dokonywane jest wiązanie obiektu całą kolekcję.</span><span class="sxs-lookup"><span data-stu-id="07dd3-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="07dd3-116">Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwość `true` Aby to działało.</span><span class="sxs-lookup"><span data-stu-id="07dd3-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="07dd3-117">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="07dd3-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="07dd3-118">Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera ona dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i aktualność.</span><span class="sxs-lookup"><span data-stu-id="07dd3-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="07dd3-119">Należy pamiętać, że `Person` klasy zastąpienia `ToString` metody w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="07dd3-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="07dd3-120">Domyślnie <xref:System.Windows.Controls.ListBox> wywołania `ToString` i wyświetla reprezentację ciągu każdego obiektu w powiązanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="07dd3-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="07dd3-121">Dlatego każdego `Person` pojawia się jako nazwę pierwszego <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="07dd3-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="07dd3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07dd3-122">See also</span></span>

- [<span data-ttu-id="07dd3-123">Używanie wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="07dd3-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="07dd3-124">Używanie wzorca szczegółowego z danymi hierarchicznymi XML</span><span class="sxs-lookup"><span data-stu-id="07dd3-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="07dd3-125">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="07dd3-125">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="07dd3-126">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="07dd3-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="07dd3-127">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="07dd3-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
