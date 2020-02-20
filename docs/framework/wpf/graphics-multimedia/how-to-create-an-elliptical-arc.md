---
title: Jak utworzyć łuk eliptyczny
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453068"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="f72c4-102">Jak utworzyć łuk eliptyczny</span><span class="sxs-lookup"><span data-stu-id="f72c4-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="f72c4-103">Ten przykład pokazuje, jak narysować Łuk eliptyczny. Aby utworzyć Łuk eliptyczny, użyj klas <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>i <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="f72c4-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72c4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f72c4-104">Example</span></span>  
 <span data-ttu-id="f72c4-105">W poniższych przykładach Łuk eliptyczny jest rysowany z (10 100) do (200 100).</span><span class="sxs-lookup"><span data-stu-id="f72c4-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="f72c4-106">Łuk ma <xref:System.Windows.Media.ArcSegment.Size%2A> 100 przez 50 pikseli niezależnych od urządzenia, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> z 45 stopni, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ustawienie `true`i <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="f72c4-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="f72c4-107">formatu</span><span class="sxs-lookup"><span data-stu-id="f72c4-107">[xaml]</span></span>  
  
 <span data-ttu-id="f72c4-108">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f72c4-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="f72c4-109">formatu</span><span class="sxs-lookup"><span data-stu-id="f72c4-109">[xaml]</span></span>  
  
 <span data-ttu-id="f72c4-110">(Należy zauważyć, że ta składnia atrybutu w rzeczywistości tworzy <xref:System.Windows.Media.StreamGeometry>, a jaśniejszą wersję wagi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f72c4-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="f72c4-111">Aby uzyskać więcej informacji, zobacz stronę [składnia znaczników ścieżki](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="f72c4-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="f72c4-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można również narysować Łuk eliptyczny przez jawne użycie tagów obiektów.</span><span class="sxs-lookup"><span data-stu-id="f72c4-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="f72c4-113">Poniżej znajduje się odpowiednik poprzedzającego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznika.</span><span class="sxs-lookup"><span data-stu-id="f72c4-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="f72c4-114">Ten przykład jest częścią większego przykładu.</span><span class="sxs-lookup"><span data-stu-id="f72c4-114">This example is part of a larger sample.</span></span> <span data-ttu-id="f72c4-115">Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="f72c4-115">For the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72c4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f72c4-116">See also</span></span>

- [<span data-ttu-id="f72c4-117">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="f72c4-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="f72c4-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="f72c4-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
