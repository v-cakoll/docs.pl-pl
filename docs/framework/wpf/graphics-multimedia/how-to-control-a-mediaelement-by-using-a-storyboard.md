---
title: Jak kontrolować MediaElement z użyciem scenorysu
description: Sterowanie odtwarzaniem multimediów przy użyciu scenorysu w programie Windows Presentation Foundation (WPF). Rozważmy ten przykład tworzenia prostego odtwarzacza multimedialnego.
ms.date: 03/30/2017
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
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853728"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="1bc2c-104">Jak kontrolować MediaElement z użyciem scenorysu</span><span class="sxs-lookup"><span data-stu-id="1bc2c-104">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="1bc2c-105">Ten przykład pokazuje, jak sterować przy <xref:System.Windows.Controls.MediaElement> użyciu a <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> .</span><span class="sxs-lookup"><span data-stu-id="1bc2c-105">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc2c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bc2c-106">Example</span></span>  
 <span data-ttu-id="1bc2c-107">W przypadku korzystania z programu <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard> celu kontrolowania chronometrażu elementu <xref:System.Windows.Controls.MediaElement> Funkcja jest taka sama jak w przypadku innych <xref:System.Windows.Media.Animation.Timeline> obiektów, takich jak animacje.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-107">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="1bc2c-108">Na przykład <xref:System.Windows.Media.MediaTimeline> stosuje właściwości, <xref:System.Windows.Media.Animation.Timeline> takie jak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Właściwość, aby określić, kiedy należy rozpocząć <xref:System.Windows.Controls.MediaElement> (Rozpocznij odtwarzanie nośnika).</span><span class="sxs-lookup"><span data-stu-id="1bc2c-108">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="1bc2c-109">Używa również właściwości, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Aby określić, jak długo <xref:System.Windows.Controls.MediaElement> jest aktywny (czas trwania odtwarzania multimediów).</span><span class="sxs-lookup"><span data-stu-id="1bc2c-109">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="1bc2c-110">Aby uzyskać więcej informacji o używaniu <xref:System.Windows.Media.Animation.Timeline> obiektów z <xref:System.Windows.Media.Animation.Storyboard> , zobacz [scenoryss — Omówienie](storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1bc2c-110">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="1bc2c-111">Ten przykład przedstawia sposób tworzenia prostego odtwarzacza multimedialnego, który używa <xref:System.Windows.Media.MediaTimeline> do sterowania odtwarzaniem.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-111">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="1bc2c-112">Odtwarzacz multimedialny zawiera przyciski Odtwórz, Wstrzymaj, Wznów i Zatrzymaj.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-112">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="1bc2c-113">Gracz ma również <xref:System.Windows.Controls.Slider> kontrolkę, która działa jako pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-113">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="1bc2c-114">Poniższy przykład tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dla odtwarzacza multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-114">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="1bc2c-115">Poniższy przykład tworzy funkcję paska postępu.</span><span class="sxs-lookup"><span data-stu-id="1bc2c-115">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1bc2c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bc2c-116">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="1bc2c-117">Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)</span><span class="sxs-lookup"><span data-stu-id="1bc2c-117">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="1bc2c-118">Przegląd Scenorysy</span><span class="sxs-lookup"><span data-stu-id="1bc2c-118">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="1bc2c-119">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="1bc2c-119">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1bc2c-120">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="1bc2c-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1bc2c-121">— Tematy porad</span><span class="sxs-lookup"><span data-stu-id="1bc2c-121">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="1bc2c-122">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="1bc2c-122">Graphics and Multimedia</span></span>](index.md)
