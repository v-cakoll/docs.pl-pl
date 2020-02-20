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
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452912"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="2845c-102">Jak animować obiekt na ścieżce (animacja Matrix)</span><span class="sxs-lookup"><span data-stu-id="2845c-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="2845c-103">Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do animowania obiektu w ścieżce zdefiniowanej przez <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="2845c-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2845c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2845c-104">Example</span></span>  
 <span data-ttu-id="2845c-105">Poniższy przykład umożliwia animowanie obiektu na ścieżce, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2845c-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="2845c-106">Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.</span><span class="sxs-lookup"><span data-stu-id="2845c-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="2845c-107">Definiuje ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="2845c-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="2845c-108">Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go do animowania właściwości <xref:System.Windows.Media.Matrix> <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="2845c-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="2845c-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pobiera <xref:System.Windows.Media.PathGeometry> i używa jej do generowania wartości <xref:System.Windows.Media.Matrix>.</span><span class="sxs-lookup"><span data-stu-id="2845c-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="2845c-110">Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="2845c-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="2845c-111">Aby uzyskać więcej informacji na temat ścieżek geometrycznych, zobacz [Omówienie geometrii](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2845c-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2845c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2845c-112">See also</span></span>

- [<span data-ttu-id="2845c-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="2845c-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2845c-114">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="2845c-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="2845c-115">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="2845c-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
