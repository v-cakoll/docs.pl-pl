---
title: 'Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855850"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="14ee5-102">Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="14ee5-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="14ee5-103">Ten przykład pokazuje, <xref:System.Windows.Media.Animation.Storyboard> jak kontrolować po rozpoczęciu.</span><span class="sxs-lookup"><span data-stu-id="14ee5-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="14ee5-104">Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> od przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programu, <xref:System.Windows.Media.Animation.BeginStoryboard>należy użyć, który dystrybuuje animacje do obiektów i właściwości, które są animowane, a następnie uruchamia scenorys.</span><span class="sxs-lookup"><span data-stu-id="14ee5-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="14ee5-105">W przypadku nadania <xref:System.Windows.Media.Animation.BeginStoryboard> nazwy przez określenie jej <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości można ją przetworzyć w scenorysie.</span><span class="sxs-lookup"><span data-stu-id="14ee5-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="14ee5-106">Następnie możesz interaktywnie kontrolować scenorys po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="14ee5-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="14ee5-107">Użyj następujących działań scenorysu razem z <xref:System.Windows.EventTrigger> obiektami, aby sterować scenorysem.</span><span class="sxs-lookup"><span data-stu-id="14ee5-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="14ee5-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorys.</span><span class="sxs-lookup"><span data-stu-id="14ee5-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="14ee5-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia wstrzymanie scenorysu.</span><span class="sxs-lookup"><span data-stu-id="14ee5-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="14ee5-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.</span><span class="sxs-lookup"><span data-stu-id="14ee5-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="14ee5-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorys do końca jego okresu wypełniania, jeśli go zawiera.</span><span class="sxs-lookup"><span data-stu-id="14ee5-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="14ee5-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Powoduje zatrzymanie scenorysu.</span><span class="sxs-lookup"><span data-stu-id="14ee5-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="14ee5-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorys, zwalniając zasoby.</span><span class="sxs-lookup"><span data-stu-id="14ee5-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="14ee5-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="14ee5-114">Example</span></span>

<span data-ttu-id="14ee5-115">W poniższym przykładzie są stosowane kontrolowane akcje scenorysu do interaktywnej kontroli scenorysu.</span><span class="sxs-lookup"><span data-stu-id="14ee5-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="14ee5-116">Aby zobaczyć przykład kontrolowania scenorysu przy użyciu kodu, zobacz [kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interaktywnych](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="14ee5-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="14ee5-117">Więcej przykładów można znaleźć w [galerii przykładowej animacji](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="14ee5-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

## <a name="see-also"></a><span data-ttu-id="14ee5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14ee5-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="14ee5-119">Kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interakcyjnych</span><span class="sxs-lookup"><span data-stu-id="14ee5-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="14ee5-120">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="14ee5-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="14ee5-121">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="14ee5-121">Storyboards Overview</span></span>](storyboards-overview.md)
