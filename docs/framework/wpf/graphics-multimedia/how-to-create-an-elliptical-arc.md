---
title: "Jak utworzyć łuk eliptyczny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e11f3e0035c00bbc280b658c0931d57c37524f93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="47de6-102">Jak utworzyć łuk eliptyczny</span><span class="sxs-lookup"><span data-stu-id="47de6-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="47de6-103">W tym przykładzie przedstawiono sposób rysowania łuku. Aby utworzyć łuku, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.ArcSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="47de6-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47de6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="47de6-104">Example</span></span>  
 <span data-ttu-id="47de6-105">W poniższych przykładach łuku jest przenoszony z (10,100) do (200,100).</span><span class="sxs-lookup"><span data-stu-id="47de6-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="47de6-106">Łuk <xref:System.Windows.Media.ArcSegment.Size%2A> 100 przez 50 pikseli niezależnych od urządzenia, <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 stopni <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ustawienie `true`, a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> z <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="47de6-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="47de6-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="47de6-107">[xaml]</span></span>  
  
 <span data-ttu-id="47de6-108">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], za pomocą składni atrybut opisujący ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="47de6-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="47de6-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="47de6-109">[xaml]</span></span>  
  
 <span data-ttu-id="47de6-110">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, wersja wagi jaśniejszego <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="47de6-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="47de6-111">Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="47de6-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="47de6-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], również narysować łuku jawnie przy użyciu tagów object.</span><span class="sxs-lookup"><span data-stu-id="47de6-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="47de6-113">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników.</span><span class="sxs-lookup"><span data-stu-id="47de6-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="47de6-114">Ten przykład jest częścią większego przykładu.</span><span class="sxs-lookup"><span data-stu-id="47de6-114">This example is part of a larger sample.</span></span> <span data-ttu-id="47de6-115">Pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="47de6-115">For the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47de6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47de6-116">See Also</span></span>  
 [<span data-ttu-id="47de6-117">Tworzenie krzywej Beziera drugiego stopnia</span><span class="sxs-lookup"><span data-stu-id="47de6-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="47de6-118">Tworzenie krzywej Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="47de6-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
