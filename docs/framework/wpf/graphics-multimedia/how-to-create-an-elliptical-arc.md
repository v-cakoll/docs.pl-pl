---
title: Jak utworzyć łuk eliptyczny
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: 7ca7d06aa25f8dfae648d8c54c8b95cc277ffbf9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43722950"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="ff858-102">Jak utworzyć łuk eliptyczny</span><span class="sxs-lookup"><span data-stu-id="ff858-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="ff858-103">Ten przykład przedstawia sposób rysowania łuk eliptyczny. Aby utworzyć łuk eliptyczny, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.ArcSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="ff858-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff858-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff858-104">Example</span></span>  
 <span data-ttu-id="ff858-105">W poniższych przykładach łuk eliptyczny jest rysowana od (10,100) do (200,100).</span><span class="sxs-lookup"><span data-stu-id="ff858-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="ff858-106">Łuk <xref:System.Windows.Media.ArcSegment.Size%2A> 100, 50 pikseli niezależnych od urządzenia, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stopni <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ustawienie `true`, a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="ff858-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="ff858-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="ff858-107">[xaml]</span></span>  
  
 <span data-ttu-id="ff858-108">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ff858-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="ff858-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="ff858-109">[xaml]</span></span>  
  
 <span data-ttu-id="ff858-110">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="ff858-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="ff858-111">Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="ff858-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="ff858-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można też rysować łuk eliptyczny przez jawnie przy użyciu tagów obiekt.</span><span class="sxs-lookup"><span data-stu-id="ff858-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="ff858-113">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.</span><span class="sxs-lookup"><span data-stu-id="ff858-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="ff858-114">W tym przykładzie jest częścią większego przykładu.</span><span class="sxs-lookup"><span data-stu-id="ff858-114">This example is part of a larger sample.</span></span> <span data-ttu-id="ff858-115">Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="ff858-115">For the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff858-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff858-116">See Also</span></span>  
 [<span data-ttu-id="ff858-117">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="ff858-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="ff858-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="ff858-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
