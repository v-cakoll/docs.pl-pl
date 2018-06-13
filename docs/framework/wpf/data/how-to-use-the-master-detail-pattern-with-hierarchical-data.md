---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 46733b462861bdac3381cdacb8f2fbe0536d12eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556799"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="60dab-102">Jak użyć wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="60dab-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="60dab-103">W tym przykładzie pokazano, jak wdrożyć scenariusz główny szczegółowy.</span><span class="sxs-lookup"><span data-stu-id="60dab-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60dab-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="60dab-104">Example</span></span>  
 <span data-ttu-id="60dab-105">W tym przykładzie `LeagueList` jest kolekcją `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="60dab-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="60dab-106">Każdy `League` ma `Name` i Kolekcja `Divisions`i każdego `Division` ma nazwę oraz zbiór `Teams`.</span><span class="sxs-lookup"><span data-stu-id="60dab-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="60dab-107">Każdy `Team` ma nazwę zespołu.</span><span class="sxs-lookup"><span data-stu-id="60dab-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="60dab-108">Poniżej przedstawiono zrzut ekranu przykładu.</span><span class="sxs-lookup"><span data-stu-id="60dab-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="60dab-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane.</span><span class="sxs-lookup"><span data-stu-id="60dab-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="60dab-110">`Teams` <xref:System.Windows.Controls.ListBox> Śledzi opcje dla pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="60dab-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="60dab-111">![Wzorzec&#45;przykład szczegółów](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="60dab-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="60dab-112">Dostępne są następujące dwie rzeczy Zwróć uwagę, w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="60dab-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="60dab-113">Trzy <xref:System.Windows.Controls.ListBox> formanty powiązać z tego samego źródła.</span><span class="sxs-lookup"><span data-stu-id="60dab-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="60dab-114">Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić poziom danych, <xref:System.Windows.Controls.ListBox> do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="60dab-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="60dab-115">Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> formantów, które są śledzone zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="60dab-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="60dab-116">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony na <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="60dab-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="60dab-117">Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera on dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizowane wybór i waluty.</span><span class="sxs-lookup"><span data-stu-id="60dab-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="60dab-118">Technika jest nieco inne w przypadku korzystania z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.</span><span class="sxs-lookup"><span data-stu-id="60dab-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="60dab-119">Na przykład zobacz [wzorzec wzorzec-szczegół za pomocą hierarchiczne dane XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="60dab-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60dab-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60dab-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="60dab-121">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="60dab-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="60dab-122">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="60dab-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="60dab-123">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="60dab-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="60dab-124">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="60dab-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
