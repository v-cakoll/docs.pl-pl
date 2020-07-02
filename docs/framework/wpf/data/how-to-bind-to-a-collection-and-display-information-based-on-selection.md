---
title: Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór
description: Postępuj zgodnie z tym przykładem, aby dowiedzieć się, jak utworzyć powiązanie z kolekcją i wyświetlić informacje na podstawie wyboru w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619614"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="8d9a2-103">Jak powiązać z kolekcją i informacją wyświetlaną w oparciu o wybór</span><span class="sxs-lookup"><span data-stu-id="8d9a2-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="8d9a2-104">W prostym scenariuszu wzorca szczegółowości masz powiązane dane, <xref:System.Windows.Controls.ItemsControl> takie jak <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="8d9a2-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="8d9a2-105">W oparciu o wybór użytkownika można wyświetlić więcej informacji na temat wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="8d9a2-106">Ten przykład pokazuje, jak zaimplementować ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d9a2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d9a2-107">Example</span></span>  
 <span data-ttu-id="8d9a2-108">W tym przykładzie `People` jest <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` klasą.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="8d9a2-109">Ta `Person` Klasa zawiera trzy właściwości: `FirstName` , `LastName` , i `HomeTown` , wszystkie typu `string` .</span><span class="sxs-lookup"><span data-stu-id="8d9a2-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="8d9a2-110"><xref:System.Windows.Controls.ContentControl>Program używa następujących <xref:System.Windows.DataTemplate> elementów, które definiują sposób wyświetlania informacji `Person` :</span><span class="sxs-lookup"><span data-stu-id="8d9a2-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="8d9a2-111">Poniżej znajduje się zrzut ekranu przedstawiający sposób tworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="8d9a2-112"><xref:System.Windows.Controls.ContentControl>Pokazuje inne właściwości wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="8d9a2-113">![Powiązanie z kolekcją](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="8d9a2-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="8d9a2-114">Oto dwie rzeczy do zauważenia w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8d9a2-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="8d9a2-115"><xref:System.Windows.Controls.ListBox>I <xref:System.Windows.Controls.ContentControl> powiązanie z tym samym źródłem.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="8d9a2-116"><xref:System.Windows.Data.Binding.Path%2A>Nie określono właściwości obu powiązań, ponieważ obydwie kontrolki są powiązane z całym obiektem kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="8d9a2-117">Aby to działało, należy ustawić właściwość na wartość <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="8d9a2-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="8d9a2-118">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiany jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="8d9a2-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="8d9a2-119">Alternatywnie, jeśli <xref:System.Windows.Controls.ListBox> Pobiera z niego dane <xref:System.Windows.Data.CollectionViewSource> , automatycznie synchronizuje wybór i walutę.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="8d9a2-120">Należy zauważyć, że `Person` Klasa zastępuje `ToString` metodę w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="8d9a2-121">Domyślnie <xref:System.Windows.Controls.ListBox> wywołania `ToString` i wyświetlają ciąg reprezentujący każdy obiekt w powiązanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8d9a2-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="8d9a2-122">To dlatego, że każdy `Person` pojawia się jako imię i nazwisko w <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="8d9a2-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="8d9a2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d9a2-123">See also</span></span>

- [<span data-ttu-id="8d9a2-124">Używanie wzorca szczegółów wzorca z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="8d9a2-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="8d9a2-125">Używanie wzorca szczegółów wzorca z danymi hierarchicznymi XML</span><span class="sxs-lookup"><span data-stu-id="8d9a2-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="8d9a2-126">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="8d9a2-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8d9a2-127">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="8d9a2-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="8d9a2-128">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="8d9a2-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
