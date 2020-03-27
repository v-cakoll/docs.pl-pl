---
title: Jak animować punkt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344881"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="bb484-102">Jak animować punkt z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="bb484-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="bb484-103">W tym przykładzie <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> pokazano, jak <xref:System.Windows.Point>używać klasy do animowania programu .</span><span class="sxs-lookup"><span data-stu-id="bb484-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb484-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb484-104">Example</span></span>  
 <span data-ttu-id="bb484-105">Poniższy przykład przenosi elipsę wzdłuż trójkątnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="bb484-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="bb484-106">W przykładzie <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> użyto klasy <xref:System.Windows.Media.EllipseGeometry.Center%2A> do animowania właściwości . <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="bb484-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="bb484-107">Ta animacja wykorzystuje trzy klatki kluczowe w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bb484-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="bb484-108">W pierwszej połowie drugiej, używa wystąpienia <xref:System.Windows.Media.Animation.LinearPointKeyFrame> klasy, aby przenieść elipsy wzdłuż ścieżki w stałym tempie od pozycji wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="bb484-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="bb484-109">Liniowe klatki <xref:System.Windows.Media.Animation.LinearPointKeyFrame> kluczowe, takie jak tworzenie płynnej interpolacji liniowej między wartościami.</span><span class="sxs-lookup"><span data-stu-id="bb484-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="bb484-110">Pod koniec następnej połowy sekundy, używa <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> wystąpienia klasy, aby nagle przenieść elipsy wzdłuż ścieżki do następnej pozycji.</span><span class="sxs-lookup"><span data-stu-id="bb484-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="bb484-111">Dyskretne klatki <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> kluczowe, takie jak tworzenie nagłych przeskoków między wartościami.</span><span class="sxs-lookup"><span data-stu-id="bb484-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="bb484-112">W ciągu ostatnich dwóch sekund używa <xref:System.Windows.Media.Animation.SplinePointKeyFrame> wystąpienia klasy, aby przenieść elipsę z powrotem do pozycji wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="bb484-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="bb484-113">Klatki kluczowe splajnu, takie jak <xref:System.Windows.Media.Animation.SplinePointKeyFrame> tworzenie <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> zmiennego przejścia między wartościami zgodnie z wartościami właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb484-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="bb484-114">W tym przykładzie animacja rozpoczyna się powoli i przyspiesza wykładniczo pod koniec segmentu czasu.</span><span class="sxs-lookup"><span data-stu-id="bb484-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="bb484-115">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="bb484-115">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="bb484-116">Aby uzyskać spójność z innymi przykładami animacji, wersje kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> używają obiektu do zastosowania pliku <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="bb484-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="bb484-117">Jednak podczas stosowania pojedynczej animacji w kodzie łatwiej <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jest użyć metody <xref:System.Windows.Media.Animation.Storyboard>zamiast używać .</span><span class="sxs-lookup"><span data-stu-id="bb484-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="bb484-118">Na przykład zobacz [Animowanie właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="bb484-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb484-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb484-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="bb484-120">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="bb484-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="bb484-121">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="bb484-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
