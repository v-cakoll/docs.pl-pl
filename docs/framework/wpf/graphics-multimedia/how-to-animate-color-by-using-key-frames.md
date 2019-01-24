---
title: 'Instrukcje: Animuj kolor z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8d7dbe70f25b4712d1384a751a02053fb7f287ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645096"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="09193-102">Instrukcje: Animuj kolor z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="09193-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="09193-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="09193-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09193-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="09193-104">Example</span></span>  
 <span data-ttu-id="09193-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="09193-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="09193-106">Ta animacja używa trzech ramek kluczowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="09193-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="09193-107">Podczas pierwszych dwóch sekund, używa wystąpienia <xref:System.Windows.Media.Animation.LinearColorKeyFrame> klasy, aby stopniowo kolor z zielonego do czerwonego.</span><span class="sxs-lookup"><span data-stu-id="09193-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="09193-108">Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearColorKeyFrame> utworzyć płynne przejście liniowy między wartościami.</span><span class="sxs-lookup"><span data-stu-id="09193-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="09193-109">Podczas koniec następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> klasy, aby szybko zmienić kolor czerwony na żółto.</span><span class="sxs-lookup"><span data-stu-id="09193-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="09193-110">Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> tworzenie nagłe zmiany między wartościami, to znaczy, zmiana koloru w tej części animacji odbywa się szybko, a nie subtelne.</span><span class="sxs-lookup"><span data-stu-id="09193-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="09193-111">Podczas końcowego dwie sekundy, używa wystąpienia <xref:System.Windows.Media.Animation.SplineColorKeyFrame> klasy, aby zmienić kolor ponownie — tym razem z żółtym kopii na zielony.</span><span class="sxs-lookup"><span data-stu-id="09193-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="09193-112">Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineColorKeyFrame> Tworzenie zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="09193-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="09193-113">W tym przykładzie zmiana koloru rozpocznie się powoli i przyspiesza wykładniczo w kierunku końca odcinka czasu.</span><span class="sxs-lookup"><span data-stu-id="09193-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="09193-114">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="09193-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09193-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09193-115">See also</span></span>
- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="09193-116">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="09193-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="09193-117">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="09193-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
