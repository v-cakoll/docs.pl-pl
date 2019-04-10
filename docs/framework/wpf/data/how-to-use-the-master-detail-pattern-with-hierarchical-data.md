---
title: 'Instrukcje: Używanie wzorca szczegółowego z danymi hierarchicznymi'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e0bbb24b07fdc1c362e2be43d69d189defbc27a4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346187"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="c38ff-102">Instrukcje: Używanie wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="c38ff-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="c38ff-103">W tym przykładzie pokazano, jak można implementować scenariusza wzorzec / szczegół.</span><span class="sxs-lookup"><span data-stu-id="c38ff-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c38ff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c38ff-104">Example</span></span>  
 <span data-ttu-id="c38ff-105">W tym przykładzie `LeagueList` to zbiór `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="c38ff-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="c38ff-106">Każdy `League` ma `Name` i kolekcji `Divisions`i każdy `Division` ma nazwę oraz zbiór `Teams`.</span><span class="sxs-lookup"><span data-stu-id="c38ff-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="c38ff-107">Każdy `Team` ma nazwę zespołu.</span><span class="sxs-lookup"><span data-stu-id="c38ff-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="c38ff-108">Poniżej przedstawiono zrzut ekranu przykładu.</span><span class="sxs-lookup"><span data-stu-id="c38ff-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="c38ff-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane.</span><span class="sxs-lookup"><span data-stu-id="c38ff-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="c38ff-110">`Teams` <xref:System.Windows.Controls.ListBox> Śledzi wybory w dwóch pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c38ff-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Zrzut ekranu przedstawiający wzorzec&#45;przykładowy scenariusz szczegółów.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="c38ff-112">Dostępne są następujące dwie czynności należy zwrócić uwagę, w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c38ff-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="c38ff-113">Trzy <xref:System.Windows.Controls.ListBox> kontrolki powiązania z tym samym źródłem.</span><span class="sxs-lookup"><span data-stu-id="c38ff-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="c38ff-114">Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić, której poziom danych <xref:System.Windows.Controls.ListBox> do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="c38ff-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="c38ff-115">Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> kontrolek, których wybór są śledzone.</span><span class="sxs-lookup"><span data-stu-id="c38ff-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="c38ff-116">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="c38ff-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="c38ff-117">Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera ona dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i aktualność.</span><span class="sxs-lookup"><span data-stu-id="c38ff-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="c38ff-118">Technika jest nieco inne w przypadku, gdy używasz [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.</span><span class="sxs-lookup"><span data-stu-id="c38ff-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="c38ff-119">Aby uzyskać przykład, zobacz [Użyj wzorca szczegółowego z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="c38ff-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38ff-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c38ff-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="c38ff-121">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="c38ff-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="c38ff-122">Przegląd Wiązanie danych</span><span class="sxs-lookup"><span data-stu-id="c38ff-122">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="c38ff-123">Przegląd Szablonowanie danych</span><span class="sxs-lookup"><span data-stu-id="c38ff-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="c38ff-124">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="c38ff-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
