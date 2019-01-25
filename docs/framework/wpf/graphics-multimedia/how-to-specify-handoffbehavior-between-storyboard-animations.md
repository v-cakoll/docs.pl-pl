---
title: 'Instrukcje: Określ HandoffBehavior między animacjami scenorysu'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: 01c652e170e27da0be9b1ab5f7659d7089aee6f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677755"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="09db0-102">Instrukcje: Określ HandoffBehavior między animacjami scenorysu</span><span class="sxs-lookup"><span data-stu-id="09db0-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="09db0-103">W tym przykładzie pokazano, jak określić zachowanie dotyczące przekazania między animacjami scenorysu.</span><span class="sxs-lookup"><span data-stu-id="09db0-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="09db0-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.BeginStoryboard> Określa, jak nowe animacji interakcji z wszelkie istniejące, które już są stosowane do właściwości.</span><span class="sxs-lookup"><span data-stu-id="09db0-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09db0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="09db0-105">Example</span></span>  
 <span data-ttu-id="09db0-106">Poniższy przykład tworzy dwa przyciski powiększania, gdy kursor myszy przesuwa się nad nimi, które stają się mniejsza, gdy kursor przesuwa się natychmiast.</span><span class="sxs-lookup"><span data-stu-id="09db0-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="09db0-107">Jeśli wskaźnik myszy na przycisku i szybko usunąć kursor drugiej animacji będą stosowane przed zakończeniem pierwszy z nich.</span><span class="sxs-lookup"><span data-stu-id="09db0-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="09db0-108">Jest to, gdy dwa animacji nakładają się następująco, które mogą zobaczyć różnicę między <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> wartości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> i <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="09db0-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="09db0-109">Wartość <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> łączy nakładających się animacji, powodując gładkie przejście między animacjami podczas wartość <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> powoduje, że nowej animacji od razu zastąpić wcześniej nakładających się animacji.</span><span class="sxs-lookup"><span data-stu-id="09db0-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="09db0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09db0-110">See also</span></span>
- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [<span data-ttu-id="09db0-111">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="09db0-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="09db0-112">Animacja i chronometraż</span><span class="sxs-lookup"><span data-stu-id="09db0-112">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="09db0-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="09db0-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
