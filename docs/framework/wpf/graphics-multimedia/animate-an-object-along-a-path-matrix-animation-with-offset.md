---
title: "Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a9fd282d3ca4603eadd0ed10436944f7e9ab593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="a2644-102">Jak animować obiekt na ścieżce (animacja matrycy akumulacją przesunięcia)</span><span class="sxs-lookup"><span data-stu-id="a2644-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="a2644-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> klasy do animowania obiektu wzdłuż ścieżki i animacji gromadzone jego przesunięcie wartości jak powtarza się.</span><span class="sxs-lookup"><span data-stu-id="a2644-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2644-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2644-104">Example</span></span>  
 <span data-ttu-id="a2644-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu do animowania <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform> stosowane do przycisku.</span><span class="sxs-lookup"><span data-stu-id="a2644-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="a2644-106">W związku z tym przycisku przenosi wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a2644-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="a2644-107">Ponadto w przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości `true`, co powoduje, że przesunięcie animowany macierzy gromadzone jako powtarza animacji.</span><span class="sxs-lookup"><span data-stu-id="a2644-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="a2644-108">Ponieważ w wyniku przesunięcie, przycisk przechodzi dalej wzdłuż ekranu, gdy animacji jest powtarzany, zamiast zresetowanie do pozycji początkowej.</span><span class="sxs-lookup"><span data-stu-id="a2644-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="a2644-109">Należy zauważyć, że chociaż <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> właściwości powoduje przesunięcia wartości gromadzone przez powtórzeń, nie powoduje wartości obrotu kumulują się.</span><span class="sxs-lookup"><span data-stu-id="a2644-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="a2644-110">Aby wartości obrotu gromadzone, ustaw animację <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> i <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="a2644-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="a2644-111">Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="a2644-111">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="a2644-112">Na przykład przedstawiający sposób animować <xref:System.Windows.Media.Matrix> wartość wzdłuż ścieżki bez przesunięcia akumulacji, zobacz [Animowanie obiektów wzdłuż ścieżki (macierzy Animacja)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="a2644-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2644-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2644-113">See Also</span></span>  
 [<span data-ttu-id="a2644-114">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="a2644-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a2644-115">Ścieżka animacji — tematy porad</span><span class="sxs-lookup"><span data-stu-id="a2644-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
