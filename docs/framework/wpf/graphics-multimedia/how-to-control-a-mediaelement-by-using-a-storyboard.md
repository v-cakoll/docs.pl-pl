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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Jak kontrolować MediaElement z użyciem scenorysu
Ten przykład pokazuje, jak sterować przy <xref:System.Windows.Controls.MediaElement> użyciu a <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> .  
  
## <a name="example"></a>Przykład  
 W przypadku korzystania z programu <xref:System.Windows.Media.MediaTimeline> w <xref:System.Windows.Media.Animation.Storyboard> celu kontrolowania chronometrażu elementu <xref:System.Windows.Controls.MediaElement> Funkcja jest taka sama jak w przypadku innych <xref:System.Windows.Media.Animation.Timeline> obiektów, takich jak animacje. Na przykład <xref:System.Windows.Media.MediaTimeline> stosuje właściwości, <xref:System.Windows.Media.Animation.Timeline> takie jak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Właściwość, aby określić, kiedy należy rozpocząć <xref:System.Windows.Controls.MediaElement> (Rozpocznij odtwarzanie nośnika). Używa również właściwości, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Aby określić, jak długo <xref:System.Windows.Controls.MediaElement> jest aktywny (czas trwania odtwarzania multimediów). Aby uzyskać więcej informacji o używaniu <xref:System.Windows.Media.Animation.Timeline> obiektów z <xref:System.Windows.Media.Animation.Storyboard> , zobacz [scenoryss — Omówienie](storyboards-overview.md).  
  
 Ten przykład przedstawia sposób tworzenia prostego odtwarzacza multimedialnego, który używa <xref:System.Windows.Media.MediaTimeline> do sterowania odtwarzaniem. Odtwarzacz multimedialny zawiera przyciski Odtwórz, Wstrzymaj, Wznów i Zatrzymaj. Gracz ma również <xref:System.Windows.Controls.Slider> kontrolkę, która działa jako pasek postępu.  
  
 Poniższy przykład tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dla odtwarzacza multimedialnego.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Poniższy przykład tworzy funkcję paska postępu.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [Przegląd Scenorysy](storyboards-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Przegląd Animacja](animation-overview.md)
- [— Tematy porad](audio-and-video-how-to-topics.md)
- [Grafika i multimedia](index.md)
