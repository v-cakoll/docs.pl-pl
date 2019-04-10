---
title: 'Instrukcje: Animowanie obiektu na ścieżce (animacja matrycy akumulacją przesunięcia)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 3e7b892e2a2215d26512850477844d71bce7fe09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207373"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="486d0-102">Instrukcje: Animowanie obiektu na ścieżce (animacja matrycy akumulacją przesunięcia)</span><span class="sxs-lookup"><span data-stu-id="486d0-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="486d0-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy animowanie obiektu na ścieżce i animacji są gromadzone przesunięcie wartości jak powtarza się.</span><span class="sxs-lookup"><span data-stu-id="486d0-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="486d0-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="486d0-104">Example</span></span>  
 <span data-ttu-id="486d0-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> stosowane do przycisku.</span><span class="sxs-lookup"><span data-stu-id="486d0-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="486d0-106">W rezultacie przycisku przenosi wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="486d0-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="486d0-107">Ponadto w przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości `true`, co powoduje, że przesunięcie animowany macierzy kumulowania jako animacji powtarza się.</span><span class="sxs-lookup"><span data-stu-id="486d0-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="486d0-108">Ponieważ w wyniku Przesunięcie przycisku porusza się dalej na ekran, gdy jest powtarzany animacji, zamiast zresetowanie do ustawień pozycja początkowa.</span><span class="sxs-lookup"><span data-stu-id="486d0-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="486d0-109">Należy zauważyć, że, mimo że <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości powoduje przesunięcia wartości są gromadzone przez powtórzeń, nie powoduje obrotu wartości do.</span><span class="sxs-lookup"><span data-stu-id="486d0-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="486d0-110">Aby obrotu wartości są gromadzone, ustaw animacji <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="486d0-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="486d0-111">Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="486d0-111">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="486d0-112">Aby uzyskać przykład pokazujący sposób animować <xref:System.Windows.Media.Matrix> wartość na ścieżce bez akumulacją przesunięcia, zobacz [animowanie obiektu na ścieżce (animacja Matrix)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="486d0-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="486d0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="486d0-113">See also</span></span>

- [<span data-ttu-id="486d0-114">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="486d0-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="486d0-115">Animacja ścieżki Tematy Pomocy</span><span class="sxs-lookup"><span data-stu-id="486d0-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
