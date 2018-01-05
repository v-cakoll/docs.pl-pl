---
title: "Jak pochylić element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9da10e4eb6cf045c6c4936b76f847f21ea1495e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="96827-102">Jak pochylić element</span><span class="sxs-lookup"><span data-stu-id="96827-102">How to: Skew an Element</span></span>
<span data-ttu-id="96827-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.SkewTransform> fałszować elementu.</span><span class="sxs-lookup"><span data-stu-id="96827-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="96827-104">Zegara, który jest również nazywany Ścinanie, jest transformację w sposób niejednolitego rozciąga się przestrzeni współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="96827-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="96827-105">Jeden typowy sposób użycia protokołu <xref:System.Windows.Media.SkewTransform> jest symulowanie [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] głębokość [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="96827-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="96827-106">Użyj <xref:System.Windows.Media.SkewTransform.CenterX%2A> i <xref:System.Windows.Media.SkewTransform.CenterY%2A> punkt właściwości, aby określić Centrum <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="96827-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="96827-107">Użyj <xref:System.Windows.Media.SkewTransform.AngleX%2A> i <xref:System.Windows.Media.SkewTransform.AngleY%2A> właściwości do określenia kąta pochylenia osi x i y i pochylanie bieżący układ współrzędnych wzdłuż osi te.</span><span class="sxs-lookup"><span data-stu-id="96827-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="96827-108">Przewidywanie efekt transformację pochylenia, rozważ <xref:System.Windows.Media.SkewTransform.AngleX%2A> pochyla wartości na osi x względem oryginalnego układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="96827-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="96827-109">W związku z tym dla <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, oś y obraca 30 stopni za pośrednictwem źródła i pochyla wartości x-o 30 stopni z tego źródła.</span><span class="sxs-lookup"><span data-stu-id="96827-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="96827-110">Podobnie <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 pochyla wartości y kształtu przez 30 stopni ze źródła.</span><span class="sxs-lookup"><span data-stu-id="96827-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="96827-111">Należy pamiętać, że nie jest to ten sam efekt co tłumaczenia (przenoszenia) współrzędnych przez 30 stopni w x i y.</span><span class="sxs-lookup"><span data-stu-id="96827-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="96827-112">Poniższy przykład dotyczy pochylenie w poziomie 45 stopni do <xref:System.Windows.Shapes.Rectangle> od środka (0,0).</span><span class="sxs-lookup"><span data-stu-id="96827-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96827-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="96827-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="96827-114">Poniższy przykład dotyczy pochylenie w poziomie 45 stopni do <xref:System.Windows.Shapes.Rectangle> od punktu center (25,25).</span><span class="sxs-lookup"><span data-stu-id="96827-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="96827-115">Poniższy przykład dotyczy pochylenie w pionie 45 stopni do <xref:System.Windows.Shapes.Rectangle> od punktu center (25,25).</span><span class="sxs-lookup"><span data-stu-id="96827-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="96827-116">Na poniższej ilustracji przedstawiono różne pochyla, które są używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="96827-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="96827-117">![Przykłady obiektu SkewTransform](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="96827-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="96827-118">Trzy przedstawione przykłady obiektu SkewTransform</span><span class="sxs-lookup"><span data-stu-id="96827-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="96827-119">Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="96827-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96827-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96827-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="96827-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="96827-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="96827-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="96827-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
