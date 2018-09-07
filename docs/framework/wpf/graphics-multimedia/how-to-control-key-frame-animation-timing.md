---
title: Jak kontrolować chronometraż animacji kluczowych klatek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: d65bf6f7643adf1d98d468853ae8017a4a6554ac
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086196"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="3f298-102">Jak kontrolować chronometraż animacji kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="3f298-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="3f298-103">W tym przykładzie pokazano, jak kontrolować chronometraż klatek kluczowych w animacji kluczowych klatek.</span><span class="sxs-lookup"><span data-stu-id="3f298-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="3f298-104">Podobnie jak inne animacji mają Animacja kluczowych klatek <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3f298-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="3f298-105">Oprócz określenia czasu trwania animacji, należy określić, jaka część za ten czas jest przydzielony do każdego z jego użyciem klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="3f298-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="3f298-106">Aby przydzielić czas, należy określić <xref:System.Windows.Media.Animation.KeyTime> dla każdej ramki kluczowe animacji.</span><span class="sxs-lookup"><span data-stu-id="3f298-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="3f298-107"><xref:System.Windows.Media.Animation.KeyTime> Dla każdej ramki kluczowe określa po zakończeniu klatek kluczowych (nie określa długość czasu odtwarzania klatek kluczowych).</span><span class="sxs-lookup"><span data-stu-id="3f298-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="3f298-108">Można określić <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> wartości, jako wartość procentowa lub jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> specjalna wartość.</span><span class="sxs-lookup"><span data-stu-id="3f298-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f298-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f298-109">Example</span></span>  
 <span data-ttu-id="3f298-110">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animować prostokąt na ekranie.</span><span class="sxs-lookup"><span data-stu-id="3f298-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="3f298-111">Czasy kluczowych klatek kluczowych są konfigurowane przy użyciu <xref:System.TimeSpan> wartości.</span><span class="sxs-lookup"><span data-stu-id="3f298-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="3f298-112">Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.</span><span class="sxs-lookup"><span data-stu-id="3f298-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="3f298-113">![Wartości klucza są osiągane na 3, 4 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="3f298-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="3f298-114">W kolejnym przykładzie pokazano animacji, który jest identyczny, z tą różnicą, że czasy kluczowych klatek kluczowych są konfigurowane przy użyciu wartości procentowe.</span><span class="sxs-lookup"><span data-stu-id="3f298-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="3f298-115">Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.</span><span class="sxs-lookup"><span data-stu-id="3f298-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="3f298-116">![Wartości klucza są osiągane na 3, 4 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="3f298-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="3f298-117">W następnym przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> wartości czasu klucza.</span><span class="sxs-lookup"><span data-stu-id="3f298-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="3f298-118">Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.</span><span class="sxs-lookup"><span data-stu-id="3f298-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="3f298-119">![Wartości klucza są osiągane w 3.3,6.6 i 9,9 s](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="3f298-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="3f298-120">W ostatnim przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> wartości czasu klucza.</span><span class="sxs-lookup"><span data-stu-id="3f298-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="3f298-121">Poniższa ilustracja przedstawia po osiągnięciu wartości poszczególnych kluczowych klatek.</span><span class="sxs-lookup"><span data-stu-id="3f298-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="3f298-122">![Wartości klucza są osiągane na 0, 5 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="3f298-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="3f298-123">Dla uproszczenia wersje kodu, ten przykład użycia lokalnej animacji, nie scenorysy, ponieważ tylko jednej animacji są stosowane do pojedynczej właściwości, ale przykłady może zmodyfikować tak, aby zamiast tego użyj scenorysów.</span><span class="sxs-lookup"><span data-stu-id="3f298-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="3f298-124">Przykład przedstawiający sposób deklarowania scenorysu w kodzie, zobacz [animować właściwość przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="3f298-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="3f298-125">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="3f298-125">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="3f298-126">Aby uzyskać więcej informacji na temat klatek kluczowych animacji zobacz [Przegląd Animacja kluczowych klatek](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f298-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f298-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f298-127">See Also</span></span>  
 [<span data-ttu-id="3f298-128">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="3f298-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="3f298-129">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="3f298-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="3f298-130">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3f298-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
