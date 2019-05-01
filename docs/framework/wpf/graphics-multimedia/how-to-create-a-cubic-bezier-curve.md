---
title: 'Instrukcje: Tworzenie krzywej Beziera trzeciego stopnia'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 36544abc774b7fe82c2ff47483cfedd6fb13e344
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054630"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="be4f2-102">Instrukcje: Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="be4f2-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="be4f2-103">W tym przykładzie pokazano, jak utworzyć krzywą Beziera trzeciego stopnia.</span><span class="sxs-lookup"><span data-stu-id="be4f2-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="be4f2-104">Aby utworzyć krzywą Beziera trzeciego stopnia, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.BezierSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="be4f2-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="be4f2-105">Aby wyświetlić wynikowe geometry, użyj <xref:System.Windows.Shapes.Path> elementu, lub korzystać z niej za pomocą <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="be4f2-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="be4f2-106">W poniższych przykładach krzywą Beziera trzeciego stopnia jest rysowana od (10, 100) na (300, 100).</span><span class="sxs-lookup"><span data-stu-id="be4f2-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="be4f2-107">Krzywa ma punkty kontrolne (100, 0) i (200, 200).</span><span class="sxs-lookup"><span data-stu-id="be4f2-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be4f2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="be4f2-108">Example</span></span>  
 <span data-ttu-id="be4f2-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="be4f2-109">[xaml]</span></span>  
  
 <span data-ttu-id="be4f2-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], może użyć znaczników skróconej składni opisujący ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="be4f2-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="be4f2-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="be4f2-111">[xaml]</span></span>  
  
 <span data-ttu-id="be4f2-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można też rysować krzywą Beziera trzeciego stopnia przy użyciu tagów obiekt.</span><span class="sxs-lookup"><span data-stu-id="be4f2-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="be4f2-113">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="be4f2-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="be4f2-114">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="be4f2-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4f2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be4f2-115">See also</span></span>

- [<span data-ttu-id="be4f2-116">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="be4f2-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="be4f2-117">Tworzenie obiektu LineSegment w elemencie PathGeometry</span><span class="sxs-lookup"><span data-stu-id="be4f2-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="be4f2-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="be4f2-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="be4f2-119">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="be4f2-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
