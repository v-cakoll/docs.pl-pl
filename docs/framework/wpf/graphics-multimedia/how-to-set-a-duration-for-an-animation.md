---
title: "Jak ustawić czas trwania dla animacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9560e9d0a2809ae8f55a060eaec3b271539d5f94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="45c1f-102">Jak ustawić czas trwania dla animacji</span><span class="sxs-lookup"><span data-stu-id="45c1f-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="45c1f-103">A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długość danego segmentu jest określany na osi czasu <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="45c1f-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="45c1f-104">Gdy <xref:System.Windows.Media.Animation.Timeline> rzędach jego trwania zatrzymuje odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="45c1f-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="45c1f-105">Jeśli <xref:System.Windows.Media.Animation.Timeline> ma osi podrzędnej one zatrzymać odtwarzanie również.</span><span class="sxs-lookup"><span data-stu-id="45c1f-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="45c1f-106">W przypadku animacji <xref:System.Windows.Duration> Określa, jak długo animacji umożliwia przejście ze swojej wartości początkowej, do jego wartości końcowej.</span><span class="sxs-lookup"><span data-stu-id="45c1f-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="45c1f-107">Można określić <xref:System.Windows.Duration> czasu określone, skończoną lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="45c1f-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="45c1f-108">Czas trwania animacji musi być zawsze wartość czasu, ponieważ animacji zawsze musi mieć długość zdefiniowana, ograniczone — w przeciwnym razie animacji nie wiedział, jak przejście od jego wartości docelowych.</span><span class="sxs-lookup"><span data-stu-id="45c1f-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="45c1f-109">Kontener osi czasu (<xref:System.Windows.Media.Animation.TimelineGroup> obiektów), takich jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, ma domyślny okres <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="45c1f-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="45c1f-110">W poniższych przykład szerokości, wysokości i wypełnienia kolor <xref:System.Windows.Shapes.Rectangle> jest animowany.</span><span class="sxs-lookup"><span data-stu-id="45c1f-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="45c1f-111">Czas trwania są ustawiane na osiach czasu animacji i kontener skutki animacji, w tym kontrolowanie postrzegana prędkość animacji i zastępowanie czas trwania podrzędnych osi czasu z czasem trwania elementu timeline kontenera.</span><span class="sxs-lookup"><span data-stu-id="45c1f-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45c1f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="45c1f-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="45c1f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45c1f-113">See Also</span></span>  
 <xref:System.Windows.Duration>  
 [<span data-ttu-id="45c1f-114">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="45c1f-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
