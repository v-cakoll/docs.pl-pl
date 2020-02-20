---
title: Jak animować obiekt na ścieżce (animacja punktu)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452899"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="e2045-102">Jak animować obiekt na ścieżce (animacja punktu)</span><span class="sxs-lookup"><span data-stu-id="e2045-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="e2045-103">W tym przykładzie pokazano, jak za pomocą obiektu <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animować <xref:System.Windows.Point> wzdłuż ścieżki zakrzywionej.</span><span class="sxs-lookup"><span data-stu-id="e2045-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2045-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2045-104">Example</span></span>  
 <span data-ttu-id="e2045-105">Poniższy przykład przenosi <xref:System.Windows.Media.EllipseGeometry> wzdłuż ścieżki zdefiniowanej przez <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e2045-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e2045-106">Właściwość <xref:System.Windows.Media.EllipseGeometry.Center%2A> geometrii wielokropka, która przyjmuje wartość <xref:System.Windows.Point>, określa jej pozycję. Aby przenieść geometrię elipsy, należy animować jej Właściwość <xref:System.Windows.Media.EllipseGeometry.Center%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2045-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="e2045-107">W przykładzie używa się <xref:System.Windows.Media.Animation.PointAnimationUsingPath> do animowania właściwości <xref:System.Windows.Media.EllipseGeometry.Center%2A> obiektu <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e2045-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="e2045-108">Aby zapoznać się z kompletnym przykładem, zobacz [przykład animacji Path](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="e2045-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="e2045-109">Wersja kodu powyższego przykładu użyła <xref:System.Windows.Media.Animation.Storyboard>, aby animować <xref:System.Windows.Media.EllipseGeometry>, nawet jeśli zastosowano tylko jedną animację.</span><span class="sxs-lookup"><span data-stu-id="e2045-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="e2045-110"><xref:System.Windows.Media.Animation.Storyboard> jest często najprostszym sposobem zastosowania wielu animacji, ponieważ te animacje mogą być kontrolowane przez ten sam <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="e2045-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="e2045-111">Jednak łatwiejszym sposobem zastosowania pojedynczej animacji do właściwości przy użyciu kodu jest użycie metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2045-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="e2045-112">Aby zapoznać się z przykładem, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="e2045-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2045-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2045-113">See also</span></span>

- [<span data-ttu-id="e2045-114">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="e2045-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="e2045-115">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="e2045-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e2045-116">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e2045-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
