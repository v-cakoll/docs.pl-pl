---
title: "Jak kontrolować scenorys po uruchomieniu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 051ac6fea73b207fb5ef4d6293c5e996552f1281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="e8eb5-102">Jak kontrolować scenorys po uruchomieniu</span><span class="sxs-lookup"><span data-stu-id="e8eb5-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="e8eb5-103">W tym przykładzie przedstawiono użycie kodu w celu sterowania <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="e8eb5-104">Aby kontrolować scenorysu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Trigger> i <xref:System.Windows.TriggerAction> obiektów, na przykład sprawdzić, [Użyj wyzwalacze zdarzeń, aby kontrolować scenorysu po jego uruchomieniu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="e8eb5-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="e8eb5-105">Aby uruchomić scenorysu, należy użyć jego <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodę, która dystrybuuje scenorysu animacji właściwości animacji i uruchamia scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="e8eb5-106">Aby wprowadzić sterowane scenorysu, należy użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> — metoda i określ **true** jako drugiego parametru.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="e8eb5-107">Następnie można metody interakcyjne scenorysu wstrzymać, wznowić, wyszukiwanie, Zatrzymaj, przyspieszyć, lub spowolnić scenorysu lub jego dojściu do okresu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="e8eb5-108">Oto lista metod interakcyjne scenorysu:</span><span class="sxs-lookup"><span data-stu-id="e8eb5-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <span data-ttu-id="e8eb5-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Wstrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="e8eb5-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Wznawia działanie wstrzymanej scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="e8eb5-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Ustawia szybkość interakcyjne scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
-   <span data-ttu-id="e8eb5-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Stara scenorysu określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
-   <span data-ttu-id="e8eb5-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Stara scenorysu do określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="e8eb5-114">W odróżnieniu od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody, ta operacja jest przetwarzana przed następnym znaczników.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <span data-ttu-id="e8eb5-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Przesuwa scenorys z okresu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="e8eb5-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Przestaje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="e8eb5-117">W poniższym przykładzie kilka metod scenorysu są używane do sterowania interaktywnego scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8eb5-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="e8eb5-118">**Uwaga:** aby zobaczyć przykładowy kontrolowanie scenorysu przy użyciu wyzwalaczy z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [wyzwalacze zdarzeń używana do sterowania scenorysu po jego uruchomieniu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="e8eb5-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8eb5-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8eb5-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e8eb5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8eb5-120">See Also</span></span>  
 [<span data-ttu-id="e8eb5-121">Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e8eb5-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
