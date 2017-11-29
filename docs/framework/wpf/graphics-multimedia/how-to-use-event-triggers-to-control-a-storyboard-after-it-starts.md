---
title: "Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="947a6-102">Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu</span><span class="sxs-lookup"><span data-stu-id="947a6-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="947a6-103">W tym przykładzie przedstawiono sposób kontrolowania <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="947a6-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="947a6-104">Aby uruchomić <xref:System.Windows.Media.Animation.Storyboard> za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard>, która dystrybuuje animacje obiektów i właściwości animacji i następnie uruchamia scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="947a6-105">Jeśli zostanie nadana <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę przez określenie jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, można ustawić, którymi można sterować scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="947a6-106">Użytkownik może interakcyjnie wybrać scenorysu po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="947a6-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="947a6-107">Użyj następujących akcji scenorysu razem z <xref:System.Windows.EventTrigger> obiekty do kontrolowania scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="947a6-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="947a6-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="947a6-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="947a6-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorysu do końca okresu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="947a6-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="947a6-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Przestaje scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="947a6-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu, zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="947a6-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="947a6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="947a6-114">Example</span></span>  
 <span data-ttu-id="947a6-115">W poniższym przykładzie użyto akcji sterowane scenorysu do sterowania interaktywnego scenorysu.</span><span class="sxs-lookup"><span data-stu-id="947a6-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="947a6-116">**Uwaga:** Aby zapoznać się przykładem kontrolowanie scenorysu przy użyciu kodu, zobacz [kontrolować scenorysu po jego rozpoczyna się za pomocą jego interakcyjne metod](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="947a6-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="947a6-117">Aby uzyskać dodatkowe przykłady, zobacz [galerii przykład animacji](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="947a6-117">For additional examples, see the [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947a6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="947a6-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="947a6-119">Kontrolowanie scenorysu po uruchomieniu, za pomocą jej metod interakcyjne</span><span class="sxs-lookup"><span data-stu-id="947a6-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="947a6-120">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="947a6-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="947a6-121">Scenorys — omówienie</span><span class="sxs-lookup"><span data-stu-id="947a6-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
