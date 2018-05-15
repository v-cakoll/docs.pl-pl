---
title: Jak utworzyć kształt używając PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: 6c77844b054dd89a0c3f3cbecd0725968df9ae71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="180dc-102">Jak utworzyć kształt używając PathGeometry</span><span class="sxs-lookup"><span data-stu-id="180dc-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="180dc-103">W tym przykładzie pokazano, jak utworzyć kształtu przy użyciu <xref:System.Windows.Media.PathGeometry> klasy.</span><span class="sxs-lookup"><span data-stu-id="180dc-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="180dc-104"><xref:System.Windows.Media.PathGeometry> obiekty składają się z co najmniej jeden <xref:System.Windows.Media.PathFigure> obiektów; każda <xref:System.Windows.Media.PathFigure> reprezentuje różne "rysunek" lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="180dc-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="180dc-105">Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jednego <xref:System.Windows.Media.PathSegment> obiekty, każdy reprezentuje połączony fragment rysunku lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="180dc-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="180dc-106">Segment typy <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, i <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="180dc-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="180dc-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="180dc-107">Example</span></span>  
 <span data-ttu-id="180dc-108">W poniższym przykładzie użyto <xref:System.Windows.Media.PathGeometry> utworzyć trójkąt.</span><span class="sxs-lookup"><span data-stu-id="180dc-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="180dc-109"><xref:System.Windows.Media.PathGeometry> Jest wyświetlany za pomocą <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="180dc-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="180dc-110">Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie kształtu.</span><span class="sxs-lookup"><span data-stu-id="180dc-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="180dc-111">![Obiekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="180dc-111">![A PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="180dc-112">Trójkąt utworzone za pomocą PathGeometry</span><span class="sxs-lookup"><span data-stu-id="180dc-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="180dc-113">W poprzednim przykładzie pokazano, jak utworzyć stosunkowo proste kształt trójkąta.</span><span class="sxs-lookup"><span data-stu-id="180dc-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="180dc-114">A <xref:System.Windows.Media.PathGeometry> może również służyć do tworzenia bardziej złożonych kształtów, w tym łuki i krzywych.</span><span class="sxs-lookup"><span data-stu-id="180dc-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="180dc-115">Przykłady można znaleźć [utworzyć łuku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [tworzenie sześcienny krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), i [tworzenie kwadratową krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="180dc-115">For examples, see [Create an Elliptical Arc](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="180dc-116">Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="180dc-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180dc-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="180dc-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [<span data-ttu-id="180dc-118">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="180dc-118">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="180dc-119">Przykładowe mają geometrię</span><span class="sxs-lookup"><span data-stu-id="180dc-119">Geometries Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159989)
