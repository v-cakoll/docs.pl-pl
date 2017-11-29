---
title: "Jak animować punkt z wykorzystaniem klatek kluczowych"
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
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f574f85a5840e8bbe2d6c026d57a4cc28bd8a797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="39cbe-102">Jak animować punkt z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="39cbe-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="39cbe-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="39cbe-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39cbe-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="39cbe-104">Example</span></span>  
 <span data-ttu-id="39cbe-105">Poniższy przykład przenosi elipsy trójkątny ścieżce.</span><span class="sxs-lookup"><span data-stu-id="39cbe-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="39cbe-106">W przykładzie użyto <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwość <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="39cbe-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="39cbe-107">Ta animacja używa trzech klatek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="39cbe-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="39cbe-108">Podczas pierwszego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.LinearPointKeyFrame> klasę, aby przenieść elipsy wzdłuż ścieżki stałą szybkością z punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="39cbe-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="39cbe-109">Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearPointKeyFrame> utworzyć smooth interpolacji liniowej między wartościami.</span><span class="sxs-lookup"><span data-stu-id="39cbe-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="39cbe-110">W końcu następnej pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> klasy nagle przejście elipsy wzdłuż ścieżki do pozycji dalej.</span><span class="sxs-lookup"><span data-stu-id="39cbe-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="39cbe-111">Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> tworzenie nagłym przeskoków między wartościami.</span><span class="sxs-lookup"><span data-stu-id="39cbe-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="39cbe-112">Podczas końcowego dwusekundowe używa wystąpienia <xref:System.Windows.Media.Animation.SplinePointKeyFrame> klasę, aby przenieść elipsy z powrotem do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="39cbe-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="39cbe-113">Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplinePointKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="39cbe-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="39cbe-114">W tym przykładzie animacji rozpoczyna się powoli i przyspiesza wykładniczo do końca segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="39cbe-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="39cbe-115">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="39cbe-115">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="39cbe-116">Spójności z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt do zastosowania <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="39cbe-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="39cbe-117">Jednak podczas stosowania pojedynczego animacji w kodzie, łatwiej jest użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="39cbe-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="39cbe-118">Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="39cbe-118">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cbe-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39cbe-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [<span data-ttu-id="39cbe-120">Omówienie klucza poklatkowych</span><span class="sxs-lookup"><span data-stu-id="39cbe-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="39cbe-121">Klucz ramki — tematy porad</span><span class="sxs-lookup"><span data-stu-id="39cbe-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
