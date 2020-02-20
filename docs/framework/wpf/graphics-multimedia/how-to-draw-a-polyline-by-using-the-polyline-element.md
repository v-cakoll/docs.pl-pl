---
title: Jak narysować wielokąt przy użyciu elementu wielokątnego
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452964"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="75fb0-102">Jak narysować wielokąt przy użyciu elementu wielokątnego</span><span class="sxs-lookup"><span data-stu-id="75fb0-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="75fb0-103">Ten przykład pokazuje, jak narysować linię łamaną, która jest serią połączonych linii przy użyciu elementu <xref:System.Windows.Shapes.Polyline>.</span><span class="sxs-lookup"><span data-stu-id="75fb0-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="75fb0-104">Aby narysować linię łamaną, Utwórz <xref:System.Windows.Shapes.Polyline> element i użyj jej właściwości <xref:System.Windows.Shapes.Polyline.Points%2A>, aby określić wierzchołki kształtu.</span><span class="sxs-lookup"><span data-stu-id="75fb0-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="75fb0-105">Na koniec Użyj właściwości <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> do opisania konturu linii łamanej, ponieważ linia bez pociągnięcia jest niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="75fb0-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75fb0-106">Ponieważ element <xref:System.Windows.Shapes.Polyline> nie jest zamkniętym kształtem, właściwość <xref:System.Windows.Shapes.Shape.Fill%2A> nie ma żadnego efektu, nawet jeśli odcelowo zamknie konspekt kształtu.</span><span class="sxs-lookup"><span data-stu-id="75fb0-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="75fb0-107">Aby utworzyć zamknięty kształt z <xref:System.Windows.Shapes.Shape.Fill%2A>, użyj elementu <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="75fb0-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="75fb0-108">Poniższy przykład rysuje dwa elementy <xref:System.Windows.Shapes.Polyline> wewnątrz <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="75fb0-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75fb0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="75fb0-109">Example</span></span>  
 <span data-ttu-id="75fb0-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]prawidłowa składnia dla punktów to rozdzielana spacjami lista par współrzędnych x i y oddzielanych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="75fb0-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="75fb0-111">Chociaż w tym przykładzie użyto <xref:System.Windows.Controls.Canvas>, aby zawierała linie łamane, można użyć elementów łamaną (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control>, które obsługują zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="75fb0-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="75fb0-112">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="75fb0-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fb0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75fb0-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="75fb0-114">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="75fb0-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="75fb0-115">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="75fb0-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
