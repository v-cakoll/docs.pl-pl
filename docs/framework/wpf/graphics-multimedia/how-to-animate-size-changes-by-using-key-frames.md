---
title: "Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30ee897efd01712bf4313da87e1050c5a16e4523
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="eb6d8-102">Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="eb6d8-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="eb6d8-103">W tym przykładzie przedstawiono sposób animowanie zmian rozmiaru przy użyciu klucza ramki.</span><span class="sxs-lookup"><span data-stu-id="eb6d8-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb6d8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb6d8-104">Example</span></span>  
 <span data-ttu-id="eb6d8-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.ArcSegment.Size%2A> właściwość <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="eb6d8-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="eb6d8-106">Ta animacja używa trzech klatek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="eb6d8-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="eb6d8-107">Podczas pierwszego pół sekundy animacji używa wystąpienia <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> klasy stopniowo zwiększać rozmiar łuku. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> utworzyć liniowej przejścia między wartościami.</span><span class="sxs-lookup"><span data-stu-id="eb6d8-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="eb6d8-108">Po zakończeniu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> klasy nagle zwiększyć rozmiar łuk. Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> utworzyć nagłym przechodzi między wartościami, oznacza to, zmiany rozmiaru wystąpić nagle i nie są niewielkie.</span><span class="sxs-lookup"><span data-stu-id="eb6d8-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3.  <span data-ttu-id="eb6d8-109">W ostatnim dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> klasę, aby zwiększyć rozmiar łuk. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb6d8-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="eb6d8-110">W tym przykładzie rozmiar łuk powoli zwiększa się na początku i znacznie zwiększa, do końca segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="eb6d8-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="eb6d8-111">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="eb6d8-111">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6d8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb6d8-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [<span data-ttu-id="eb6d8-113">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="eb6d8-113">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="eb6d8-114">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="eb6d8-114">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
