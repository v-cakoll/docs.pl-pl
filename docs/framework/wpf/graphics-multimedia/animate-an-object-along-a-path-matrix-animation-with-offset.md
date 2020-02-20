---
title: Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453107"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="4110a-102">Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)</span><span class="sxs-lookup"><span data-stu-id="4110a-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="4110a-103">Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do animowania obiektu na ścieżce i czy animacja będzie zbierać wartości przesunięcia w miarę ich powtarzania.</span><span class="sxs-lookup"><span data-stu-id="4110a-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4110a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4110a-104">Example</span></span>  
 <span data-ttu-id="4110a-105">Poniższy przykład używa obiektu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>, aby animować Właściwość <xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform> zastosowana do przycisku.</span><span class="sxs-lookup"><span data-stu-id="4110a-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="4110a-106">W efekcie przycisk jest przesuwany wzdłuż ścieżki zakrzywionej.</span><span class="sxs-lookup"><span data-stu-id="4110a-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="4110a-107">Ponadto, przykład ustawia właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> na `true`, co powoduje, że przesunięcie animowanej macierzy będzie sumowane w miarę powtarzania animacji.</span><span class="sxs-lookup"><span data-stu-id="4110a-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="4110a-108">Ze względu na to, że przesunięcie zostanie wykonane, przycisk przesuwa się dalej na ekranie, gdy animacja powtarza się, a nie resetuje do pozycji początkowej.</span><span class="sxs-lookup"><span data-stu-id="4110a-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="4110a-109">Należy zauważyć, że mimo że właściwość <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> powoduje, że wartości przesunięcia są sumowane za pośrednictwem powtórzeń, nie powoduje sumowania wartości obrotu.</span><span class="sxs-lookup"><span data-stu-id="4110a-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="4110a-110">Aby narastać wartości rotacji, ustaw właściwości <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> animacji na `true`.</span><span class="sxs-lookup"><span data-stu-id="4110a-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="4110a-111">Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="4110a-111">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="4110a-112">Aby zapoznać się z przykładem pokazującym, jak animować wartość <xref:System.Windows.Media.Matrix> wzdłuż ścieżki bez kumulacji przesunięcia, zobacz [animowanie obiektu na ścieżce (animacja macierzy)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="4110a-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4110a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4110a-113">See also</span></span>

- [<span data-ttu-id="4110a-114">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="4110a-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4110a-115">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="4110a-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
