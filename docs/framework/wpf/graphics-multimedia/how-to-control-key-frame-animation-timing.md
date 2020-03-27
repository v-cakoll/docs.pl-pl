---
title: Jak kontrolować chronometraż animacji kluczowych klatek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344734"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="ea846-102">Jak kontrolować chronometraż animacji kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="ea846-102">How to: Control Key-Frame Animation Timing</span></span>

<span data-ttu-id="ea846-103">W tym przykładzie pokazano, jak kontrolować czas klatek kluczowych w animacji klatki kluczowej.</span><span class="sxs-lookup"><span data-stu-id="ea846-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="ea846-104">Podobnie jak inne animacje, animacje <xref:System.Windows.Media.Animation.Timeline.Duration%2A> klatek kluczowych mają właściwość.</span><span class="sxs-lookup"><span data-stu-id="ea846-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="ea846-105">Oprócz określenia czasu trwania animacji, należy określić, jaka część tego czasu trwania jest przydzielana do każdej z jej klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="ea846-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="ea846-106">Aby przymielić czas, należy określić <xref:System.Windows.Media.Animation.KeyTime> dla każdej klatki kluczowej w animacji.</span><span class="sxs-lookup"><span data-stu-id="ea846-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>

<span data-ttu-id="ea846-107">Dla <xref:System.Windows.Media.Animation.KeyTime> każdej klatki kluczowej określa się, kiedy kończy się klatka kluczowa (nie określa czasu odtwarzania klatki kluczowej).</span><span class="sxs-lookup"><span data-stu-id="ea846-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="ea846-108">Można określić <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> wartość, jako wartość procentową lub jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> wartość specjalną lub specjalną. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A></span><span class="sxs-lookup"><span data-stu-id="ea846-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>

## <a name="example"></a><span data-ttu-id="ea846-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea846-109">Example</span></span>

<span data-ttu-id="ea846-110">W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania prostokąta na ekranie.</span><span class="sxs-lookup"><span data-stu-id="ea846-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="ea846-111">Czasy kluczowe ramki są <xref:System.TimeSpan> ustawiane z wartościami.</span><span class="sxs-lookup"><span data-stu-id="ea846-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

<span data-ttu-id="ea846-112">Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.</span><span class="sxs-lookup"><span data-stu-id="ea846-112">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ea846-113">![Wartości kluczy są osiągane po 3, 4 i 10 sekundach](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="ea846-113">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>

<span data-ttu-id="ea846-114">W następnym przykładzie pokazano animację, która jest identyczna, z tą różnicą, że czasy klucza klatek kluczowych są ustawiane z wartościami procentowymi.</span><span class="sxs-lookup"><span data-stu-id="ea846-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

<span data-ttu-id="ea846-115">Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.</span><span class="sxs-lookup"><span data-stu-id="ea846-115">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ea846-116">![Wartości kluczy są osiągane po 3, 4 i 10 sekundach](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="ea846-116">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>

<span data-ttu-id="ea846-117">W następnym przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> kluczowych wartości czasu.</span><span class="sxs-lookup"><span data-stu-id="ea846-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

<span data-ttu-id="ea846-118">Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.</span><span class="sxs-lookup"><span data-stu-id="ea846-118">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ea846-119">![Wartości kluczy są osiągane na poziomie 3,3,6,6 i 9,9 sekundy](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="ea846-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>

<span data-ttu-id="ea846-120">W przykładzie <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> końcowym użyto kluczowych wartości czasu.</span><span class="sxs-lookup"><span data-stu-id="ea846-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

<span data-ttu-id="ea846-121">Na poniższej ilustracji pokazano, kiedy zostanie osiągnięta wartość każdej klatki kluczowej.</span><span class="sxs-lookup"><span data-stu-id="ea846-121">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ea846-122">![Wartości kluczy są osiągane w 0, 5 i 10 sekund](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="ea846-122">![Key values are reached at 0, 5, and 10 seconds](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>

<span data-ttu-id="ea846-123">Dla uproszczenia wersje kodu w tym przykładzie używają animacji lokalnych, a nie scenoprzyokiłów, ponieważ tylko pojedyncza animacja jest stosowana do jednej właściwości, ale przykłady mogą być modyfikowane w celu użycia scenodzielek zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ea846-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="ea846-124">Aby zapoznać się z przykładem przedstawiającym sposób deklarowania serii ujęć w kodzie, zobacz [Animowanie właściwości przy użyciu scenorysu](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="ea846-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>

<span data-ttu-id="ea846-125">Aby uzyskać pełną próbkę, zobacz [Przykład animacji klatki kluczowej](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="ea846-125">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span> <span data-ttu-id="ea846-126">Aby uzyskać więcej informacji na temat animacji klatek kluczowych, zobacz [Omówienie animacji klatek kluczowych](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ea846-126">For more information about key frame animations, see the [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea846-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea846-127">See also</span></span>

- [<span data-ttu-id="ea846-128">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="ea846-128">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ea846-129">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="ea846-129">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ea846-130">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="ea846-130">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
