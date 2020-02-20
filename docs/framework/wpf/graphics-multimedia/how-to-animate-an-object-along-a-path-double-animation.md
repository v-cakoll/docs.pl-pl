---
title: Jak animować obiekt na ścieżce (animacja double)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452860"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="5408d-102">Jak animować obiekt na ścieżce (animacja double)</span><span class="sxs-lookup"><span data-stu-id="5408d-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="5408d-103">Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> do przenoszenia obiektu w ścieżce zdefiniowanej przez <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="5408d-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5408d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5408d-104">Example</span></span>  
 <span data-ttu-id="5408d-105">Poniższy przykład używa dwóch <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> obiektów do przenoszenia prostokąta wzdłuż ścieżki geometrycznej:</span><span class="sxs-lookup"><span data-stu-id="5408d-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
- <span data-ttu-id="5408d-106">Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> Animuj <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> zastosowany do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="5408d-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="5408d-107">Sprawia, że prostokąt przemieszcza się w poziomie wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="5408d-107">It makes the rectangle move horizontally along the path.</span></span>  
  
- <span data-ttu-id="5408d-108">Druga <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> Animuj <xref:System.Windows.Media.TranslateTransform.Y%2A> <xref:System.Windows.Media.TranslateTransform> zastosowana do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="5408d-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="5408d-109">Sprawia, że prostokąt przemieszcza się w pionie wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="5408d-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="5408d-110">Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="5408d-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="5408d-111">Innym sposobem przenoszenia obiektu przy użyciu ścieżki geometrycznej jest użycie obiektu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>.</span><span class="sxs-lookup"><span data-stu-id="5408d-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="5408d-112">Aby zapoznać się z przykładem, zobacz [animowanie obiektu na ścieżce (animacja matrycy)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="5408d-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5408d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5408d-113">See also</span></span>

- [<span data-ttu-id="5408d-114">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="5408d-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="5408d-115">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="5408d-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
