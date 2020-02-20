---
title: Jak utworzyć krzywą Beziera trzeciego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452113"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="1ce83-102">Jak utworzyć krzywą Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="1ce83-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="1ce83-103">Ten przykład pokazuje, jak utworzyć wskaźnik krzywej Beziera w postaci sześciennej.</span><span class="sxs-lookup"><span data-stu-id="1ce83-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="1ce83-104">Aby utworzyć w sześciennej krzywej Beziera, użyj klas <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>i <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="1ce83-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="1ce83-105">Aby wyświetlić wyniki geometryczne, użyj elementu <xref:System.Windows.Shapes.Path> lub użyj go z <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="1ce83-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="1ce83-106">W poniższych przykładowych krzywych Beziera jest rysowana od (10, 100) do (300, 100).</span><span class="sxs-lookup"><span data-stu-id="1ce83-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="1ce83-107">Krzywa ma punkty kontrolne (100, 0) i (200, 200).</span><span class="sxs-lookup"><span data-stu-id="1ce83-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ce83-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ce83-108">Example</span></span>  
 <span data-ttu-id="1ce83-109">formatu</span><span class="sxs-lookup"><span data-stu-id="1ce83-109">[xaml]</span></span>  
  
 <span data-ttu-id="1ce83-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można użyć skróconej składni znaczników do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="1ce83-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="1ce83-111">formatu</span><span class="sxs-lookup"><span data-stu-id="1ce83-111">[xaml]</span></span>  
  
 <span data-ttu-id="1ce83-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można również narysować zakrzywioną krzywą Beziera przy użyciu tagów obiektów.</span><span class="sxs-lookup"><span data-stu-id="1ce83-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="1ce83-113">Poniżej znajduje się odpowiednik powyższego przykładu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ce83-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="1ce83-114">Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="1ce83-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce83-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ce83-115">See also</span></span>

- [<span data-ttu-id="1ce83-116">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="1ce83-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="1ce83-117">Tworzenie obiektu LineSegment w elemencie PathGeometry</span><span class="sxs-lookup"><span data-stu-id="1ce83-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="1ce83-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="1ce83-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="1ce83-119">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="1ce83-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
