---
title: 'Instrukcje: Obróć obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: de61e2469e22d077da4b082e18340a837fac2880
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565894"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="95213-102">Instrukcje: Obróć obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)</span><span class="sxs-lookup"><span data-stu-id="95213-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="95213-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> i <xref:System.Windows.Media.MatrixTransform> wymienić (Tabela przestawna) wzdłuż ścieżki geometrycznej zdefiniowane przez obiekt <xref:System.Windows.Media.PathGeometry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="95213-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95213-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="95213-104">Example</span></span>  
 <span data-ttu-id="95213-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> obiektu animować <xref:System.Windows.Media.MatrixTransform.Matrix%2A> właściwość <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="95213-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="95213-106"><xref:System.Windows.Media.MatrixTransform> Jest stosowany do przycisku i powoduje, że przesunąć wzdłuż ścieżki.</span><span class="sxs-lookup"><span data-stu-id="95213-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="95213-107">Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest ustawiona na `true`, prostokąt obraca się wzdłuż tangens ścieżki.</span><span class="sxs-lookup"><span data-stu-id="95213-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="95213-108">Aby uzyskać pełny przykład, zobacz [przykład animacji ścieżki](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="95213-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="95213-109">Wersja kodu powyższego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> animować <xref:System.Windows.Media.EllipseGeometry>, mimo że zastosowano tylko jednej animacji.</span><span class="sxs-lookup"><span data-stu-id="95213-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="95213-110">Łatwiejszy sposób zastosowania jednej animacji do właściwości w kodzie jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="95213-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="95213-111">Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="95213-111">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95213-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95213-112">See also</span></span>
- [<span data-ttu-id="95213-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="95213-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="95213-114">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="95213-114">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
- [<span data-ttu-id="95213-115">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="95213-115">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
