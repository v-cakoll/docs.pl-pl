---
title: Jak utworzyć krzywą Beziera drugiego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 8481a7e0e6d682a335b22ea6cdf73a23a9f155af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085835"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="daa49-102">Jak utworzyć krzywą Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="daa49-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="daa49-103">W tym przykładzie pokazano, jak utworzyć krzywą Beziera drugiego stopnia.</span><span class="sxs-lookup"><span data-stu-id="daa49-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="daa49-104">Aby utworzyć krzywą Beziera drugiego stopnia, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.QuadraticBezierSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="daa49-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daa49-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="daa49-105">Example</span></span>  
 <span data-ttu-id="daa49-106">W poniższych przykładach krzywą Beziera drugiego stopnia jest rysowana od (10,100) do (300,100).</span><span class="sxs-lookup"><span data-stu-id="daa49-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="daa49-107">Krzywa ma punkt kontrolny w (200,200).</span><span class="sxs-lookup"><span data-stu-id="daa49-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="daa49-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="daa49-108">[xaml]</span></span>  
  
 <span data-ttu-id="daa49-109">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="daa49-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="daa49-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="daa49-110">[xaml]</span></span>  
  
 <span data-ttu-id="daa49-111">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="daa49-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="daa49-112">Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="daa49-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="daa49-113">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], może również zwracać krzywą Beziera drugiego stopnia stosowanie składni obiektów.</span><span class="sxs-lookup"><span data-stu-id="daa49-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="daa49-114">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="daa49-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="daa49-115">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="daa49-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa49-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daa49-116">See Also</span></span>  
 [<span data-ttu-id="daa49-117">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="daa49-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="daa49-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="daa49-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
