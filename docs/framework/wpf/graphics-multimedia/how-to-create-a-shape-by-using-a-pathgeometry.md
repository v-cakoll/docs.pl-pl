---
title: 'Instrukcje: Tworzenie kształtu przy użyciu elementu PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: b0ab703596612524881ab892a1095b0f49cd1551
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159318"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="b32ec-102">Instrukcje: Tworzenie kształtu przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="b32ec-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="b32ec-103">W tym przykładzie pokazano, jak utworzyć kształt używając <xref:System.Windows.Media.PathGeometry> klasy.</span><span class="sxs-lookup"><span data-stu-id="b32ec-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <xref:System.Windows.Media.PathGeometry> <span data-ttu-id="b32ec-104">obiekty składają się z co najmniej jeden <xref:System.Windows.Media.PathFigure> obiektów; każdy <xref:System.Windows.Media.PathFigure> reprezentuje różne "rysunek" lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="b32ec-104">objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="b32ec-105">Każdy <xref:System.Windows.Media.PathFigure> sam składa się z co najmniej jeden <xref:System.Windows.Media.PathSegment> obiektów, każdy reprezentuje połączone część rysunek lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="b32ec-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="b32ec-106">Segment typy obejmują <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, i <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="b32ec-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b32ec-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b32ec-107">Example</span></span>  
 <span data-ttu-id="b32ec-108">W poniższym przykładzie użyto <xref:System.Windows.Media.PathGeometry> utworzyć trójkąt.</span><span class="sxs-lookup"><span data-stu-id="b32ec-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="b32ec-109"><xref:System.Windows.Media.PathGeometry> Jest wyświetlana przy użyciu <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="b32ec-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="b32ec-110">Poniższa ilustracja przedstawia kształtem utworzona w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b32ec-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="b32ec-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="b32ec-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="b32ec-112">Trójkąt utworzone przy PathGeometry</span><span class="sxs-lookup"><span data-stu-id="b32ec-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="b32ec-113">W poprzednim przykładzie pokazano, jak utworzyć kształt stosunkowo prosty trójkąt.</span><span class="sxs-lookup"><span data-stu-id="b32ec-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="b32ec-114">Element <xref:System.Windows.Media.PathGeometry> może również służyć do utworzenia bardziej złożonych kształtów, między innymi, krzywych i łuki.</span><span class="sxs-lookup"><span data-stu-id="b32ec-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="b32ec-115">Aby uzyskać przykłady, zobacz [tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md), [Utwórz krzywą Beziera trzeciego stopnia](how-to-create-a-cubic-bezier-curve.md), i [Utwórz krzywą Beziera drugiego stopnia](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="b32ec-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="b32ec-116">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="b32ec-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b32ec-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b32ec-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="b32ec-118">Przegląd Geometria</span><span class="sxs-lookup"><span data-stu-id="b32ec-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="b32ec-119">Przykładowe geometrii</span><span class="sxs-lookup"><span data-stu-id="b32ec-119">Geometries Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159989)
