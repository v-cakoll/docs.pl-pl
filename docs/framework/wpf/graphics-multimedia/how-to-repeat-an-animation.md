---
title: Jak powtórzyć animację
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 176fc9c31f85361a243cd9357d79608e0ff6a4cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461621"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="2c544-102">Jak powtórzyć animację</span><span class="sxs-lookup"><span data-stu-id="2c544-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="2c544-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> w celu sterowania zachowaniem Powtórz animację.</span><span class="sxs-lookup"><span data-stu-id="2c544-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c544-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c544-104">Example</span></span>  
 <span data-ttu-id="2c544-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, ile razy animacji powtarza proste czas jego trwania.</span><span class="sxs-lookup"><span data-stu-id="2c544-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="2c544-106">Za pomocą <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, można określić, że <xref:System.Windows.Media.Animation.Timeline> powtarza określoną liczbę razy (liczba iteracji) lub w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="2c544-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="2c544-107">W obu przypadkach animacji przechodzi przez dowolną liczbę przebiegów początku do końca, których potrzebuje, aby wypełnić żądana liczba lub czas trwania.</span><span class="sxs-lookup"><span data-stu-id="2c544-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="2c544-108">Domyślnie osie czasu mają liczbę powtórzeń 1.0, co oznacza odtwarzania jeden raz, a nie powtarzaj.</span><span class="sxs-lookup"><span data-stu-id="2c544-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="2c544-109">Jednak jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, oś czasu jest powtarzany na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="2c544-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="2c544-110">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości do sterowania zachowaniem powtarzanie animacji.</span><span class="sxs-lookup"><span data-stu-id="2c544-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="2c544-111">Przykład animuje <xref:System.Windows.FrameworkElement.Width%2A> właściwość pięć prostokąty z każdego prostokąta przy użyciu innego typu zachowanie Powtórz tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="2c544-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="2c544-112">Aby uzyskać pełny przykład, zobacz [przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="2c544-112">For the complete sample, see [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c544-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c544-113">See Also</span></span>  
 [<span data-ttu-id="2c544-114">Gromadzenie wartości animacji podczas cykli powtórzeń</span><span class="sxs-lookup"><span data-stu-id="2c544-114">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="2c544-115">Określanie, czy oś czasu ma być automatycznie odtwarzana od końca</span><span class="sxs-lookup"><span data-stu-id="2c544-115">Specify Whether a Timeline Automatically Reverses</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [<span data-ttu-id="2c544-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="2c544-116">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [<span data-ttu-id="2c544-117">Animacja i chronometraż</span><span class="sxs-lookup"><span data-stu-id="2c544-117">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="2c544-118">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="2c544-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="2c544-119">Przykład zachowania chronometrażu animacji</span><span class="sxs-lookup"><span data-stu-id="2c544-119">Animation Timing Behavior Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159970)
