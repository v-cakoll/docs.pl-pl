---
title: 'Instrukcje: Utwórz łuk eliptyczny'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: bb4b4d99aab9daef70f446af176bb462b0661d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354352"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="5c323-102">Instrukcje: Utwórz łuk eliptyczny</span><span class="sxs-lookup"><span data-stu-id="5c323-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="5c323-103">Ten przykład przedstawia sposób rysowania łuk eliptyczny. Aby utworzyć łuk eliptyczny, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.ArcSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="5c323-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c323-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c323-104">Example</span></span>  
 <span data-ttu-id="5c323-105">W poniższych przykładach łuk eliptyczny jest rysowana od (10,100) do (200,100).</span><span class="sxs-lookup"><span data-stu-id="5c323-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="5c323-106">Łuk <xref:System.Windows.Media.ArcSegment.Size%2A> 100, 50 pikseli niezależnych od urządzenia, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stopni <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ustawienie `true`, a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="5c323-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="5c323-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="5c323-107">[xaml]</span></span>  
  
 <span data-ttu-id="5c323-108">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="5c323-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="5c323-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="5c323-109">[xaml]</span></span>  
  
 <span data-ttu-id="5c323-110">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="5c323-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="5c323-111">Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="5c323-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="5c323-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można też rysować łuk eliptyczny przez jawnie przy użyciu tagów obiekt.</span><span class="sxs-lookup"><span data-stu-id="5c323-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="5c323-113">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.</span><span class="sxs-lookup"><span data-stu-id="5c323-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="5c323-114">W tym przykładzie jest częścią większego przykładu.</span><span class="sxs-lookup"><span data-stu-id="5c323-114">This example is part of a larger sample.</span></span> <span data-ttu-id="5c323-115">Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="5c323-115">For the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c323-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c323-116">See also</span></span>
- [<span data-ttu-id="5c323-117">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="5c323-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="5c323-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="5c323-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
