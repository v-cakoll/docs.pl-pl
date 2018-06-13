---
title: Jak utworzyć krzywą Beziera drugiego stopnia
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 9d389125b6ad09833a16b64cb8f498cc20d4e79c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558894"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="91042-102">Jak utworzyć krzywą Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="91042-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="91042-103">W tym przykładzie przedstawiono sposób tworzenia kwadratową krzywą Beziera.</span><span class="sxs-lookup"><span data-stu-id="91042-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="91042-104">Aby utworzyć kwadratową krzywej Beziera, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.QuadraticBezierSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="91042-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91042-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="91042-105">Example</span></span>  
 <span data-ttu-id="91042-106">W poniższych przykładach kwadratową krzywej Beziera jest przenoszony z (10,100) do (300,100).</span><span class="sxs-lookup"><span data-stu-id="91042-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="91042-107">Krzywej ma punkt kontrolny w (200,200).</span><span class="sxs-lookup"><span data-stu-id="91042-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="91042-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="91042-108">[xaml]</span></span>  
  
 <span data-ttu-id="91042-109">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], za pomocą składni atrybut opisujący ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="91042-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="91042-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="91042-110">[xaml]</span></span>  
  
 <span data-ttu-id="91042-111">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, wersja wagi jaśniejszego <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="91042-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="91042-112">Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="91042-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="91042-113">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], może również zwrócić kwadratową krzywej Beziera przy użyciu składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="91042-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="91042-114">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="91042-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="91042-115">Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="91042-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91042-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91042-116">See Also</span></span>  
 [<span data-ttu-id="91042-117">Tworzenie łuku eliptycznego</span><span class="sxs-lookup"><span data-stu-id="91042-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="91042-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="91042-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
