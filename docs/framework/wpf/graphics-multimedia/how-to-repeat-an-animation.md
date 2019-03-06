---
title: 'Instrukcje: Powtórz animację'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: a098c912289f59f8be48edeec0f066b7f94b9fda
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354010"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="06e12-102">Instrukcje: Powtórz animację</span><span class="sxs-lookup"><span data-stu-id="06e12-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="06e12-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> w celu sterowania zachowaniem Powtórz animację.</span><span class="sxs-lookup"><span data-stu-id="06e12-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06e12-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="06e12-104">Example</span></span>  
 <span data-ttu-id="06e12-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, ile razy animacji powtarza proste czas jego trwania.</span><span class="sxs-lookup"><span data-stu-id="06e12-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="06e12-106">Za pomocą <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, można określić, że <xref:System.Windows.Media.Animation.Timeline> powtarza określoną liczbę razy (liczba iteracji) lub w określonym przedziale czasu.</span><span class="sxs-lookup"><span data-stu-id="06e12-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="06e12-107">W obu przypadkach animacji przechodzi przez dowolną liczbę przebiegów początku do końca, których potrzebuje, aby wypełnić żądana liczba lub czas trwania.</span><span class="sxs-lookup"><span data-stu-id="06e12-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="06e12-108">Domyślnie osie czasu mają liczbę powtórzeń 1.0, co oznacza odtwarzania jeden raz, a nie powtarzaj.</span><span class="sxs-lookup"><span data-stu-id="06e12-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="06e12-109">Jednak jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, oś czasu jest powtarzany na czas nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="06e12-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="06e12-110">Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości do sterowania zachowaniem powtarzanie animacji.</span><span class="sxs-lookup"><span data-stu-id="06e12-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="06e12-111">Przykład animuje <xref:System.Windows.FrameworkElement.Width%2A> właściwość pięć prostokąty z każdego prostokąta przy użyciu innego typu zachowanie Powtórz tę procedurę.</span><span class="sxs-lookup"><span data-stu-id="06e12-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="06e12-112">Aby uzyskać pełny przykład, zobacz [przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="06e12-112">For the complete sample, see [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e12-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06e12-113">See also</span></span>
- [<span data-ttu-id="06e12-114">Gromadzenie wartości animacji podczas cykli powtórzeń</span><span class="sxs-lookup"><span data-stu-id="06e12-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="06e12-115">Określanie, czy oś czasu ma być automatycznie odtwarzana od końca</span><span class="sxs-lookup"><span data-stu-id="06e12-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="06e12-116">Animacja i chronometraż tematy porad</span><span class="sxs-lookup"><span data-stu-id="06e12-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="06e12-117">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="06e12-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="06e12-118">Przykład zachowania chronometrażu animacji</span><span class="sxs-lookup"><span data-stu-id="06e12-118">Animation Timing Behavior Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159970)
