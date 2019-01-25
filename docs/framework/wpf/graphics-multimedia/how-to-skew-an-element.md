---
title: 'Instrukcje: Pochyl element'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 0ba5f3645156459a711d88b7330b221a5d083e7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611335"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="7dac0-102">Instrukcje: Pochyl element</span><span class="sxs-lookup"><span data-stu-id="7dac0-102">How to: Skew an Element</span></span>
<span data-ttu-id="7dac0-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.SkewTransform> do Pochyl element.</span><span class="sxs-lookup"><span data-stu-id="7dac0-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="7dac0-104">Przesunięcia czasowego, który jest znany także jako Pochyl, to przekształcenie, które rozciąga przestrzeni współrzędnych w sposób obsługuje technologię niejednolitego.</span><span class="sxs-lookup"><span data-stu-id="7dac0-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="7dac0-105">Jednym z zastosowań typowe <xref:System.Windows.Media.SkewTransform> jest symulowania [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] głębokość w [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="7dac0-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="7dac0-106">Użyj <xref:System.Windows.Media.SkewTransform.CenterX%2A> i <xref:System.Windows.Media.SkewTransform.CenterY%2A> punkt właściwości, aby określić Centrum <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="7dac0-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="7dac0-107">Użyj <xref:System.Windows.Media.SkewTransform.AngleX%2A> i <xref:System.Windows.Media.SkewTransform.AngleY%2A> właściwości do określenia kąta pochylenie w osi x i y oraz pochylanie bieżący układ współrzędnych wzdłuż tych osi.</span><span class="sxs-lookup"><span data-stu-id="7dac0-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="7dac0-108">Do przewidywania wpływu transformację pochylenia, rozważ <xref:System.Windows.Media.SkewTransform.AngleX%2A> pochyla wartości osi x, względem oryginalnego współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7dac0-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="7dac0-109">W związku z tym, aby uzyskać <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, oś y obraca się 30 stopni za pośrednictwem źródła i pochyla wartości x — 30 stopni z tego źródła.</span><span class="sxs-lookup"><span data-stu-id="7dac0-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="7dac0-110">Podobnie <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 pochyla wartości y kształtu o 30 stopni ze źródła.</span><span class="sxs-lookup"><span data-stu-id="7dac0-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="7dac0-111">Należy pamiętać, że nie jest taki sam skutek jak tłumaczenia (przenoszenie) współrzędnych przez 30 stopni w x i y.</span><span class="sxs-lookup"><span data-stu-id="7dac0-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="7dac0-112">Następujący przykład dotyczy poziomej przesunięcia czasowego 45 stopni na <xref:System.Windows.Shapes.Rectangle> z punktu centralnego (0,0).</span><span class="sxs-lookup"><span data-stu-id="7dac0-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dac0-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="7dac0-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="7dac0-114">Następujący przykład dotyczy poziomej przesunięcia czasowego 45 stopni na <xref:System.Windows.Shapes.Rectangle> z punktu centralnego (25,25).</span><span class="sxs-lookup"><span data-stu-id="7dac0-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="7dac0-115">Następujący przykład dotyczy pionowej przesunięcia czasowego 45 stopni na <xref:System.Windows.Shapes.Rectangle> z punktu centralnego (25,25).</span><span class="sxs-lookup"><span data-stu-id="7dac0-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="7dac0-116">Poniższa ilustracja przedstawia różne niesymetryczności, które są używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7dac0-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="7dac0-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="7dac0-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="7dac0-118">Przedstawione trzy przykłady SkewTransform —</span><span class="sxs-lookup"><span data-stu-id="7dac0-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="7dac0-119">Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="7dac0-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dac0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dac0-120">See also</span></span>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="7dac0-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="7dac0-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="7dac0-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="7dac0-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
