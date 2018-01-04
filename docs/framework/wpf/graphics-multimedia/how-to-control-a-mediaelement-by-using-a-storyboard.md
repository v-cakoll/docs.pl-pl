---
title: "Jak kontrolować MediaElement z użyciem scenorysu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f52801ee3704c13ec5213cfc54b6392baa97e245
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="e7b52-102">Jak kontrolować MediaElement z użyciem scenorysu</span><span class="sxs-lookup"><span data-stu-id="e7b52-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="e7b52-103">W tym przykładzie przedstawiono sposób kontrolowania <xref:System.Windows.Controls.MediaElement> za pomocą <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="e7b52-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7b52-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7b52-104">Example</span></span>  
 <span data-ttu-id="e7b52-105">Jeśli używasz <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard> Aby kontrolować czas <xref:System.Windows.Controls.MediaElement>, funkcjonalność jest taka sama jak funkcje oferowane przez <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.</span><span class="sxs-lookup"><span data-stu-id="e7b52-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="e7b52-106">Na przykład <xref:System.Windows.Media.MediaTimeline> używa <xref:System.Windows.Media.Animation.Timeline> właściwości, takie jak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> właściwości w celu określenia, kiedy należy uruchomić <xref:System.Windows.Controls.MediaElement> (Rozpocznij odtwarzanie multimediów).</span><span class="sxs-lookup"><span data-stu-id="e7b52-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="e7b52-107">Również używa <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości, aby określić, jak długo <xref:System.Windows.Controls.MediaElement> jest aktywne (czas trwania odtwarzanie multimediów).</span><span class="sxs-lookup"><span data-stu-id="e7b52-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="e7b52-108">Aby uzyskać więcej informacji o korzystaniu z <xref:System.Windows.Media.Animation.Timeline> obiekty z <xref:System.Windows.Media.Animation.Storyboard>, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7b52-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="e7b52-109">W tym przykładzie przedstawiono sposób tworzenia prostego media player, który używa <xref:System.Windows.Media.MediaTimeline> do sterowania odtwarzaniem.</span><span class="sxs-lookup"><span data-stu-id="e7b52-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="e7b52-110">Media player zawiera play, wstrzymywanie, wznawianie i zatrzymywanie przycisków.</span><span class="sxs-lookup"><span data-stu-id="e7b52-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="e7b52-111">Ma również odtwarzacz <xref:System.Windows.Controls.Slider> formant, który działa jako pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="e7b52-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="e7b52-112">Poniższy przykład tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dla odtwarzacza multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="e7b52-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="e7b52-113">Poniższy przykład tworzy funkcje pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="e7b52-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e7b52-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7b52-114">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="e7b52-115">Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)</span><span class="sxs-lookup"><span data-stu-id="e7b52-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [<span data-ttu-id="e7b52-116">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="e7b52-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="e7b52-117">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="e7b52-117">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="e7b52-118">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="e7b52-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e7b52-119">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e7b52-119">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="e7b52-120">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="e7b52-120">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
