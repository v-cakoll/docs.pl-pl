---
title: Jak ustawić położenie ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186948"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="d0533-102">Jak ustawić położenie ToolTip</span><span class="sxs-lookup"><span data-stu-id="d0533-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="d0533-103">W tym przykładzie pokazano, jak określić położenie etykietki narzędzia na ekranie.</span><span class="sxs-lookup"><span data-stu-id="d0533-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0533-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0533-104">Example</span></span>  
 <span data-ttu-id="d0533-105">Etykietkę narzędzia można umieścić przy użyciu zestawu pięciu właściwości, <xref:System.Windows.Controls.ToolTip> które <xref:System.Windows.Controls.ToolTipService> są zdefiniowane zarówno w klasach, jak i klasach.</span><span class="sxs-lookup"><span data-stu-id="d0533-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="d0533-106">W poniższej tabeli przedstawiono te dwa zestawy pięciu właściwości i zawiera łącza do ich dokumentacji referencyjnej zgodnie z klasą.</span><span class="sxs-lookup"><span data-stu-id="d0533-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="d0533-107">Odpowiednie właściwości etykietki narzędzia zgodnie z klasą</span><span class="sxs-lookup"><span data-stu-id="d0533-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="d0533-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="d0533-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="d0533-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>właściwości klasy</span><span class="sxs-lookup"><span data-stu-id="d0533-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="d0533-110">Jeśli zawartość etykietki narzędzia zostanie zdefiniowana przy użyciu <xref:System.Windows.Controls.ToolTip> obiektu, można użyć właściwości jednej z klas; jednak <xref:System.Windows.Controls.ToolTipService> właściwości mają pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="d0533-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="d0533-111"><xref:System.Windows.Controls.ToolTipService> Właściwości służą do etykietek narzędzi, które <xref:System.Windows.Controls.ToolTip> nie są zdefiniowane jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="d0533-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="d0533-112">Na poniższych ilustracjach pokazano, jak umieścić etykietkę narzędzia przy użyciu tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="d0533-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="d0533-113">Chociaż przykłady na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tych ilustracjach pokazują, jak ustawić właściwości, <xref:System.Windows.Controls.ToolTip> które są zdefiniowane <xref:System.Windows.Controls.ToolTipService> przez klasę, odpowiednie właściwości klasy są zgodne z tymi samymi regułami układu.</span><span class="sxs-lookup"><span data-stu-id="d0533-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="d0533-114">Aby uzyskać więcej informacji na temat możliwych wartości właściwości Umieszczanie, zobacz [Zachowanie umieszczania wyskakujących](popup-placement-behavior.md)okienków .</span><span class="sxs-lookup"><span data-stu-id="d0533-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  

 <span data-ttu-id="d0533-115">Na poniższej ilustracji przedstawiono położenie etykietki narzędzia przy użyciu właściwości Placement:</span><span class="sxs-lookup"><span data-stu-id="d0533-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![Diagram przedstawiający położenie etykietek narzędzi przy użyciu właściwości Placement.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 <span data-ttu-id="d0533-117">Na poniższej ilustracji przedstawiono położenie etykietki narzędzia przy użyciu właściwości Placement i PlacementRectangle:</span><span class="sxs-lookup"><span data-stu-id="d0533-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>

 ![Diagram przedstawiający położenie etykietki narzędzi przy użyciu właściwości PlacementRectangle.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 <span data-ttu-id="d0533-119">Na poniższej ilustracji przedstawiono położenie etykietki narzędzia przy użyciu właściwości Położenie, Rozmieszczenie i Przesunięcie:</span><span class="sxs-lookup"><span data-stu-id="d0533-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>
  
 ![Diagram przedstawiający położenie etykietek narzędzi przy użyciu właściwości Przesunięcie.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="d0533-121">W poniższym przykładzie <xref:System.Windows.Controls.ToolTip> pokazano, jak użyć właściwości, aby określić <xref:System.Windows.Controls.ToolTip> położenie etykietki narzędzia, której zawartość jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="d0533-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="d0533-122">W poniższym przykładzie <xref:System.Windows.Controls.ToolTipService> pokazano, jak użyć właściwości, aby określić <xref:System.Windows.Controls.ToolTip> położenie etykietki narzędzia, której zawartość nie jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="d0533-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="d0533-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0533-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="d0533-124">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="d0533-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="d0533-125">ToolTip — Przegląd</span><span class="sxs-lookup"><span data-stu-id="d0533-125">ToolTip Overview</span></span>](tooltip-overview.md)
