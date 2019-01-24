---
title: 'Instrukcje: Użyj wzorca szczegółowego z danymi hierarchicznymi'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 36eded28085aec3aaea1a2351ae3babc6ad6c700
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689643"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="1cfa9-102">Instrukcje: Użyj wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="1cfa9-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="1cfa9-103">W tym przykładzie pokazano, jak można implementować scenariusza wzorzec / szczegół.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cfa9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1cfa9-104">Example</span></span>  
 <span data-ttu-id="1cfa9-105">W tym przykładzie `LeagueList` to zbiór `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="1cfa9-106">Każdy `League` ma `Name` i kolekcji `Divisions`i każdy `Division` ma nazwę oraz zbiór `Teams`.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="1cfa9-107">Każdy `Team` ma nazwę zespołu.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="1cfa9-108">Poniżej przedstawiono zrzut ekranu przykładu.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="1cfa9-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="1cfa9-110">`Teams` <xref:System.Windows.Controls.ListBox> Śledzi wybory w dwóch pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="1cfa9-111">![Wzorzec&#45;przykład szczegółów](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="1cfa9-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="1cfa9-112">Dostępne są następujące dwie czynności należy zwrócić uwagę, w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1cfa9-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="1cfa9-113">Trzy <xref:System.Windows.Controls.ListBox> kontrolki powiązania z tym samym źródłem.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="1cfa9-114">Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić, której poziom danych <xref:System.Windows.Controls.ListBox> do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="1cfa9-115">Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> kontrolek, których wybór są śledzone.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="1cfa9-116">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="1cfa9-117">Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera ona dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i aktualność.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="1cfa9-118">Technika jest nieco inne w przypadku, gdy używasz [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.</span><span class="sxs-lookup"><span data-stu-id="1cfa9-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="1cfa9-119">Aby uzyskać przykład, zobacz [Użyj wzorca szczegółowego z danymi hierarchicznymi XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="1cfa9-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cfa9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cfa9-120">See also</span></span>
- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="1cfa9-121">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="1cfa9-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="1cfa9-122">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="1cfa9-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1cfa9-123">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="1cfa9-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="1cfa9-124">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1cfa9-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
