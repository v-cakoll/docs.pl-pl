---
title: 'Instrukcje: Animuj obiekt na ścieżce (animacja double)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: a57b21e3f05f90e756c46c167bb419b5bc9068f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600417"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="c0211-102">Instrukcje: Animuj obiekt na ścieżce (animacja double)</span><span class="sxs-lookup"><span data-stu-id="c0211-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="c0211-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> klasy, aby przenieść obiekt na ścieżce definicją <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="c0211-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0211-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0211-104">Example</span></span>  
 <span data-ttu-id="c0211-105">W poniższym przykładzie użyto dwóch <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> przenieść prostokąt wzdłuż ścieżki geometrycznej obiekty:</span><span class="sxs-lookup"><span data-stu-id="c0211-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="c0211-106">Pierwszy <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.X%2A> z <xref:System.Windows.Media.TranslateTransform> stosowane do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="c0211-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="c0211-107">To sprawia, że prostokąt przenoszony w poziomie wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c0211-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="c0211-108">Drugi <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animuje <xref:System.Windows.Media.TranslateTransform.Y%2A> z <xref:System.Windows.Media.TranslateTransform> stosowane do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="c0211-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="c0211-109">To sprawia, że prostokąt przesunąć pionowo wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c0211-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="c0211-110">Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="c0211-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="c0211-111">Innym sposobem, aby przenieść obiekt przy użyciu ścieżki geometrycznej jest użycie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c0211-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="c0211-112">Aby uzyskać przykład, zobacz [animowanie obiektu na ścieżce (animacja Matrix)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="c0211-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0211-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0211-113">See also</span></span>
- [<span data-ttu-id="c0211-114">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="c0211-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="c0211-115">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c0211-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
