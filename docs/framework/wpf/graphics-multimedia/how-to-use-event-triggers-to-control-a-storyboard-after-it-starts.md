---
title: 'Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: e0bc019ee361cba6a28ac573da3d2ee09e2168ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663298"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="2d812-102">Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="2d812-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="2d812-103">W tym przykładzie pokazano, jak kontrolować <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="2d812-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="2d812-104">Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard>, która dystrybuuje animacji do obiektów i właściwości, animować, a następnie uruchamia scenorysu.</span><span class="sxs-lookup"><span data-stu-id="2d812-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="2d812-105">Jeśli nadasz <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę, określając jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, możesz obejrzeć sterowane scenorysu.</span><span class="sxs-lookup"><span data-stu-id="2d812-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="2d812-106">Możesz następnie interaktywnie kontrolować scenorys po uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="2d812-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="2d812-107">Użyj następujących akcji scenorysu w połączeniu z <xref:System.Windows.EventTrigger> obiektów, aby kontrolować scenorys.</span><span class="sxs-lookup"><span data-stu-id="2d812-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
- <span data-ttu-id="2d812-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="2d812-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
- <span data-ttu-id="2d812-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.</span><span class="sxs-lookup"><span data-stu-id="2d812-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
- <span data-ttu-id="2d812-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.</span><span class="sxs-lookup"><span data-stu-id="2d812-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
- <span data-ttu-id="2d812-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorysu do końca okresu wypełnienia, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="2d812-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
- <span data-ttu-id="2d812-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Zatrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="2d812-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
- <span data-ttu-id="2d812-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu zwalnianiu zasobów.</span><span class="sxs-lookup"><span data-stu-id="2d812-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d812-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d812-114">Example</span></span>  
 <span data-ttu-id="2d812-115">W poniższym przykładzie użyto akcji musi scenorysu, aby interaktywnie kontrolować scenorys.</span><span class="sxs-lookup"><span data-stu-id="2d812-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="2d812-116">**Uwaga:** Aby zapoznać się przykładem kontrolowanie scenorysu przy użyciu kodu, zobacz [kontrolować Scenorys po jego rozpoczyna się przy użyciu jego metod interakcyjnych](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="2d812-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="2d812-117">Aby uzyskać więcej przykładów, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="2d812-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d812-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d812-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="2d812-119">Kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interakcyjnych</span><span class="sxs-lookup"><span data-stu-id="2d812-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="2d812-120">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="2d812-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2d812-121">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="2d812-121">Storyboards Overview</span></span>](storyboards-overview.md)
