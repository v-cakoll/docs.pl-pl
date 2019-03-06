---
title: 'Instrukcje: Utwórz krzywą Beziera drugiego stopnia'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 8adb5d0348fe53cecbdabf8ffa3b244fe34831e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363725"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="e0eb8-102">Instrukcje: Utwórz krzywą Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="e0eb8-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="e0eb8-103">W tym przykładzie pokazano, jak utworzyć krzywą Beziera drugiego stopnia.</span><span class="sxs-lookup"><span data-stu-id="e0eb8-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="e0eb8-104">Aby utworzyć krzywą Beziera drugiego stopnia, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.QuadraticBezierSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="e0eb8-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0eb8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0eb8-105">Example</span></span>  
 <span data-ttu-id="e0eb8-106">W poniższych przykładach krzywą Beziera drugiego stopnia jest rysowana od (10,100) do (300,100).</span><span class="sxs-lookup"><span data-stu-id="e0eb8-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="e0eb8-107">Krzywa ma punkt kontrolny w (200,200).</span><span class="sxs-lookup"><span data-stu-id="e0eb8-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="e0eb8-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="e0eb8-108">[xaml]</span></span>  
  
 <span data-ttu-id="e0eb8-109">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e0eb8-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="e0eb8-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="e0eb8-110">[xaml]</span></span>  
  
 <span data-ttu-id="e0eb8-111">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e0eb8-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e0eb8-112">Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="e0eb8-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="e0eb8-113">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], może również zwracać krzywą Beziera drugiego stopnia stosowanie składni obiektów.</span><span class="sxs-lookup"><span data-stu-id="e0eb8-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="e0eb8-114">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="e0eb8-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="e0eb8-115">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="e0eb8-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0eb8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0eb8-116">See also</span></span>
- [<span data-ttu-id="e0eb8-117">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="e0eb8-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="e0eb8-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="e0eb8-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
