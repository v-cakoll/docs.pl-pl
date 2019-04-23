---
title: 'Instrukcje: Ustawianie czas trwania animacji'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198793"
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="aa601-102">Instrukcje: Ustawianie czas trwania animacji</span><span class="sxs-lookup"><span data-stu-id="aa601-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="aa601-103">A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długość danego segmentu jest ustalany na osi czasu <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="aa601-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="aa601-104">Gdy <xref:System.Windows.Media.Animation.Timeline> osiągnie koniec jego trwania przestaje odtwarzania.</span><span class="sxs-lookup"><span data-stu-id="aa601-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="aa601-105">Jeśli <xref:System.Windows.Media.Animation.Timeline> podrzędnych osi czasu, ma także odtwarzanie one zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="aa601-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="aa601-106">W przypadku animacji <xref:System.Windows.Duration> określa animacji czas przejścia z jej wartość początkową wartość końcową.</span><span class="sxs-lookup"><span data-stu-id="aa601-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="aa601-107">Można określić <xref:System.Windows.Duration> przy użyciu określonych, skończony czas lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="aa601-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="aa601-108">Czas trwania animacji musi być zawsze wartość czasu, ponieważ animacji zawsze musi mieć zdefiniowany, skończonego długość — w przeciwnym razie animacja będzie wiadomo, jak przejście pomiędzy jego wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="aa601-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="aa601-109">Osie czasu kontenera (<xref:System.Windows.Media.Animation.TimelineGroup> obiektów), takie jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, mają domyślny czas trwania <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="aa601-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="aa601-110">W poniższy przykład szerokości, wysokości i wypełnienia kolor <xref:System.Windows.Shapes.Rectangle> jest animowany.</span><span class="sxs-lookup"><span data-stu-id="aa601-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="aa601-111">Czas trwania są ustawione na osi czasu animacji i kontener skutkuje efektów animacji, w tym kontrolowanie postrzegany szybkość animacji i zastępowanie czas trwania podrzędnych osi czasu z czasem trwania osi czasu w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="aa601-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa601-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa601-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="aa601-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa601-113">See also</span></span>

- <xref:System.Windows.Duration>
- [<span data-ttu-id="aa601-114">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="aa601-114">Animation Overview</span></span>](animation-overview.md)
