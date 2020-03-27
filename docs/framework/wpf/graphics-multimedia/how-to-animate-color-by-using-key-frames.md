---
title: Jak animować kolor z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344747"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="88736-102">Jak animować kolor z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="88736-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="88736-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> a <xref:System.Windows.Media.SolidColorBrush> za pomocą klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="88736-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88736-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="88736-104">Example</span></span>  
 <span data-ttu-id="88736-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> użyto <xref:System.Windows.Media.SolidColorBrush.Color%2A> klasy do <xref:System.Windows.Media.SolidColorBrush>animowania właściwości . .</span><span class="sxs-lookup"><span data-stu-id="88736-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="88736-106">Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="88736-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="88736-107">W ciągu pierwszych dwóch sekund używa <xref:System.Windows.Media.Animation.LinearColorKeyFrame> wystąpienia klasy, aby stopniowo zmieniać kolor z zielonego na czerwony.</span><span class="sxs-lookup"><span data-stu-id="88736-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="88736-108">Liniowe klatki <xref:System.Windows.Media.Animation.LinearColorKeyFrame> kluczowe, takie jak tworzenie płynnego liniowego przejścia między wartościami.</span><span class="sxs-lookup"><span data-stu-id="88736-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="88736-109">Pod koniec następnej połowy drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> klasy, aby szybko zmienić kolor z czerwonego na żółty.</span><span class="sxs-lookup"><span data-stu-id="88736-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="88736-110">Dyskretne klatki <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> kluczowe, takie jak tworzenie nagłych zmian między wartościami, to znaczy, zmiana koloru w tej części animacji występuje szybko i nie jest subtelna.</span><span class="sxs-lookup"><span data-stu-id="88736-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="88736-111">W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplineColorKeyFrame> wystąpienia klasy, aby ponownie zmienić kolor — tym razem z żółtego z powrotem na zielony.</span><span class="sxs-lookup"><span data-stu-id="88736-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="88736-112">Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplineColorKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości.</span><span class="sxs-lookup"><span data-stu-id="88736-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="88736-113">W tym przykładzie zmiana koloru rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="88736-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="88736-114">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="88736-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88736-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88736-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="88736-116">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="88736-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="88736-117">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="88736-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
