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
ms.openlocfilehash: d6dc79cd7a15aef2a4168fffb293c5e1f33cde08
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870357"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="88b3a-102">Jak animować obiekt na ścieżce (animacja punktu)</span><span class="sxs-lookup"><span data-stu-id="88b3a-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="88b3a-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.PointAnimationUsingPath> obiektu animować <xref:System.Windows.Point> wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="88b3a-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b3a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="88b3a-104">Example</span></span>  
 <span data-ttu-id="88b3a-105">W poniższym przykładzie <xref:System.Windows.Media.EllipseGeometry> wzdłuż ścieżki definicją <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="88b3a-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="88b3a-106">Geometria elipsy <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwość, która przyjmuje <xref:System.Windows.Point> wartość, określa jej położenie; geometrii elipsy, animowanie możesz przenieść jego <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="88b3a-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="88b3a-107">W przykładzie użyto <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animować <xref:System.Windows.Media.EllipseGeometry> obiektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="88b3a-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="88b3a-108">Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="88b3a-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="88b3a-109">Wersja kodu powyższego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> animować <xref:System.Windows.Media.EllipseGeometry>, mimo że zastosowano tylko jednej animacji.</span><span class="sxs-lookup"><span data-stu-id="88b3a-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="88b3a-110">A <xref:System.Windows.Media.Animation.Storyboard> często jest najprostszym sposobem na stosowanie wielu animacji, ponieważ te animacje mogą być kontrolowane przez ten sam <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="88b3a-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="88b3a-111">Jednak ułatwiających stosowanie jednej animacji z właściwością przy użyciu kodu jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="88b3a-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="88b3a-112">Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="88b3a-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b3a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88b3a-113">See Also</span></span>  
 [<span data-ttu-id="88b3a-114">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="88b3a-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="88b3a-115">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="88b3a-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="88b3a-116">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="88b3a-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
