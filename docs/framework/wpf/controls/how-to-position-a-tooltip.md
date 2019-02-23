---
title: 'Instrukcje: Ustaw położenie ToolTip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 985c9b7737d979937837d7184f9b96f226ec73c3
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746918"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="1d8fb-102">Instrukcje: Ustaw położenie ToolTip</span><span class="sxs-lookup"><span data-stu-id="1d8fb-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="1d8fb-103">Ten przykład przedstawia sposób określania położenia etykietki narzędzia na ekranie.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d8fb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d8fb-104">Example</span></span>  
 <span data-ttu-id="1d8fb-105">Ustaw położenie tooltip korzystając z zestawu pięciu właściwości, które są zdefiniowane w obu <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="1d8fb-106">Poniższa tabela zawiera te dwa zestawy właściwości pięć oraz zawiera łącza do ich dokumentację referencyjną, zgodnie z klasy.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="1d8fb-107">Odpowiednie właściwości etykietka narzędzia, zgodnie z klasy</span><span class="sxs-lookup"><span data-stu-id="1d8fb-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="1d8fb-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="1d8fb-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="1d8fb-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="1d8fb-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="1d8fb-110">Możesz definiować zawartość etykietka narzędzia za pomocą <xref:System.Windows.Controls.ToolTip> obiektu, można użyć właściwości każdej klasy; jednak <xref:System.Windows.Controls.ToolTipService> właściwości mają pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="1d8fb-111">Użyj <xref:System.Windows.Controls.ToolTipService> właściwości dla etykietki narzędzi, które nie są zdefiniowane jako <xref:System.Windows.Controls.ToolTip> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="1d8fb-112">Na poniższych ilustracjach przedstawiono sposób położenie tooltip przy użyciu tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="1d8fb-113">Mimo że, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] te ilustracje przykładach w sposób ustawiania właściwości, które są definiowane przez <xref:System.Windows.Controls.ToolTip> klasy odpowiednie właściwości <xref:System.Windows.Controls.ToolTipService> klasy są zgodne z regułami układu.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="1d8fb-114">Aby uzyskać więcej informacji na temat możliwych wartości dla właściwości umieszczania, zobacz [zachowanie położenia okna podręcznego](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="1d8fb-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="1d8fb-115">![Położenie ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="1d8fb-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="1d8fb-116">Położenia etykietki narzędzia, za pomocą właściwości umieszczania</span><span class="sxs-lookup"><span data-stu-id="1d8fb-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="1d8fb-117">![Umieszczenie etykietka narzędzia, za pomocą prostokąta umieszczania](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="1d8fb-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="1d8fb-118">Położenia etykietki narzędzia, za pomocą właściwości umieszczania i PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="1d8fb-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="1d8fb-119">![Diagram położenie ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="1d8fb-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="1d8fb-120">Położenie ToolTip przy użyciu właściwości Placement, PlacementRectangle i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="1d8fb-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="1d8fb-121">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTip> właściwości, aby określić położenie tooltip, którego zawartość ma <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="1d8fb-122">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTipService> właściwości, aby określić położenie tooltip, którego zawartość nie jest <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d8fb-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="1d8fb-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d8fb-123">See also</span></span>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="1d8fb-124">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1d8fb-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
- [<span data-ttu-id="1d8fb-125">ToolTip — omówienie</span><span class="sxs-lookup"><span data-stu-id="1d8fb-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
