---
title: 'Instrukcje: Animowanie grubości obramowania przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 101fd077bf125faadbd9a0186c2282e4b20ee78f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699035"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="151d7-102">Instrukcje: Animowanie grubości obramowania przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="151d7-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="151d7-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="151d7-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="151d7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="151d7-104">Example</span></span>  
 <span data-ttu-id="151d7-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="151d7-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="151d7-106">Ta animacja używa trzech ramek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="151d7-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="151d7-107">Podczas pierwszego pół sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> klasy, aby stopniowo zwiększać grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="151d7-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="151d7-108">W przykładzie użyto <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> utworzyć smooth liniowy wzrost między wartościami.</span><span class="sxs-lookup"><span data-stu-id="151d7-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="151d7-109">Na końcu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> klasy nagłe zwiększenie grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="151d7-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="151d7-110">Dyskretnych klatek kluczowych, takich jak te pochodzące z <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, jerky przepływu animacji.</span><span class="sxs-lookup"><span data-stu-id="151d7-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="151d7-111">Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> klasy, aby zmniejszyć grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="151d7-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="151d7-112">Ramek kluczowych krzywej składanej, takich jak te pochodzące z <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="151d7-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="151d7-113">W tym klatek kluczowych animacji wolno rozpoczyna się i przyspiesza wykładniczo w kierunku końca odcinka czasu.</span><span class="sxs-lookup"><span data-stu-id="151d7-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="151d7-114">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="151d7-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151d7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="151d7-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="151d7-116">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="151d7-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="151d7-117">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="151d7-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="151d7-118">Animowanie wartości BorderThickness</span><span class="sxs-lookup"><span data-stu-id="151d7-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
