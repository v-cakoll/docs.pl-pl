---
title: Jak utworzyć krzywą Beziera trzeciego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 2dd9dfa7f15ce00261c87f316079c25a7aa52532
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743193"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="5d9a8-102">Jak utworzyć krzywą Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="5d9a8-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="5d9a8-103">W tym przykładzie pokazano, jak utworzyć krzywą Beziera trzeciego stopnia.</span><span class="sxs-lookup"><span data-stu-id="5d9a8-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="5d9a8-104">Aby utworzyć krzywą Beziera trzeciego stopnia, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.BezierSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d9a8-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="5d9a8-105">Aby wyświetlić wynikowe geometry, użyj <xref:System.Windows.Shapes.Path> elementu, lub korzystać z niej za pomocą <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="5d9a8-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="5d9a8-106">W poniższych przykładach krzywą Beziera trzeciego stopnia jest rysowana od (10, 100) na (300, 100).</span><span class="sxs-lookup"><span data-stu-id="5d9a8-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="5d9a8-107">Krzywa ma punkty kontrolne (100, 0) i (200, 200).</span><span class="sxs-lookup"><span data-stu-id="5d9a8-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d9a8-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d9a8-108">Example</span></span>  
 <span data-ttu-id="5d9a8-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="5d9a8-109">[xaml]</span></span>  
  
 <span data-ttu-id="5d9a8-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], może użyć znaczników skróconej składni opisujący ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5d9a8-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="5d9a8-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="5d9a8-111">[xaml]</span></span>  
  
 <span data-ttu-id="5d9a8-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można też rysować krzywą Beziera trzeciego stopnia przy użyciu tagów obiekt.</span><span class="sxs-lookup"><span data-stu-id="5d9a8-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="5d9a8-113">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="5d9a8-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="5d9a8-114">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="5d9a8-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9a8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d9a8-115">See Also</span></span>  
 [<span data-ttu-id="5d9a8-116">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="5d9a8-116">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="5d9a8-117">Tworzenie obiektu LineSegment w elemencie PathGeometry</span><span class="sxs-lookup"><span data-stu-id="5d9a8-117">Create a LineSegment in a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [<span data-ttu-id="5d9a8-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="5d9a8-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [<span data-ttu-id="5d9a8-119">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="5d9a8-119">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
