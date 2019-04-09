---
title: 'Instrukcje: Kontrolować Scenorys po uruchomieniu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161489"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="8cc82-102">Instrukcje: Kontrolować Scenorys po uruchomieniu</span><span class="sxs-lookup"><span data-stu-id="8cc82-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="8cc82-103">W tym przykładzie pokazano, jak używać kodu do kontroli <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="8cc82-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="8cc82-104">Aby kontrolować scenorys w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Trigger> i <xref:System.Windows.TriggerAction> obiektów; Aby uzyskać przykład, zobacz [użyć wyzwalaczy zdarzeń, aby kontrolować Scenorys po uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="8cc82-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="8cc82-105">Aby rozpocząć scenorysu, należy użyć jego <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody, która dystrybuuje animacjami scenorysu, właściwości, animowanie i uruchamia scenorysu.</span><span class="sxs-lookup"><span data-stu-id="8cc82-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="8cc82-106">Aby scenorysu sterowane, użyj <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody i określ **true** jako drugi parametr.</span><span class="sxs-lookup"><span data-stu-id="8cc82-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="8cc82-107">Następnie można metod interakcyjnych scenorysu wstrzymać, wznowić, wyszukiwanie, Zatrzymaj, przyspieszyć, lub spowolnić scenorysu lub przejdź go do okresu wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="8cc82-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="8cc82-108">Oto lista metod interakcyjnych scenorysu:</span><span class="sxs-lookup"><span data-stu-id="8cc82-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A><span data-ttu-id="8cc82-109">: Wstrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="8cc82-109">: Pauses the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A><span data-ttu-id="8cc82-110">: Wznawia działanie wstrzymanej scenorysu.</span><span class="sxs-lookup"><span data-stu-id="8cc82-110">: Resumes a paused storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A><span data-ttu-id="8cc82-111">: Ustawia szybkość interaktywne scenorysu.</span><span class="sxs-lookup"><span data-stu-id="8cc82-111">: Sets the storyboard's interactive speed.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A><span data-ttu-id="8cc82-112">: Szuka scenorysu określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8cc82-112">: Seeks the storyboard the specified location.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A><span data-ttu-id="8cc82-113">: Szuka scenorysu do określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8cc82-113">: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="8cc82-114">W odróżnieniu od <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metody, ta operacja jest przetwarzana przed następnym znaczników.</span><span class="sxs-lookup"><span data-stu-id="8cc82-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A><span data-ttu-id="8cc82-115">: Przesuwa scenorysu do okresu wypełnienia, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="8cc82-115">: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A><span data-ttu-id="8cc82-116">: Zatrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="8cc82-116">: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="8cc82-117">W poniższym przykładzie kilka metod scenorysu są używane do interaktywnie kontrolować scenorys.</span><span class="sxs-lookup"><span data-stu-id="8cc82-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="8cc82-118">**Uwaga:** Aby zobaczyć przykład kontrolowanie scenorysu, za pomocą wyzwalaczy z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [użyć wyzwalaczy zdarzeń, aby kontrolować Scenorys po uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="8cc82-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cc82-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cc82-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8cc82-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cc82-120">See also</span></span>

- [<span data-ttu-id="8cc82-121">Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8cc82-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
