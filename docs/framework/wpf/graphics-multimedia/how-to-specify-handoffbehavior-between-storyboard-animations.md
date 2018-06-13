---
title: Jak określić HandoffBehavior między animacjami scenorysu
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: c4728dc1cb4eeeff55e533b8d91e4512d9cc1d94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560554"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="3fec8-102">Jak określić HandoffBehavior między animacjami scenorysu</span><span class="sxs-lookup"><span data-stu-id="3fec8-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="3fec8-103">Ten przykład przedstawia sposób określania zachowania przekazaniem między animacje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="3fec8-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="3fec8-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.BeginStoryboard> określa sposób animacje interakcji z istniejących komunikatów, które już są stosowane do właściwości.</span><span class="sxs-lookup"><span data-stu-id="3fec8-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fec8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fec8-105">Example</span></span>  
 <span data-ttu-id="3fec8-106">Poniższy przykład tworzy dwa przyciski powiększania, gdy wskaźnik myszy przesuwa się nad nimi, które stają się mniejszy, gdy kursor przesuwa optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="3fec8-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="3fec8-107">Jeśli wskaźnik myszy na przycisk, a następnie szybko Usuń kursora, drugi animacji zostaną zastosowane przed zakończeniem pierwszego z nich.</span><span class="sxs-lookup"><span data-stu-id="3fec8-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="3fec8-108">Jest w przypadku dwóch animacje nakłada się na podobny do tego, które widać różnicę między <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> wartości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> i <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="3fec8-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="3fec8-109">Wartość <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> łączy nakładające się animacji, powodując płynniejszy przejścia między animacji podczas wartość <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> powoduje, że nowe animacji natychmiast zastąpienie wcześniej nakładające się animacji.</span><span class="sxs-lookup"><span data-stu-id="3fec8-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3fec8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fec8-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="3fec8-111">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="3fec8-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="3fec8-112">Synchronizację</span><span class="sxs-lookup"><span data-stu-id="3fec8-112">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="3fec8-113">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3fec8-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
