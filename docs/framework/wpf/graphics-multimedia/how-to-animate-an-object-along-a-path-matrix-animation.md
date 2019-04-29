---
title: 'Instrukcje: Animowanie obiektu na ścieżce (animacja Matrix)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: ab15126680b7d8c6936246a7dae2f67c7541233b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651444"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="fccd2-102">Instrukcje: Animowanie obiektu na ścieżce (animacja Matrix)</span><span class="sxs-lookup"><span data-stu-id="fccd2-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="fccd2-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy animowanie obiektu na ścieżce, który jest definiowany przez <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="fccd2-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fccd2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fccd2-104">Example</span></span>  
 <span data-ttu-id="fccd2-105">Poniższy przykład animuje obiekt na ścieżce, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fccd2-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="fccd2-106">Stosuje <xref:System.Windows.Media.MatrixTransform> do obiektu, aby go przenieść.</span><span class="sxs-lookup"><span data-stu-id="fccd2-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="fccd2-107">Określa ścieżkę przy użyciu <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="fccd2-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="fccd2-108">Tworzy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i używa go, animować <xref:System.Windows.Media.Matrix> właściwość <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="fccd2-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="fccd2-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Przyjmuje <xref:System.Windows.Media.PathGeometry> i używa ich do generowania <xref:System.Windows.Media.Matrix> wartości.</span><span class="sxs-lookup"><span data-stu-id="fccd2-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="fccd2-110">Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="fccd2-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="fccd2-111">Aby uzyskać więcej informacji na temat ścieżek geometrycznych zobacz [Przegląd Geometria](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fccd2-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccd2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fccd2-112">See also</span></span>

- [<span data-ttu-id="fccd2-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="fccd2-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="fccd2-114">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="fccd2-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="fccd2-115">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="fccd2-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
