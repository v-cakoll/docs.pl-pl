---
title: 'Instrukcje: Sterowanie elementem MediaElement z użyciem scenorysu'
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
ms.openlocfilehash: ae785e11b1da0f2c408b24021ad46ab071419378
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100317"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Instrukcje: Sterowanie elementem MediaElement z użyciem scenorysu
W tym przykładzie pokazano, jak kontrolować <xref:System.Windows.Controls.MediaElement> przy użyciu <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Przykład  
 Kiedy używasz <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard> kontrolować czas <xref:System.Windows.Controls.MediaElement>, funkcjonalność jest taka sama jak inne funkcje <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji. Na przykład <xref:System.Windows.Media.MediaTimeline> używa <xref:System.Windows.Media.Animation.Timeline> właściwości, takie jak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> właściwości w celu określenia, kiedy rozpoczyna <xref:System.Windows.Controls.MediaElement> (rozpoczęcia odtwarzania multimediów). Korzysta również <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości, aby określić, jak długo <xref:System.Windows.Controls.MediaElement> jest aktywna (czas trwania odtwarzania multimediów). Aby uzyskać więcej informacji o korzystaniu z <xref:System.Windows.Media.Animation.Timeline> obiekty z <xref:System.Windows.Media.Animation.Storyboard>, zobacz [Przegląd Scenorysy](storyboards-overview.md).  
  
 W tym przykładzie pokazano, jak utworzyć odtwarzacz multimediów prostego, który używa <xref:System.Windows.Media.MediaTimeline> Aby sterować odtwarzaniem. Usługa media player obejmuje sklepu play, wstrzymywanie, wznawianie i zatrzymywanie przycisków. Ma również odtwarzacz <xref:System.Windows.Controls.Slider> formant, który działa jako pasek postępu.  
  
 Poniższy przykład tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] programu media player.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Poniższy przykład tworzy funkcje pasek postępu.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [Przegląd Scenorysy](storyboards-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Przegląd Animacja](animation-overview.md)
- [— Tematy porad](audio-and-video-how-to-topics.md)
- [Grafika i multimedia](index.md)
