---
title: Jak utworzyć wiele podścieżek w obrębie PathGeometry
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559334"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="00af8-102">Jak utworzyć wiele podścieżek w obrębie PathGeometry</span><span class="sxs-lookup"><span data-stu-id="00af8-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="00af8-103">W tym przykładzie przedstawiono sposób tworzenia wielu podrzędne w <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="00af8-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="00af8-104">Aby utworzyć wiele ścieżek podrzędnych, należy utworzyć <xref:System.Windows.Media.PathFigure> dla podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="00af8-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00af8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="00af8-105">Example</span></span>  
 <span data-ttu-id="00af8-106">Poniższy przykład tworzy dwie ścieżki podrzędne, każdy z nich trójkąt.</span><span class="sxs-lookup"><span data-stu-id="00af8-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="00af8-107">Poniższy przykład przedstawia sposób tworzenia wielu ścieżek podrzędnych za pomocą <xref:System.Windows.Shapes.Path> i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu składni.</span><span class="sxs-lookup"><span data-stu-id="00af8-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="00af8-108">Każdy `M` tworzy nowy podrzędną, dzięki czemu w przykładzie jest tworzony dwie ścieżki podrzędne, że każdy rysowania trójkąt.</span><span class="sxs-lookup"><span data-stu-id="00af8-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="00af8-109">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, wersja wagi jaśniejszego <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="00af8-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="00af8-110">Aby uzyskać więcej informacji, zobacz [składnia znacznika ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="00af8-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00af8-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00af8-111">See Also</span></span>  
 [<span data-ttu-id="00af8-112">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="00af8-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
