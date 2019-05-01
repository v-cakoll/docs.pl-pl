---
title: 'Instrukcje: Animowanie zmian rozmiaru przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0629b6600444bd172af451fd7e970bff894d8047
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789262"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="c1991-102">Instrukcje: Animowanie zmian rozmiaru przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="c1991-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="c1991-103">Ten przykład pokazuje, jak animować zmiany rozmiaru z wykorzystaniem klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="c1991-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1991-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1991-104">Example</span></span>  
 <span data-ttu-id="c1991-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.ArcSegment.Size%2A> właściwość <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="c1991-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="c1991-106">Ta animacja używa trzech ramek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c1991-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="c1991-107">Podczas pierwszego pół sekundy animacji używa wystąpienia <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> klasy, aby stopniowo zwiększać rozmiar łuku. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> utworzyć płynne przejście liniowy między wartościami.</span><span class="sxs-lookup"><span data-stu-id="c1991-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="c1991-108">Na końcu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> klasy nagle zwiększyć rozmiar łuku. Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, zmiany rozmiaru nagle występują i nie są subtelne.</span><span class="sxs-lookup"><span data-stu-id="c1991-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="c1991-109">Za pośrednictwem końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> klasy, aby zwiększyć rozmiar łuku. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c1991-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="c1991-110">W tym przykładzie rozmiar łuk powoli zwiększa się na początku i wykładniczo zwiększa, kierunku końca odcinka czasu.</span><span class="sxs-lookup"><span data-stu-id="c1991-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="c1991-111">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="c1991-111">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1991-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1991-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="c1991-113">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="c1991-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="c1991-114">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c1991-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
