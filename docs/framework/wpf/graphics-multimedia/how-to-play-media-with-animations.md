---
title: 'Instrukcje: Odtwórz z nośnika z animacjami'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: e6a011b1fa6f3551c3570370247fbae262b20e4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594255"
---
# <a name="how-to-play-media-with-animations"></a>Instrukcje: Odtwórz z nośnika z animacjami
W tym przykładzie pokazano, jak odtwarzanie multimediów i animacji w tym samym czasie za pomocą <xref:System.Windows.Media.MediaTimeline> i <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klas w tym samym <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Przykład  
 Można użyć co najmniej jeden <xref:System.Windows.Media.MediaTimeline> obiekty w <xref:System.Windows.Media.Animation.Storyboard> wraz z innymi <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.  
  
 Poniższy przykład ustawia <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Storyboard> wartości `Slip`, która określa, że animacja postępu do czasu trwania nośnika (klip wideo, w tym przykładzie). Ta funkcja może być pożądane, jeśli odtwarzania multimediów jest opóźnione z powodu czas ładowania.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
- [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
- [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
