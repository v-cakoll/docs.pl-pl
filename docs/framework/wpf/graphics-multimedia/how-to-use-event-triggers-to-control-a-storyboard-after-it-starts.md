---
title: 'Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d444349f8bc9236e1d15f484f35b1326c77e2425
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170654"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="e8d8e-102">Instrukcje: Sterowanie scenorysem po uruchomieniu przy użyciu wyzwalaczy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e8d8e-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="e8d8e-103">W tym przykładzie pokazano, jak kontrolować <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="e8d8e-104">Aby rozpocząć <xref:System.Windows.Media.Animation.Storyboard> przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard>, która dystrybuuje animacji do obiektów i właściwości, animować, a następnie uruchamia scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="e8d8e-105">Jeśli nadasz <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę, określając jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, możesz obejrzeć sterowane scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="e8d8e-106">Możesz następnie interaktywnie kontrolować scenorys po uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="e8d8e-107">Użyj następujących akcji scenorysu w połączeniu z <xref:System.Windows.EventTrigger> obiektów, aby kontrolować scenorys.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard><span data-ttu-id="e8d8e-108">: Wstrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-108">: Pauses the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard><span data-ttu-id="e8d8e-109">: Wznawia działanie wstrzymanej scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-109">: Resumes a paused storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio><span data-ttu-id="e8d8e-110">: Zmienia szybkość scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-110">: Changes the storyboard speed.</span></span>  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill><span data-ttu-id="e8d8e-111">: Przesuwa scenorysu do końca okresu wypełnienia, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-111">: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard><span data-ttu-id="e8d8e-112">: Zatrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-112">: Stops the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard><span data-ttu-id="e8d8e-113">: Usuwa scenorysu zwalnianiu zasobów.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-113">: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8d8e-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8d8e-114">Example</span></span>  
 <span data-ttu-id="e8d8e-115">W poniższym przykładzie użyto akcji musi scenorysu, aby interaktywnie kontrolować scenorys.</span><span class="sxs-lookup"><span data-stu-id="e8d8e-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="e8d8e-116">**Uwaga:** Aby zapoznać się przykładem kontrolowanie scenorysu przy użyciu kodu, zobacz [kontrolować Scenorys po jego rozpoczyna się przy użyciu jego metod interakcyjnych](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="e8d8e-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="e8d8e-117">Aby uzyskać więcej przykładów, zobacz [galerii przykład animacji](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="e8d8e-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d8e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8d8e-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="e8d8e-119">Kontrolowanie scenorysu po uruchomieniu przy użyciu jego metod interakcyjnych</span><span class="sxs-lookup"><span data-stu-id="e8d8e-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="e8d8e-120">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="e8d8e-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e8d8e-121">Przegląd Scenorysy</span><span class="sxs-lookup"><span data-stu-id="e8d8e-121">Storyboards Overview</span></span>](storyboards-overview.md)
