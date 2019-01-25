---
title: 'Instrukcje: Animuj grubość obramowania z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: d30e414dd83e596da6415cc455c599820a22f3e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689958"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="1a88d-102">Instrukcje: Animuj grubość obramowania z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="1a88d-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="1a88d-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="1a88d-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a88d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a88d-104">Example</span></span>  
 <span data-ttu-id="1a88d-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="1a88d-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="1a88d-106">Ta animacja używa trzech ramek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1a88d-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="1a88d-107">Podczas pierwszego pół sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> klasy, aby stopniowo zwiększać grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="1a88d-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="1a88d-108">W przykładzie użyto <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> utworzyć smooth liniowy wzrost między wartościami.</span><span class="sxs-lookup"><span data-stu-id="1a88d-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2.  <span data-ttu-id="1a88d-109">Na końcu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> klasy nagłe zwiększenie grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="1a88d-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="1a88d-110">Dyskretnych klatek kluczowych, takich jak te pochodzące z <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, jerky przepływu animacji.</span><span class="sxs-lookup"><span data-stu-id="1a88d-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3.  <span data-ttu-id="1a88d-111">Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> klasy, aby zmniejszyć grubość obramowania.</span><span class="sxs-lookup"><span data-stu-id="1a88d-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="1a88d-112">Ramek kluczowych krzywej składanej, takich jak te pochodzące z <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a88d-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="1a88d-113">W tym klatek kluczowych animacji wolno rozpoczyna się i przyspiesza wykładniczo w kierunku końca odcinka czasu.</span><span class="sxs-lookup"><span data-stu-id="1a88d-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="1a88d-114">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="1a88d-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a88d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a88d-115">See also</span></span>
- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="1a88d-116">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="1a88d-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="1a88d-117">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1a88d-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="1a88d-118">Animowanie wartości BorderThickness</span><span class="sxs-lookup"><span data-stu-id="1a88d-118">Animate a BorderThickness Value</span></span>](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
