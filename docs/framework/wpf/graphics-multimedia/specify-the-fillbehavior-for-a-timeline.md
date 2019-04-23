---
title: 'Instrukcje: Określanie elementu FillBehavior dla osi czasu, która osiągnęła koniec swojego okresu aktywności'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 9f03c5b8d4585c32e0a9f119649dd15a23523033
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091129"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="d6323-102">Instrukcje: Określanie elementu FillBehavior dla osi czasu, która osiągnęła koniec swojego okresu aktywności</span><span class="sxs-lookup"><span data-stu-id="d6323-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="d6323-103">W tym przykładzie pokazano, jak określić <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dla nieaktywnych <xref:System.Windows.Media.Animation.Timeline> właściwości animowany.</span><span class="sxs-lookup"><span data-stu-id="d6323-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6323-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6323-104">Example</span></span>  
 <span data-ttu-id="d6323-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, co się dzieje z wartości właściwości animowany, gdy nie jest animowany, oznacza to, kiedy <xref:System.Windows.Media.Animation.Timeline> jest nieaktywna, ale jego element nadrzędny <xref:System.Windows.Media.Animation.Timeline> znajduje się wewnątrz jego aktywny lub okres przechowywania.</span><span class="sxs-lookup"><span data-stu-id="d6323-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="d6323-106">Na przykład, jest animowany właściwości pozostają w jego końcem wartości po animacji kończy się lub zrobi to przywrócić wartość miała zanim animacja została uruchomiona?</span><span class="sxs-lookup"><span data-stu-id="d6323-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="d6323-107">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="d6323-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="d6323-108">Każdego prostokąta używa innego <xref:System.Windows.Media.Animation.Timeline> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d6323-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="d6323-109">Jeden <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> który jest skonfigurowany do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, aby powrócić do jego bez — animowane wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy.</span><span class="sxs-lookup"><span data-stu-id="d6323-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="d6323-110">Druga <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, co powoduje, że szerokość pozostaje na jej końcu wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy.</span><span class="sxs-lookup"><span data-stu-id="d6323-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="d6323-111">Aby uzyskać pełny przykład, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="d6323-111">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6323-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6323-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="d6323-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="d6323-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="d6323-114">Animacja i chronometraż tematy porad</span><span class="sxs-lookup"><span data-stu-id="d6323-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
