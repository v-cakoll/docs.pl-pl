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
ms.openlocfilehash: d20eea0890708eb2ec2ada503f5c871d54ccc035
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364540"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="c790d-102">Instrukcje: Ustaw położenie ToolTip</span><span class="sxs-lookup"><span data-stu-id="c790d-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="c790d-103">Ten przykład przedstawia sposób określania położenia etykietki narzędzia na ekranie.</span><span class="sxs-lookup"><span data-stu-id="c790d-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c790d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c790d-104">Example</span></span>  
 <span data-ttu-id="c790d-105">Ustaw położenie tooltip korzystając z zestawu pięciu właściwości, które są zdefiniowane w obu <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> klasy.</span><span class="sxs-lookup"><span data-stu-id="c790d-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="c790d-106">Poniższa tabela zawiera te dwa zestawy właściwości pięć oraz zawiera łącza do ich dokumentację referencyjną, zgodnie z klasy.</span><span class="sxs-lookup"><span data-stu-id="c790d-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="c790d-107">Odpowiednie właściwości etykietka narzędzia, zgodnie z klasy</span><span class="sxs-lookup"><span data-stu-id="c790d-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="c790d-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="c790d-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="c790d-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="c790d-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="c790d-110">Możesz definiować zawartość etykietka narzędzia za pomocą <xref:System.Windows.Controls.ToolTip> obiektu, można użyć właściwości każdej klasy; jednak <xref:System.Windows.Controls.ToolTipService> właściwości mają pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="c790d-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="c790d-111">Użyj <xref:System.Windows.Controls.ToolTipService> właściwości dla etykietki narzędzi, które nie są zdefiniowane jako <xref:System.Windows.Controls.ToolTip> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c790d-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="c790d-112">Na poniższych ilustracjach przedstawiono sposób położenie tooltip przy użyciu tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="c790d-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="c790d-113">Mimo że, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] te ilustracje przykładach w sposób ustawiania właściwości, które są definiowane przez <xref:System.Windows.Controls.ToolTip> klasy odpowiednie właściwości <xref:System.Windows.Controls.ToolTipService> klasy są zgodne z regułami układu.</span><span class="sxs-lookup"><span data-stu-id="c790d-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="c790d-114">Aby uzyskać więcej informacji na temat możliwych wartości dla właściwości umieszczania, zobacz [zachowanie położenia okna podręcznego](popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="c790d-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="c790d-115">![Położenie ToolTip](./media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="c790d-115">![ToolTip placement](./media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="c790d-116">Położenia etykietki narzędzia, za pomocą właściwości umieszczania</span><span class="sxs-lookup"><span data-stu-id="c790d-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="c790d-117">![Umieszczenie etykietka narzędzia, za pomocą prostokąta umieszczania](./media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="c790d-117">![Placing a ToolTip by using a placement rectangle](./media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="c790d-118">Położenia etykietki narzędzia, za pomocą właściwości umieszczania i PlacementRectangle</span><span class="sxs-lookup"><span data-stu-id="c790d-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="c790d-119">![Diagram położenie ToolTip](./media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="c790d-119">![ToolTip placement diagram](./media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="c790d-120">Położenie ToolTip przy użyciu właściwości Placement, PlacementRectangle i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="c790d-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="c790d-121">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTip> właściwości, aby określić położenie tooltip, którego zawartość ma <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c790d-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="c790d-122">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.ToolTipService> właściwości, aby określić położenie tooltip, którego zawartość nie jest <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c790d-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="c790d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c790d-123">See also</span></span>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="c790d-124">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c790d-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="c790d-125">ToolTip — omówienie</span><span class="sxs-lookup"><span data-stu-id="c790d-125">ToolTip Overview</span></span>](tooltip-overview.md)
