---
title: 'Instrukcje: Kontrolowanie scenorysu po rozpoczęciu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855866"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="58f1b-102">Instrukcje: Kontrolowanie scenorysu po rozpoczęciu</span><span class="sxs-lookup"><span data-stu-id="58f1b-102">How to: Control a Storyboard After It Starts</span></span>

<span data-ttu-id="58f1b-103">Ten przykład pokazuje, <xref:System.Windows.Media.Animation.Storyboard> jak używać kodu do sterowania po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="58f1b-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="58f1b-104">Aby kontrolować scenorys w programie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Trigger> obiektów <xref:System.Windows.TriggerAction> i, aby zapoznać się z przykładem, zobacz [Używanie wyzwalaczy zdarzeń do kontrolowania scenorysu po jego uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="58f1b-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

<span data-ttu-id="58f1b-105">Aby uruchomić scenorys, należy użyć jego <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody, która dystrybuuje animacje scenorysu do właściwości, które są animowane i uruchamia scenorys.</span><span class="sxs-lookup"><span data-stu-id="58f1b-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>

<span data-ttu-id="58f1b-106">Aby można było sterować scenorysem, należy użyć <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody i określić **wartość true** jako drugi parametr.</span><span class="sxs-lookup"><span data-stu-id="58f1b-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="58f1b-107">Następnie możesz użyć interaktywnych metod, aby wstrzymywać, wznawiać, wyszukiwać, zatrzymywać, przyspieszyć lub spowalniać scenorys lub przełączać się do jego okresu wypełniania.</span><span class="sxs-lookup"><span data-stu-id="58f1b-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="58f1b-108">Poniżej znajduje się lista interaktywnych metod scenorysu:</span><span class="sxs-lookup"><span data-stu-id="58f1b-108">The following is a list of the storyboard's interactive methods:</span></span>

- <span data-ttu-id="58f1b-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Wstrzymuje scenorys.</span><span class="sxs-lookup"><span data-stu-id="58f1b-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>

- <span data-ttu-id="58f1b-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Wznawia wstrzymanie scenorysu.</span><span class="sxs-lookup"><span data-stu-id="58f1b-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="58f1b-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Ustawia szybkość interaktywną scenorysu.</span><span class="sxs-lookup"><span data-stu-id="58f1b-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>

- <span data-ttu-id="58f1b-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Wyszukuje scenorys w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="58f1b-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>

- <span data-ttu-id="58f1b-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Szuka scenorysu do określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="58f1b-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="58f1b-114">W przeciwieństwie <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> do metody, ta operacja jest przetwarzana przed następnym znacznikiem.</span><span class="sxs-lookup"><span data-stu-id="58f1b-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>

- <span data-ttu-id="58f1b-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Przesuwa scenorys do jego okresu wypełnienia, jeśli go zawiera.</span><span class="sxs-lookup"><span data-stu-id="58f1b-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>

- <span data-ttu-id="58f1b-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Powoduje zatrzymanie scenorysu.</span><span class="sxs-lookup"><span data-stu-id="58f1b-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>

<span data-ttu-id="58f1b-117">W poniższym przykładzie kilka metod scenorysu służy do interaktywnego sterowania scenorysem.</span><span class="sxs-lookup"><span data-stu-id="58f1b-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="58f1b-118">Aby zobaczyć przykład kontrolowania scenorysu przy użyciu wyzwalaczy z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], zobacz [Używanie wyzwalaczy zdarzeń do kontrolowania scenorysu po jego uruchomieniu](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="58f1b-118">To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

## <a name="example"></a><span data-ttu-id="58f1b-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="58f1b-119">Example</span></span>

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a><span data-ttu-id="58f1b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58f1b-120">See also</span></span>

- [<span data-ttu-id="58f1b-121">Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="58f1b-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
