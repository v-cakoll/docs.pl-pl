---
title: Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344652"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="9ac6d-102">Jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="9ac6d-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="9ac6d-103">W tym przykładzie pokazano, jak animować zmiany rozmiaru przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="9ac6d-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ac6d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ac6d-104">Example</span></span>  
 <span data-ttu-id="9ac6d-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.ArcSegment.Size%2A> klasy do <xref:System.Windows.Media.ArcSegment>animowania właściwości programu .</span><span class="sxs-lookup"><span data-stu-id="9ac6d-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="9ac6d-106">Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9ac6d-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="9ac6d-107">W pierwszej połowie drugiej części animacji, używa <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> wystąpienia klasy, aby stopniowo zwiększać rozmiar łuku. Liniowe klatki <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.</span><span class="sxs-lookup"><span data-stu-id="9ac6d-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="9ac6d-108">Pod koniec następnej połowy drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> klasy, aby nagle zwiększyć rozmiar łuku. Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami, oznacza to, że zmiany rozmiaru występują nagle i nie są subtelne.</span><span class="sxs-lookup"><span data-stu-id="9ac6d-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="9ac6d-109">W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> wystąpienia klasy, aby zwiększyć rozmiar łuku. Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ac6d-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="9ac6d-110">W tym przykładzie rozmiar łuku zwiększa się powoli na początku, a następnie zwiększa wykładniczo pod koniec segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="9ac6d-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="9ac6d-111">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="9ac6d-111">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac6d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ac6d-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="9ac6d-113">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="9ac6d-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9ac6d-114">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9ac6d-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
