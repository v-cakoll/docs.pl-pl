---
title: Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 947be09140dc2d1d5e130ccb74472d8dce3408cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563483"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="97ff1-102">Jak określić FillBehavior dla przedziału czasowego, który osiągnął koniec swojego okresu aktywności</span><span class="sxs-lookup"><span data-stu-id="97ff1-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="97ff1-103">W tym przykładzie przedstawiono sposób określania <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> dla nieaktywnych <xref:System.Windows.Media.Animation.Timeline> animowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="97ff1-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97ff1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="97ff1-104">Example</span></span>  
 <span data-ttu-id="97ff1-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, co się dzieje z wartości właściwości animowany, gdy nie jest on animowany, oznacza to, kiedy <xref:System.Windows.Media.Animation.Timeline> jest nieaktywna, ale jego element nadrzędny <xref:System.Windows.Media.Animation.Timeline> znajduje się wewnątrz jego aktywny lub okres przechowywania.</span><span class="sxs-lookup"><span data-stu-id="97ff1-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="97ff1-106">Na przykład jest właściwością animowany pozostają na jej końcu wartość po animacji kończy się lub nie go przywrócić wartość sprzed animacja została uruchomiona?</span><span class="sxs-lookup"><span data-stu-id="97ff1-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="97ff1-107">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania <xref:System.Windows.FrameworkElement.Width%2A> dwóch prostokątów.</span><span class="sxs-lookup"><span data-stu-id="97ff1-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="97ff1-108">Każdy prostokąt używa innej <xref:System.Windows.Media.Animation.Timeline> obiektu.</span><span class="sxs-lookup"><span data-stu-id="97ff1-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="97ff1-109">Jeden <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> który ustawiono <xref:System.Windows.Media.Animation.FillBehavior.Stop>, co powoduje, że szerokość prostokąta, aby powrócić do jego z systemem innym niż — animowane wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy się.</span><span class="sxs-lookup"><span data-stu-id="97ff1-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="97ff1-110">Druga <xref:System.Windows.Media.Animation.Timeline> ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, co powoduje, że szerokość pozostaje na jej końcu wartość przy <xref:System.Windows.Media.Animation.Timeline> kończy się.</span><span class="sxs-lookup"><span data-stu-id="97ff1-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="97ff1-111">Pełny przykład, zobacz [galerii przykład animacji](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="97ff1-111">For the complete sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97ff1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97ff1-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [<span data-ttu-id="97ff1-113">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="97ff1-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="97ff1-114">Synchronizację</span><span class="sxs-lookup"><span data-stu-id="97ff1-114">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="97ff1-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="97ff1-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
