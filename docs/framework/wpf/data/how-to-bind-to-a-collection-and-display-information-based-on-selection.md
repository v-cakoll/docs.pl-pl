---
title: Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459142"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="b8937-102">Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór</span><span class="sxs-lookup"><span data-stu-id="b8937-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="b8937-103">W prostym scenariuszu wzorca szczegółowości masz <xref:System.Windows.Controls.ItemsControl> powiązane z danymi, takie jak <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="b8937-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="b8937-104">W oparciu o wybór użytkownika można wyświetlić więcej informacji na temat wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="b8937-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="b8937-105">Ten przykład pokazuje, jak zaimplementować ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="b8937-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8937-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8937-106">Example</span></span>  
 <span data-ttu-id="b8937-107">W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> klas `Person`.</span><span class="sxs-lookup"><span data-stu-id="b8937-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="b8937-108">Ta klasa `Person` zawiera trzy właściwości: `FirstName`, `LastName`i `HomeTown`wszystkie typy `string`.</span><span class="sxs-lookup"><span data-stu-id="b8937-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="b8937-109"><xref:System.Windows.Controls.ContentControl> używa następujących <xref:System.Windows.DataTemplate>, które definiują sposób przedstawiania informacji `Person`:</span><span class="sxs-lookup"><span data-stu-id="b8937-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="b8937-110">Poniżej znajduje się zrzut ekranu przedstawiający sposób tworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="b8937-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="b8937-111">W <xref:System.Windows.Controls.ContentControl> są wyświetlane inne właściwości wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="b8937-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="b8937-112">![Powiązanie z kolekcją](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="b8937-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="b8937-113">Oto dwie rzeczy do zauważenia w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b8937-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="b8937-114"><xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ContentControl> powiązać z tym samym źródłem.</span><span class="sxs-lookup"><span data-stu-id="b8937-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="b8937-115">Nie określono właściwości <xref:System.Windows.Data.Binding.Path%2A> obu powiązań, ponieważ obydwie kontrolki są powiązane z całym obiektem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b8937-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="b8937-116">Aby ta wartość działała, należy ustawić `true` Właściwość <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8937-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="b8937-117">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiany jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8937-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="b8937-118">Alternatywnie, jeśli <xref:System.Windows.Controls.ListBox> pobiera dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i walutę.</span><span class="sxs-lookup"><span data-stu-id="b8937-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="b8937-119">Należy zauważyć, że Klasa `Person` przesłania metodę `ToString` w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b8937-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="b8937-120">Domyślnie <xref:System.Windows.Controls.ListBox> wywołuje `ToString` i wyświetla reprezentację ciągu dla każdego obiektu w powiązanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b8937-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="b8937-121">To dlatego, że każdy `Person` pojawia się jako imię w <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="b8937-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="b8937-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8937-122">See also</span></span>

- [<span data-ttu-id="b8937-123">Używanie wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="b8937-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="b8937-124">Używanie wzorca szczegółowego z danymi hierarchicznymi XML</span><span class="sxs-lookup"><span data-stu-id="b8937-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="b8937-125">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="b8937-125">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="b8937-126">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="b8937-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="b8937-127">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="b8937-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
