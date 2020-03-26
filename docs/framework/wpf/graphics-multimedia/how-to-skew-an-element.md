---
title: Jak pochylić element
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112027"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="a6fa3-102">Jak pochylić element</span><span class="sxs-lookup"><span data-stu-id="a6fa3-102">How to: Skew an Element</span></span>
<span data-ttu-id="a6fa3-103">W tym przykładzie <xref:System.Windows.Media.SkewTransform> pokazano, jak użyć a pochylić element.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="a6fa3-104">Pochylenie, które jest również znane jako ścinanie, jest transformacją, która rozciąga przestrzeń współrzędnych w sposób nieujemny.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="a6fa3-105">Jednym z typowych zastosowań <xref:System.Windows.Media.SkewTransform> jest symulowanie głębi 3D w obiektach 2D.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3D depth in 2D objects.</span></span>  
  
 <span data-ttu-id="a6fa3-106">Użyj <xref:System.Windows.Media.SkewTransform.CenterX%2A> właściwości <xref:System.Windows.Media.SkewTransform.CenterY%2A> i, aby określić <xref:System.Windows.Media.SkewTransform>punkt środkowy .</span><span class="sxs-lookup"><span data-stu-id="a6fa3-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="a6fa3-107">Użyj <xref:System.Windows.Media.SkewTransform.AngleX%2A> właściwości <xref:System.Windows.Media.SkewTransform.AngleY%2A> i, aby określić kąt pochylenia osi x i osi y oraz pochylić bieżący układ współrzędnych wzdłuż tych osi.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="a6fa3-108">Aby przewidzieć efekt transformacji pochylenia, należy wziąć pod uwagę, że <xref:System.Windows.Media.SkewTransform.AngleX%2A> pochyla wartości osi x względem oryginalnego układu współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="a6fa3-109">W związku z <xref:System.Windows.Media.SkewTransform.AngleX%2A> tym dla osi y y obraca się o 30 stopni przez początek układu współrzędnych i pochyla wartości w x- o 30 stopni od tego początku.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="a6fa3-110">Podobnie, <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 pochyla wartości y kształtu o 30 stopni od początku układu współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="a6fa3-111">Należy zauważyć, że nie jest to ten sam efekt, co tłumaczenie (przenoszenie) układu współrzędnych o 30 stopni w x- lub y-.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="a6fa3-112">W poniższym przykładzie stosuje się pochylenie poziome o 45 stopni do <xref:System.Windows.Shapes.Rectangle> punktu środkowego (0,0).</span><span class="sxs-lookup"><span data-stu-id="a6fa3-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6fa3-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6fa3-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="a6fa3-114">W poniższym przykładzie stosuje się pochylenie poziome o 45 stopni do <xref:System.Windows.Shapes.Rectangle> punktu środkowego (25,25).</span><span class="sxs-lookup"><span data-stu-id="a6fa3-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="a6fa3-115">W poniższym przykładzie stosuje się pochylenie pionowe o 45 stopni do <xref:System.Windows.Shapes.Rectangle> punktu środkowego (25,25).</span><span class="sxs-lookup"><span data-stu-id="a6fa3-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="a6fa3-116">Na poniższej ilustracji przedstawiono różne pochylenia, które są używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a6fa3-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="a6fa3-117">![Przykłady skewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="a6fa3-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="a6fa3-118">Trzy przykłady SkewTransform zilustrowane</span><span class="sxs-lookup"><span data-stu-id="a6fa3-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="a6fa3-119">Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="a6fa3-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fa3-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6fa3-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="a6fa3-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="a6fa3-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="a6fa3-122">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="a6fa3-122">How-to Topics</span></span>](transformations-how-to-topics.md)
