---
title: 'Instrukcje: Rysowanie wielokąta przy użyciu elementu wielokątnego'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934964"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="5c0cf-102">Instrukcje: Rysowanie wielokąta przy użyciu elementu wielokątnego</span><span class="sxs-lookup"><span data-stu-id="5c0cf-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="5c0cf-103">Ten przykład pokazuje, jak narysować linię łamaną, która jest serią połączonych linii przy użyciu <xref:System.Windows.Shapes.Polyline> elementu.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="5c0cf-104">Aby narysować linię łamaną, Utwórz <xref:System.Windows.Shapes.Polyline> element i użyj jego <xref:System.Windows.Shapes.Polyline.Points%2A> właściwości, aby określić wierzchołki kształtu.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="5c0cf-105">Na koniec Użyj <xref:System.Windows.Shapes.Shape.Stroke%2A> właściwości i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> , aby opisać kontur linii łamanej, ponieważ linia bez pociągnięcia jest niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c0cf-106">Ponieważ element nie jest zamkniętym kształtem <xref:System.Windows.Shapes.Shape.Fill%2A> , właściwość nie ma żadnego efektu, nawet jeśli odcelowo zamknie konspekt kształtu. <xref:System.Windows.Shapes.Polyline></span><span class="sxs-lookup"><span data-stu-id="5c0cf-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="5c0cf-107">Aby utworzyć zamknięty kształt z <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Polygon> Użyj elementu.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="5c0cf-108">Poniższy przykład rysuje dwa <xref:System.Windows.Shapes.Polyline> elementy <xref:System.Windows.Controls.Canvas>wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c0cf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c0cf-109">Example</span></span>  
 <span data-ttu-id="5c0cf-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]programie prawidłowa składnia dla punktów to rozdzielana spacjami lista par współrzędnych x i y oddzielanych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="5c0cf-111">Mimo że w tym przykładzie <xref:System.Windows.Controls.Canvas> używa się, aby zawierać linie łamane, można użyć elementów łamaną (i wszystkich innych elementów kształtu) z dowolnym <xref:System.Windows.Controls.Panel> lub <xref:System.Windows.Controls.Control> obsługującym zawartość nietekstową.</span><span class="sxs-lookup"><span data-stu-id="5c0cf-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="5c0cf-112">Ten przykład jest częścią większego przykładu; Aby uzyskać pełną próbkę, zobacz [Przykładowe elementy Shape](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="5c0cf-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0cf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c0cf-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="5c0cf-114">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="5c0cf-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="5c0cf-115">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="5c0cf-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
