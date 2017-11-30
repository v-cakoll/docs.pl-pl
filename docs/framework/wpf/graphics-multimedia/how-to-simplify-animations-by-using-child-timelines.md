---
title: "Jak uprościć animacje przy użyciu podrzędnych szeregów czasowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daa4caac0046293e8b86a773bfffd46cf30e835b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a><span data-ttu-id="47566-102">Jak uprościć animacje przy użyciu podrzędnych szeregów czasowych</span><span class="sxs-lookup"><span data-stu-id="47566-102">How to: Simplify Animations by Using Child Timelines</span></span>
<span data-ttu-id="47566-103">W tym przykładzie pokazano, jak uprościć animacji za pomocą podrzędnej <xref:System.Windows.Media.Animation.ParallelTimeline> obiektów.</span><span class="sxs-lookup"><span data-stu-id="47566-103">This example shows how to simplify animations by using child <xref:System.Windows.Media.Animation.ParallelTimeline> objects.</span></span> <span data-ttu-id="47566-104">A <xref:System.Windows.Media.Animation.Storyboard> jest typem <xref:System.Windows.Media.Animation.Timeline> udostępniająca informacje określania wartości docelowej dla osi czasu, zawiera.</span><span class="sxs-lookup"><span data-stu-id="47566-104">A <xref:System.Windows.Media.Animation.Storyboard> is a type of <xref:System.Windows.Media.Animation.Timeline> that provides targeting information for the timelines it contains.</span></span> <span data-ttu-id="47566-105">Użyj <xref:System.Windows.Media.Animation.Storyboard> zapewnienie kierowanie informacji, w tym informacje o obiekcie i właściwości osi czasu.</span><span class="sxs-lookup"><span data-stu-id="47566-105">Use a <xref:System.Windows.Media.Animation.Storyboard> to provide timeline targeting information, including object and property information.</span></span>  
  
 <span data-ttu-id="47566-106">Aby rozpocząć animacji, użyj jednej lub kilku <xref:System.Windows.Media.Animation.ParallelTimeline> obiekty jako elementy podrzędne zagnieżdżonych <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="47566-106">To begin an animation, use one or more <xref:System.Windows.Media.Animation.ParallelTimeline> objects as nested child elements of a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="47566-107">Te <xref:System.Windows.Media.Animation.ParallelTimeline> obiekty mogą zawierać inne animacji i w związku z tym można lepiej Hermetyzowanie sekwencji chronometrażu w złożonych animacji.</span><span class="sxs-lookup"><span data-stu-id="47566-107">These <xref:System.Windows.Media.Animation.ParallelTimeline> objects can contain other animations and therefore, can better encapsulate the timing sequences in complex animations.</span></span> <span data-ttu-id="47566-108">Na przykład, jeśli są animacji <xref:System.Windows.Controls.TextBlock> i kilka kształtów w tej samej <xref:System.Windows.Media.Animation.Storyboard>, można oddzielić animacji dla <xref:System.Windows.Controls.TextBlock> i kształty umieszczanie każdego w osobnym <xref:System.Windows.Media.Animation.ParallelTimeline>.</span><span class="sxs-lookup"><span data-stu-id="47566-108">For example, if you are animating a <xref:System.Windows.Controls.TextBlock> and several shapes in the same <xref:System.Windows.Media.Animation.Storyboard>, you can separate the animations for the <xref:System.Windows.Controls.TextBlock> and the shapes, putting each into a separate <xref:System.Windows.Media.Animation.ParallelTimeline>.</span></span> <span data-ttu-id="47566-109">Ponieważ każdy <xref:System.Windows.Media.Animation.ParallelTimeline> ma własną <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> i wszystkie elementy podrzędne <xref:System.Windows.Media.Animation.ParallelTimeline> rozpocząć względem to <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, lepiej jest hermetyzowany chronometrażu.</span><span class="sxs-lookup"><span data-stu-id="47566-109">Because each <xref:System.Windows.Media.Animation.ParallelTimeline> has its own <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> and all child elements of the <xref:System.Windows.Media.Animation.ParallelTimeline> begin relative to this <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, timing is better encapsulated.</span></span>  
  
 <span data-ttu-id="47566-110">Poniższy przykład animuje dwóch fragmentów tekstu (<xref:System.Windows.Controls.TextBlock> obiektów) od w tym samym <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="47566-110">The following example animates two pieces of text (<xref:System.Windows.Controls.TextBlock> objects) from within the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="47566-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> hermetyzuje animacji w jednej z <xref:System.Windows.Controls.TextBlock> obiektów.</span><span class="sxs-lookup"><span data-stu-id="47566-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsulates the animations of one of the <xref:System.Windows.Controls.TextBlock> objects.</span></span>  
  
 <span data-ttu-id="47566-112">**Wydajność Uwaga:** mimo że można zagnieżdżać <xref:System.Windows.Media.Animation.Storyboard> osi czasu wewnątrz innych, <xref:System.Windows.Media.Animation.ParallelTimeline>s są bardziej odpowiednie dla zagnieżdżania, ponieważ wymagają one mniejsze koszty.</span><span class="sxs-lookup"><span data-stu-id="47566-112">**Performance Note:** Although you can nest <xref:System.Windows.Media.Animation.Storyboard> timelines inside each other, <xref:System.Windows.Media.Animation.ParallelTimeline>s are more suitable for nesting because they require less overhead.</span></span> <span data-ttu-id="47566-113">( <xref:System.Windows.Media.Animation.Storyboard> Klasa dziedziczy <xref:System.Windows.Media.Animation.ParallelTimeline> klasy.)</span><span class="sxs-lookup"><span data-stu-id="47566-113">(The <xref:System.Windows.Media.Animation.Storyboard> class inherits from the <xref:System.Windows.Media.Animation.ParallelTimeline> class.)</span></span>  
  
## <a name="example"></a><span data-ttu-id="47566-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="47566-114">Example</span></span>  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="47566-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47566-115">See Also</span></span>  
 [<span data-ttu-id="47566-116">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="47566-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="47566-117">Określ właściwości HandoffBehavior między scenorysu animacji</span><span class="sxs-lookup"><span data-stu-id="47566-117">Specify HandoffBehavior Between Storyboard Animations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
