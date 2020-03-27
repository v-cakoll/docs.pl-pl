---
title: Jak animować grubość obramowania z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344689"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="a8bd6-102">Jak animować grubość obramowania z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="a8bd6-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="a8bd6-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość programu <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8bd6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8bd6-104">Example</span></span>  
 <span data-ttu-id="a8bd6-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> użyto <xref:System.Windows.Controls.Control.BorderThickness%2A> klasy do <xref:System.Windows.Controls.Border>animowania właściwości . .</span><span class="sxs-lookup"><span data-stu-id="a8bd6-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="a8bd6-106">Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a8bd6-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="a8bd6-107">W pierwszej połowie drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> klasy, aby stopniowo zwiększać grubość granicy.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="a8bd6-108">W przykładzie <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> użyto do utworzenia płynnego wzrostu liniowego między wartościami.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="a8bd6-109">Pod koniec następnej połowy drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> klasy, aby nagle zwiększyć grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="a8bd6-110">Dyskretne klatki kluczowe, takie <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> jak te pochodzące z tworzenia nagłych przeskoków między wartościami, to znaczy, że ruch animacji jest szarpany.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="a8bd6-111">W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> wystąpienia klasy, aby zmniejszyć grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="a8bd6-112">Klatki kluczowe splajnu, takie jak te pochodzące <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> z <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> tworzenia zmiennego przejścia między wartościami zgodnie z wartościami właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="a8bd6-113">W tej klatce kluczowej animacja rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="a8bd6-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="a8bd6-114">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="a8bd6-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8bd6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8bd6-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="a8bd6-116">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="a8bd6-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="a8bd6-117">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="a8bd6-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="a8bd6-118">Animowanie wartości BorderThickness</span><span class="sxs-lookup"><span data-stu-id="a8bd6-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
