---
title: Jak animować obiekt na ścieżce (animacja Matrix)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 03e1e40f8ee6840558ad7b712d96e63d9e2bf15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559006"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="a25ce-102">Jak animować obiekt na ścieżce (animacja Matrix)</span><span class="sxs-lookup"><span data-stu-id="a25ce-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="a25ce-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy do animowania obiektu wzdłuż ścieżki, która jest definiowana za pomocą <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a25ce-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25ce-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a25ce-104">Example</span></span>  
 <span data-ttu-id="a25ce-105">Poniższy przykład animuje obiektu wzdłuż ścieżki, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a25ce-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="a25ce-106">Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.</span><span class="sxs-lookup"><span data-stu-id="a25ce-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="a25ce-107">Określa ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a25ce-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="a25ce-108">Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go do animowania <xref:System.Windows.Media.Matrix> właściwość <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="a25ce-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="a25ce-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Przyjmuje <xref:System.Windows.Media.PathGeometry> i używa go do wygenerowania <xref:System.Windows.Media.Matrix> wartości.</span><span class="sxs-lookup"><span data-stu-id="a25ce-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="a25ce-110">Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="a25ce-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="a25ce-111">Aby uzyskać więcej informacji o ścieżkach geometryczne, zobacz [omówienie geometrii](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a25ce-111">For more information about geometric paths, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25ce-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a25ce-112">See Also</span></span>  
 [<span data-ttu-id="a25ce-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="a25ce-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a25ce-114">Ścieżka animacji próbki</span><span class="sxs-lookup"><span data-stu-id="a25ce-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="a25ce-115">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="a25ce-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
