---
title: Jak powtórzyć animację
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141552"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="a97af-102">Jak powtórzyć animację</span><span class="sxs-lookup"><span data-stu-id="a97af-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="a97af-103">W tym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pokazano, <xref:System.Windows.Media.Animation.Timeline> jak używać właściwości a w celu kontrolowania powtarzania zachowania animacji.</span><span class="sxs-lookup"><span data-stu-id="a97af-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a97af-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a97af-104">Example</span></span>  
 <span data-ttu-id="a97af-105">Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> kontroluje, <xref:System.Windows.Media.Animation.Timeline> ile razy animacja powtarza jej prosty czas trwania.</span><span class="sxs-lookup"><span data-stu-id="a97af-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="a97af-106">Za <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>pomocą programu można <xref:System.Windows.Media.Animation.Timeline> określić, że powtarza się przez określoną liczbę razy (liczba iteracji) lub przez określony okres czasu.</span><span class="sxs-lookup"><span data-stu-id="a97af-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="a97af-107">W obu przypadkach animacji przechodzi przez tyle od początku do końca uruchamia, że potrzebuje, aby wypełnić żądaną liczbę lub czas trwania.</span><span class="sxs-lookup"><span data-stu-id="a97af-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="a97af-108">Domyślnie osie czasu mają liczbę powtórzeń 1.0, co oznacza, że grają jeden raz i nie powtarzają się.</span><span class="sxs-lookup"><span data-stu-id="a97af-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="a97af-109">Jeśli jednak ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość a <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, oś czasu zostanie powtórzony przez czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="a97af-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="a97af-110">W poniższym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pokazano, jak używać właściwości do kontrolowania powtarzania zachowania animacji.</span><span class="sxs-lookup"><span data-stu-id="a97af-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="a97af-111">Przykład animuje <xref:System.Windows.FrameworkElement.Width%2A> właściwość pięciu prostokątów z każdego prostokąta przy użyciu innego typu zachowania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="a97af-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="a97af-112">Aby uzyskać pełną próbkę, zobacz [Przykład zachowania chronometrażu animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span><span class="sxs-lookup"><span data-stu-id="a97af-112">For the complete sample, see [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97af-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a97af-113">See also</span></span>

- [<span data-ttu-id="a97af-114">Gromadzenie wartości animacji podczas cykli powtórzeń</span><span class="sxs-lookup"><span data-stu-id="a97af-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="a97af-115">Określanie, czy oś czasu ma być automatycznie odtwarzana od końca</span><span class="sxs-lookup"><span data-stu-id="a97af-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="a97af-116">Animacja i chronometraż Tematy porad</span><span class="sxs-lookup"><span data-stu-id="a97af-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="a97af-117">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="a97af-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="a97af-118">Przykład zachowania chronometrażu animacji</span><span class="sxs-lookup"><span data-stu-id="a97af-118">Animation Timing Behavior Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
