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
ms.openlocfilehash: 7aacb975557a25b8ea7a80e02c16a59b8a746e26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562300"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="83df8-102">Jak kontrolować chronometraż animacji kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="83df8-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="83df8-103">W tym przykładzie przedstawiono sposób kontrolować czas klatek kluczowych w animacji ramki klucza.</span><span class="sxs-lookup"><span data-stu-id="83df8-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="83df8-104">Podobnie jak inne animacje mają klucz poklatkowych <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="83df8-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="83df8-105">Oprócz określanie czasu trwania animacji, należy określić, jaka część ten czas trwania jest przydzielony do każdego z jego klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="83df8-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="83df8-106">Aby przyznać czas, należy określić <xref:System.Windows.Media.Animation.KeyTime> dla każdego klatek kluczowych animacji.</span><span class="sxs-lookup"><span data-stu-id="83df8-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="83df8-107"><xref:System.Windows.Media.Animation.KeyTime> Dla każdej klatki określa podczas zakończenia klatki (nie określa czas odgrywa klatek kluczowych).</span><span class="sxs-lookup"><span data-stu-id="83df8-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="83df8-108">Można określić <xref:System.Windows.Media.Animation.KeyTime> jako <xref:System.TimeSpan> wartości, w procentach lub jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> specjalna wartość.</span><span class="sxs-lookup"><span data-stu-id="83df8-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83df8-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="83df8-109">Example</span></span>  
 <span data-ttu-id="83df8-110">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania prostokąt na ekranie.</span><span class="sxs-lookup"><span data-stu-id="83df8-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="83df8-111">Klatek kluczowych klucza czasy są konfigurowane przy użyciu <xref:System.TimeSpan> wartości.</span><span class="sxs-lookup"><span data-stu-id="83df8-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="83df8-112">Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.</span><span class="sxs-lookup"><span data-stu-id="83df8-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="83df8-113">![Wartości klucza są osiągane w 3, 4 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="83df8-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="83df8-114">W kolejnym przykładzie pokazano animacji, który jest taki sam, z wyjątkiem tego, że czasy klucza klatek kluczowych są konfigurowane przy użyciu wartości procentowe.</span><span class="sxs-lookup"><span data-stu-id="83df8-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="83df8-115">Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.</span><span class="sxs-lookup"><span data-stu-id="83df8-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="83df8-116">![Wartości klucza są osiągane w 3, 4 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="83df8-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="83df8-117">W następnym przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> wartości czasu klucza.</span><span class="sxs-lookup"><span data-stu-id="83df8-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="83df8-118">Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.</span><span class="sxs-lookup"><span data-stu-id="83df8-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="83df8-119">![Wartości klucza są osiągane w 3.3,6.6 i 9,9 s](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="83df8-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="83df8-120">W ostatnim przykładzie użyto <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> wartości czasu klucza.</span><span class="sxs-lookup"><span data-stu-id="83df8-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="83df8-121">Na poniższej ilustracji pokazano po osiągnięciu wartości każdego klatki.</span><span class="sxs-lookup"><span data-stu-id="83df8-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="83df8-122">![Wartości klucza są osiągane na 0, 5 i 10 sekund](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="83df8-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="83df8-123">Dla uproszczenia wersje kodu to przykład użycia lokalnej animacji, nie scenorys, ponieważ tylko jednego animacji jest stosowana do jednej właściwości, ale może być modyfikowany przykłady zamiast tego użyć scenorys.</span><span class="sxs-lookup"><span data-stu-id="83df8-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="83df8-124">Na przykład pokazujący sposób zadeklarować scenorysu w kodzie, zobacz [animować właściwości przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="83df8-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="83df8-125">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="83df8-125">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="83df8-126">Aby uzyskać więcej informacji na temat klatek kluczowych animacji, zobacz [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83df8-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83df8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83df8-127">See Also</span></span>  
 [<span data-ttu-id="83df8-128">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="83df8-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="83df8-129">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="83df8-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="83df8-130">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="83df8-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
