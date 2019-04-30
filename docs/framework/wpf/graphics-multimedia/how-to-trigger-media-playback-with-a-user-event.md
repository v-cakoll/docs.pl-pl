---
title: 'Instrukcje: Wyzwalanie odtwarzania multimediów za pomocą zdarzenia użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: ae8ba54cc852bb85350492c95e3e890aebf6534f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769281"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a>Instrukcje: Wyzwalanie odtwarzania multimediów za pomocą zdarzenia użytkownika
Ten przykład pokazuje, jak synchronizowanie odtwarzania nośnika ze zdarzeniem.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Controls.MediaElement> kontroli i <xref:System.Windows.Media.MediaTimeline> klasy, aby odtworzyć dźwięk, który występuje, gdy użytkownik kliknie <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.EventTrigger.RoutedEvent%2A>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Tematy z instrukcjami](audio-and-video-how-to-topics.md)
- [Grafika i multimedia](index.md)
