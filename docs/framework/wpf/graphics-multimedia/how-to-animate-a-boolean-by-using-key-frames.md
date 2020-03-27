---
title: Jak animować boolean z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 35704996dcf21fe463169dc13572941bcd8fbad1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344939"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="6d6fb-102">Jak animować boolean z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="6d6fb-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="6d6fb-103">W tym przykładzie pokazano, jak animować wartość właściwości logicznej <xref:System.Windows.Controls.Button> formantu przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="6d6fb-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d6fb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d6fb-104">Example</span></span>  
 <span data-ttu-id="6d6fb-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> użyto <xref:System.Windows.UIElement.IsEnabled%2A> klasy do <xref:System.Windows.Controls.Button> animowania właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="6d6fb-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="6d6fb-106">Wszystkie klatki kluczowe w tym przykładzie <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> użyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="6d6fb-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="6d6fb-107">Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami, to znaczy, że ruch animacji jest szarpany.</span><span class="sxs-lookup"><span data-stu-id="6d6fb-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="6d6fb-108">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="6d6fb-108">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6fb-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d6fb-109">See also</span></span>

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="6d6fb-110">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="6d6fb-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="6d6fb-111">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6d6fb-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
