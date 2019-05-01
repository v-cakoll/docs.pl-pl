---
title: 'Instrukcje: Tworzenie wielu podścieżek w obrębie elementu PathGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904725"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="9e71d-102">Instrukcje: Tworzenie wielu podścieżek w obrębie elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="9e71d-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="9e71d-103">W tym przykładzie pokazano, jak utworzyć wiele podścieżek w <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9e71d-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="9e71d-104">Aby utworzyć wiele podścieżek, należy utworzyć <xref:System.Windows.Media.PathFigure> dla podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9e71d-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e71d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e71d-105">Example</span></span>  
 <span data-ttu-id="9e71d-106">Poniższy przykład tworzy dwie ścieżki podrzędne, każdy z nich trójkąt.</span><span class="sxs-lookup"><span data-stu-id="9e71d-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="9e71d-107">Poniższy przykład pokazuje, jak utworzyć wiele podścieżek przy użyciu <xref:System.Windows.Shapes.Path> i [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu składni.</span><span class="sxs-lookup"><span data-stu-id="9e71d-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="9e71d-108">Każdy `M` przykład tworzy dwie ścieżki podrzędne, że każdy Rysowanie trójkąt tworzy nowy podrzędną.</span><span class="sxs-lookup"><span data-stu-id="9e71d-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="9e71d-109">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9e71d-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="9e71d-110">Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="9e71d-110">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e71d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e71d-111">See also</span></span>

- [<span data-ttu-id="9e71d-112">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="9e71d-112">Geometry Overview</span></span>](geometry-overview.md)
