---
title: "Jak użyć wzorca szczegółowego z danymi hierarchicznymi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="3496e-102">Jak użyć wzorca szczegółowego z danymi hierarchicznymi</span><span class="sxs-lookup"><span data-stu-id="3496e-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="3496e-103">W tym przykładzie pokazano, jak wdrożyć scenariusz główny szczegółowy.</span><span class="sxs-lookup"><span data-stu-id="3496e-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3496e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3496e-104">Example</span></span>  
 <span data-ttu-id="3496e-105">W tym przykładzie `LeagueList` jest kolekcją `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="3496e-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="3496e-106">Każdy `League` ma `Name` i Kolekcja `Divisions`i każdego `Division` ma nazwę oraz zbiór `Teams`.</span><span class="sxs-lookup"><span data-stu-id="3496e-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="3496e-107">Każdy `Team` ma nazwę zespołu.</span><span class="sxs-lookup"><span data-stu-id="3496e-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="3496e-108">Poniżej przedstawiono zrzut ekranu przykładu.</span><span class="sxs-lookup"><span data-stu-id="3496e-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="3496e-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automatyczne śledzenie zaznaczenia w `Leagues` <xref:System.Windows.Controls.ListBox> i wyświetlić odpowiednie dane.</span><span class="sxs-lookup"><span data-stu-id="3496e-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="3496e-110">`Teams` <xref:System.Windows.Controls.ListBox> Śledzi opcje dla pozostałych <xref:System.Windows.Controls.ListBox> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3496e-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="3496e-111">![&#45;wzorca; przykład szczegółów](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="3496e-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="3496e-112">Dostępne są następujące dwie rzeczy Zwróć uwagę, w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3496e-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="3496e-113">Trzy <xref:System.Windows.Controls.ListBox> formanty powiązać z tego samego źródła.</span><span class="sxs-lookup"><span data-stu-id="3496e-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="3496e-114">Możesz ustawić <xref:System.Windows.Data.Binding.Path%2A> właściwości powiązania, aby określić poziom danych, <xref:System.Windows.Controls.ListBox> do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="3496e-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="3496e-115">Należy ustawić <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> właściwości `true` na <xref:System.Windows.Controls.ListBox> formantów, które są śledzone zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="3496e-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="3496e-116">Ustawienie tej właściwości gwarantuje, że wybrany element jest zawsze ustawiony na <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="3496e-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="3496e-117">Alternatywnie Jeśli <xref:System.Windows.Controls.ListBox> pobiera on dane z <xref:System.Windows.Data.CollectionViewSource>, automatycznie synchronizowane wybór i waluty.</span><span class="sxs-lookup"><span data-stu-id="3496e-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="3496e-118">Technika jest nieco inne w przypadku korzystania z [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danych.</span><span class="sxs-lookup"><span data-stu-id="3496e-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="3496e-119">Na przykład zobacz [wzorzec wzorzec-szczegół za pomocą hierarchiczne dane XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="3496e-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3496e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3496e-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="3496e-121">Powiązania w kolekcji i wyświetlania informacji na podstawie zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="3496e-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="3496e-122">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="3496e-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="3496e-123">Omówienie tworzenia szablonów danych</span><span class="sxs-lookup"><span data-stu-id="3496e-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="3496e-124">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="3496e-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
