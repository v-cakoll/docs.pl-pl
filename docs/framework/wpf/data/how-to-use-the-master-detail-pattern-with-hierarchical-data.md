---
title: Jak użyć wzorca szczegółowego z danymi hierarchicznymi
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459082"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="6dbc8-102">Jak użyć wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="6dbc8-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="6dbc8-103">Ten przykład pokazuje, jak zaimplementować scenariusz wzorzec-szczegóły.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dbc8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6dbc8-104">Example</span></span>  
 <span data-ttu-id="6dbc8-105">W tym przykładzie `LeagueList` jest kolekcją `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="6dbc8-106">Każda `League` ma `Name` i zbiór `Divisions`, a każda `Division` ma nazwę i kolekcję `Teams`.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="6dbc8-107">Każda `Team` ma nazwę zespołu.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="6dbc8-108">Poniżej znajduje się zrzut ekranu przedstawiający przykład.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="6dbc8-109">`Divisions` <xref:System.Windows.Controls.ListBox> automatycznie śledzi wybory w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetla odpowiednie dane.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="6dbc8-110">`Teams` <xref:System.Windows.Controls.ListBox> śledzi zaznaczenia w innych dwóch kontrolkach <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Zrzut ekranu, który pokazuje&#45;przykład scenariusza z szczegółami głównymi.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="6dbc8-112">Oto dwie rzeczy do zauważenia w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6dbc8-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="6dbc8-113">Trzy formanty <xref:System.Windows.Controls.ListBox> są powiązane z tym samym źródłem.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="6dbc8-114">Właściwość <xref:System.Windows.Data.Binding.Path%2A> powiązania ustawia się w celu określenia poziomu danych, który ma być wyświetlany przez <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="6dbc8-115">Należy ustawić właściwość <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> na `true` w kontrolkach <xref:System.Windows.Controls.ListBox>, dla których jest śledzone zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="6dbc8-116">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiany jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="6dbc8-117">Alternatywnie, jeśli <xref:System.Windows.Controls.ListBox> pobiera dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizuje wybór i walutę.</span><span class="sxs-lookup"><span data-stu-id="6dbc8-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="6dbc8-118">Technika jest nieco inna, gdy używasz danych [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6dbc8-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="6dbc8-119">Aby zapoznać się z przykładem, zobacz [Używanie wzorca master-detail z danymi hierarchicznymi XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="6dbc8-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbc8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dbc8-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="6dbc8-121">Powiązywanie z kolekcją i wyświetlanie informacji na podstawie wyboru</span><span class="sxs-lookup"><span data-stu-id="6dbc8-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="6dbc8-122">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="6dbc8-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6dbc8-123">Szablonowanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="6dbc8-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="6dbc8-124">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6dbc8-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
