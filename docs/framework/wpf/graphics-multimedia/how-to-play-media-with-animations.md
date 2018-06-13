---
title: Jak odtworzyć z nośnika z animacjami
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 21c9b35828dca03c05def11cff22f1f1e33d45cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560278"
---
# <a name="how-to-play-media-with-animations"></a>Jak odtworzyć z nośnika z animacjami
W tym przykładzie pokazano, jak odtwarzanie multimediów i animacji w tym samym czasie przy użyciu <xref:System.Windows.Media.MediaTimeline> i <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klas w tym samym <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Przykład  
 Można użyć co najmniej jeden <xref:System.Windows.Media.MediaTimeline> obiekty w <xref:System.Windows.Media.Animation.Storyboard> wraz z innymi <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Storyboard> wartość `Slip`, który określa, że animacja nie postępu aż do realizowany nośnika (klip wideo w tym przykładzie). Ta funkcja może być konieczna, jeśli odtwarzanie multimediów jest opóźnione z powodu czasu ładowania.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafika i multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
