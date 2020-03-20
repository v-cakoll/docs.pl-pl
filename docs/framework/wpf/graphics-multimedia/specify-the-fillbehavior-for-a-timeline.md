---
title: Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141176"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="8b5ba-102">Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności</span><span class="sxs-lookup"><span data-stu-id="8b5ba-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="8b5ba-103">W tym przykładzie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pokazano, jak <xref:System.Windows.Media.Animation.Timeline> określić dla nieaktywne animowane właściwości.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5ba-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b5ba-104">Example</span></span>  
 <span data-ttu-id="8b5ba-105">Właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a <xref:System.Windows.Media.Animation.Timeline> określa, co dzieje się z wartością animowanej właściwości, gdy <xref:System.Windows.Media.Animation.Timeline> nie jest animowany, <xref:System.Windows.Media.Animation.Timeline> to znaczy, gdy jest nieaktywny, ale jego element nadrzędny znajduje się wewnątrz jego aktywnego lub okresu wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="8b5ba-106">Na przykład animowana właściwość pozostaje na swojej wartości końcowej po zakończeniu animacji lub powraca do wartości, którą miała przed rozpoczęciem animacji?</span><span class="sxs-lookup"><span data-stu-id="8b5ba-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="8b5ba-107">W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="8b5ba-108">Każdy prostokąt używa innego <xref:System.Windows.Media.Animation.Timeline> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="8b5ba-109">Jeden <xref:System.Windows.Media.Animation.Timeline> ma, że jest ustawiona <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> na <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, <xref:System.Windows.Media.Animation.Timeline> aby powrócić do jego wartości nieanimowany po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="8b5ba-110">Drugi <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>co powoduje, że szerokość pozostaje na <xref:System.Windows.Media.Animation.Timeline> jego wartości końcowej, gdy kończy.</span><span class="sxs-lookup"><span data-stu-id="8b5ba-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="8b5ba-111">Aby uzyskać pełną próbkę, zobacz [Przykładowa galeria animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="8b5ba-111">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5ba-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b5ba-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="8b5ba-113">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="8b5ba-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="8b5ba-114">Animacja i chronometraż Tematy porad</span><span class="sxs-lookup"><span data-stu-id="8b5ba-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
