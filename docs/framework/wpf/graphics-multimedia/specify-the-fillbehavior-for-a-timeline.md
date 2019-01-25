---
title: 'Instrukcje: Określ FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 6745cf5d57a341068e93784d5487f21e34f8a64a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530106"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="1be8d-102">Instrukcje: Określ FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności</span><span class="sxs-lookup"><span data-stu-id="1be8d-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="1be8d-103">W tym przykładzie pokazano, jak określić <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dla nieaktywnych <xref:System.Windows.Media.Animation.Timeline> właściwości animowany.</span><span class="sxs-lookup"><span data-stu-id="1be8d-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be8d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1be8d-104">Example</span></span>  
 <span data-ttu-id="1be8d-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, co się dzieje z wartości właściwości animowany, gdy nie jest animowany, oznacza to, kiedy <xref:System.Windows.Media.Animation.Timeline> jest nieaktywna, ale jego element nadrzędny <xref:System.Windows.Media.Animation.Timeline> znajduje się wewnątrz jego aktywny lub okres przechowywania.</span><span class="sxs-lookup"><span data-stu-id="1be8d-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="1be8d-106">Na przykład, jest animowany właściwości pozostają w jego końcem wartości po animacji kończy się lub zrobi to przywrócić wartość miała zanim animacja została uruchomiona?</span><span class="sxs-lookup"><span data-stu-id="1be8d-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="1be8d-107">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="1be8d-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="1be8d-108">Każdego prostokąta używa innego <xref:System.Windows.Media.Animation.Timeline> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1be8d-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="1be8d-109">Jeden <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> który jest skonfigurowany do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, aby powrócić do jego bez — animowane wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy.</span><span class="sxs-lookup"><span data-stu-id="1be8d-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="1be8d-110">Druga <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, co powoduje, że szerokość pozostaje na jej końcu wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy.</span><span class="sxs-lookup"><span data-stu-id="1be8d-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="1be8d-111">Aby uzyskać pełny przykład, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="1be8d-111">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be8d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1be8d-112">See also</span></span>
- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="1be8d-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="1be8d-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="1be8d-114">Animacja i chronometraż</span><span class="sxs-lookup"><span data-stu-id="1be8d-114">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="1be8d-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1be8d-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
