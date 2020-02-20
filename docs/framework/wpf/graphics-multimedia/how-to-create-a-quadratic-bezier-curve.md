---
title: Jak utworzyć krzywą Beziera drugiego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452074"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="e13c0-102">Jak utworzyć krzywą Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="e13c0-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="e13c0-103">Ten przykład pokazuje, jak utworzyć krzywą Beziera kwadratu.</span><span class="sxs-lookup"><span data-stu-id="e13c0-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="e13c0-104">Aby utworzyć krzywą Beziera kwadratu, użyj klas <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>i <xref:System.Windows.Media.QuadraticBezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="e13c0-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e13c0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e13c0-105">Example</span></span>  
 <span data-ttu-id="e13c0-106">W poniższych przykładach krzywa Beziera kwadratu jest rysowana od (10 100) do (300 100).</span><span class="sxs-lookup"><span data-stu-id="e13c0-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="e13c0-107">Krzywa ma punkt kontrolny (200 200).</span><span class="sxs-lookup"><span data-stu-id="e13c0-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="e13c0-108">formatu</span><span class="sxs-lookup"><span data-stu-id="e13c0-108">[xaml]</span></span>  
  
 <span data-ttu-id="e13c0-109">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e13c0-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="e13c0-110">formatu</span><span class="sxs-lookup"><span data-stu-id="e13c0-110">[xaml]</span></span>  
  
 <span data-ttu-id="e13c0-111">(Należy zauważyć, że ta składnia atrybutu w rzeczywistości tworzy <xref:System.Windows.Media.StreamGeometry>, a jaśniejszą wersję wagi <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e13c0-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e13c0-112">Aby uzyskać więcej informacji, zobacz stronę [składnia znaczników ścieżki](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="e13c0-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="e13c0-113">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]można również narysować krzywą Beziera kwadratowego przy użyciu składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="e13c0-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="e13c0-114">Poniżej znajduje się odpowiednik powyższego przykładu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e13c0-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="e13c0-115">Ten przykład jest częścią większego przykładu; Aby uzyskać kompletny przykład, zobacz [przykład geometrie](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="e13c0-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13c0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e13c0-116">See also</span></span>

- [<span data-ttu-id="e13c0-117">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="e13c0-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="e13c0-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="e13c0-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
