---
title: "Jak ustawić położenie ToolTip"
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
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62e86f2adfbe8f8aac000d653e955555c7def750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="d5721-102">Jak ustawić położenie ToolTip</span><span class="sxs-lookup"><span data-stu-id="d5721-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="d5721-103">W tym przykładzie przedstawiono sposób określić położenie etykietka narzędzia na ekranie.</span><span class="sxs-lookup"><span data-stu-id="d5721-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5721-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5721-104">Example</span></span>  
 <span data-ttu-id="d5721-105">Etykietka narzędzia można umieścić przy użyciu zestawu pięciu właściwości, które są zdefiniowane w obu <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5721-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="d5721-106">Poniższa tabela przedstawia te dwa zestawy pięciu właściwości oraz zawiera łącza do ich dokumentacji zgodnie z klasy.</span><span class="sxs-lookup"><span data-stu-id="d5721-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="d5721-107">Odpowiednie właściwości etykietka narzędzia, zgodnie z klasy</span><span class="sxs-lookup"><span data-stu-id="d5721-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="d5721-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>Właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="d5721-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="d5721-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>Właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="d5721-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="d5721-110">Można zdefiniować zawartość etykietka narzędzia przy użyciu <xref:System.Windows.Controls.ToolTip> obiektu, można użyć właściwości każdej klasy, ale <xref:System.Windows.Controls.ToolTipService> właściwości mają pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="d5721-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="d5721-111">Użyj <xref:System.Windows.Controls.ToolTipService> właściwości etykietki narzędzi, które nie są zdefiniowane jako <xref:System.Windows.Controls.ToolTip> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d5721-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="d5721-112">Na poniższych ilustracjach przedstawiono położenie etykietka narzędzia, za pomocą tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5721-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="d5721-113">Mimo że, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady w tym ilustracjom przedstawiają sposób ustawiania właściwości, które są definiowane przez <xref:System.Windows.Controls.ToolTip> klasy odpowiednich właściwościach <xref:System.Windows.Controls.ToolTipService> klasy są zgodne z regułami układu.</span><span class="sxs-lookup"><span data-stu-id="d5721-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="d5721-114">Aby uzyskać więcej informacji na temat możliwych wartości dla właściwości umieszczania, zobacz [zachowanie przy umieszczaniu podręcznego](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="d5721-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="d5721-115">![Etykietka narzędzia umieszczania](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="d5721-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="d5721-116">Etykietka narzędzia umieszczania przy użyciu właściwości umieszczania</span><span class="sxs-lookup"><span data-stu-id="d5721-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="d5721-117">![Umieszczanie obiektu ToolTip przy użyciu prostokąta umieszczania](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="d5721-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="d5721-118">Etykietka narzędzia umieszczania przy użyciu właściwości umieszczania i PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="d5721-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="d5721-119">![Etykietka narzędzia umieszczania diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="d5721-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="d5721-120">Etykietka narzędzia umieszczania przy użyciu właściwości Placement, PlacementRectangle i przesunięcie</span><span class="sxs-lookup"><span data-stu-id="d5721-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="d5721-121">Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.ToolTip> właściwości, aby określić położenie etykietka narzędzia, których zawartość znajduje się <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5721-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="d5721-122">Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.ToolTipService> właściwości, aby określić położenie etykietka narzędzia, którego zawartość nie jest <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5721-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="d5721-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5721-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="d5721-124">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="d5721-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="d5721-125">ToolTip — omówienie</span><span class="sxs-lookup"><span data-stu-id="d5721-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="d5721-126">Użyj ContextMenuService i ToolTipService</span><span class="sxs-lookup"><span data-stu-id="d5721-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
