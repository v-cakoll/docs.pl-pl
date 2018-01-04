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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Jak kontrolować MediaElement z użyciem scenorysu
W tym przykładzie przedstawiono sposób kontrolowania <xref:System.Windows.Controls.MediaElement> za pomocą <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Przykład  
 Jeśli używasz <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard> Aby kontrolować czas <xref:System.Windows.Controls.MediaElement>, funkcjonalność jest taka sama jak funkcje oferowane przez <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji. Na przykład <xref:System.Windows.Media.MediaTimeline> używa <xref:System.Windows.Media.Animation.Timeline> właściwości, takie jak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> właściwości w celu określenia, kiedy należy uruchomić <xref:System.Windows.Controls.MediaElement> (Rozpocznij odtwarzanie multimediów). Również używa <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości, aby określić, jak długo <xref:System.Windows.Controls.MediaElement> jest aktywne (czas trwania odtwarzanie multimediów). Aby uzyskać więcej informacji o korzystaniu z <xref:System.Windows.Media.Animation.Timeline> obiekty z <xref:System.Windows.Media.Animation.Storyboard>, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 W tym przykładzie przedstawiono sposób tworzenia prostego media player, który używa <xref:System.Windows.Media.MediaTimeline> do sterowania odtwarzaniem. Media player zawiera play, wstrzymywanie, wznawianie i zatrzymywanie przycisków. Ma również odtwarzacz <xref:System.Windows.Controls.Slider> formant, który działa jako pasek postępu.  
  
 Poniższy przykład tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dla odtwarzacza multimedialnego.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Poniższy przykład tworzy funkcje pasek postępu.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
