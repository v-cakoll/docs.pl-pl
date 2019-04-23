---
title: 'Instrukcje: Odtwarzanie multimediów z animacjami'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 200f9d62c67a02088fe5a5789cdb41a04837d430
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079906"
---
# <a name="how-to-play-media-with-animations"></a>Instrukcje: Odtwarzanie multimediów z animacjami
W tym przykładzie pokazano, jak odtwarzanie multimediów i animacji w tym samym czasie za pomocą <xref:System.Windows.Media.MediaTimeline> i <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klas w tym samym <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Przykład  
 Można użyć co najmniej jeden <xref:System.Windows.Media.MediaTimeline> obiekty w <xref:System.Windows.Media.Animation.Storyboard> wraz z innymi <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.  
  
 Poniższy przykład ustawia <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Storyboard> wartości `Slip`, która określa, że animacja postępu do czasu trwania nośnika (klip wideo, w tym przykładzie). Ta funkcja może być pożądane, jeśli odtwarzania multimediów jest opóźnione z powodu czas ładowania.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [Tematy z instrukcjami](audio-and-video-how-to-topics.md)
- [Scenorysy — przegląd](storyboards-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animacja — przegląd](animation-overview.md)
- [Grafika i multimedia](index.md)
