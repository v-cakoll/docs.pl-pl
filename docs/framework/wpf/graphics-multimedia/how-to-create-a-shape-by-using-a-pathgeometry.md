---
title: Jak utworzyć kształt używając PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452048"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="71389-102">Jak utworzyć kształt używając PathGeometry</span><span class="sxs-lookup"><span data-stu-id="71389-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="71389-103">Ten przykład przedstawia sposób tworzenia kształtu przy użyciu klasy <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="71389-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="71389-104">obiekty <xref:System.Windows.Media.PathGeometry> składają się z co najmniej jednego obiektu <xref:System.Windows.Media.PathFigure>; Każda <xref:System.Windows.Media.PathFigure> reprezentuje inny "rysunek" lub "kształt".</span><span class="sxs-lookup"><span data-stu-id="71389-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="71389-105">Każda <xref:System.Windows.Media.PathFigure> jest sama składająca się z co najmniej jednego obiektu <xref:System.Windows.Media.PathSegment>, z których każdy reprezentuje podłączoną część rysunku lub kształtu.</span><span class="sxs-lookup"><span data-stu-id="71389-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="71389-106">Typy segmentów obejmują <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>i <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="71389-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71389-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="71389-107">Example</span></span>  
 <span data-ttu-id="71389-108">Poniższy przykład używa <xref:System.Windows.Media.PathGeometry>, aby utworzyć trójkąt.</span><span class="sxs-lookup"><span data-stu-id="71389-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="71389-109"><xref:System.Windows.Media.PathGeometry> jest wyświetlana przy użyciu elementu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="71389-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="71389-110">Na poniższej ilustracji przedstawiono kształt utworzony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71389-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="71389-111">![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="71389-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="71389-112">Trójkąt utworzony przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="71389-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="71389-113">W poprzednim przykładzie pokazano, jak utworzyć stosunkowo prosty kształt, Trójkąt.</span><span class="sxs-lookup"><span data-stu-id="71389-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="71389-114"><xref:System.Windows.Media.PathGeometry> można również użyć do tworzenia bardziej złożonych kształtów, w tym łuków i krzywych.</span><span class="sxs-lookup"><span data-stu-id="71389-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="71389-115">Aby zapoznać się z przykładami, zobacz [Tworzenie łuku eliptycznego](how-to-create-an-elliptical-arc.md), [Tworzenie zakrzywionej krzywej Beziera](how-to-create-a-cubic-bezier-curve.md)i [Tworzenie krzywej Beziera kwadratowego](how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="71389-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="71389-116">Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="71389-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71389-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71389-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="71389-118">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="71389-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="71389-119">Przykład geometrie</span><span class="sxs-lookup"><span data-stu-id="71389-119">Geometries Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
