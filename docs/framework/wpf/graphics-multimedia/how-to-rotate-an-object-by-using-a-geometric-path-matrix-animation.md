---
title: Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187412"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="8c248-102">Jak obrócić obiekt z wykorzystaniem ścieżki geometrycznej (animacja Matrix)</span><span class="sxs-lookup"><span data-stu-id="8c248-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="8c248-103">W tym przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pokazano, <xref:System.Windows.Media.MatrixTransform> jak za pomocą a i a obracać <xref:System.Windows.Media.PathGeometry> (przestawiać) obiekt wzdłuż ścieżki geometrycznej zdefiniowanej przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="8c248-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c248-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c248-104">Example</span></span>  
 <span data-ttu-id="8c248-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> użyto <xref:System.Windows.Media.MatrixTransform.Matrix%2A> obiektu do <xref:System.Windows.Media.MatrixTransform>animowania właściwości programu .</span><span class="sxs-lookup"><span data-stu-id="8c248-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="8c248-106">Jest <xref:System.Windows.Media.MatrixTransform> stosowany do przycisku i powoduje, że porusza się po zakrzywionej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8c248-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="8c248-107">Ponieważ <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> właściwość jest `true`ustawiona na , prostokąt obraca się wzdłuż stycznej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8c248-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="8c248-108">Aby uzyskać pełną próbkę, zobacz [Przykład animacji ścieżki](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="8c248-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="8c248-109">Wersja kodu poprzedniego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.Media.EllipseGeometry>, mimo że zastosowano tylko jedną animację.</span><span class="sxs-lookup"><span data-stu-id="8c248-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="8c248-110">Łatwiejszym sposobem zastosowania pojedynczej animacji do właściwości w <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodzie jest użycie metody.</span><span class="sxs-lookup"><span data-stu-id="8c248-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="8c248-111">Na przykład zobacz [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="8c248-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c248-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c248-112">See also</span></span>

- [<span data-ttu-id="8c248-113">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="8c248-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="8c248-114">Animacja ścieżki — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8c248-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="8c248-115">Przykład animacji ścieżki</span><span class="sxs-lookup"><span data-stu-id="8c248-115">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
