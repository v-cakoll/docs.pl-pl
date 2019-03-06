---
title: 'Instrukcje: Wyzwól odtwarzanie mediów za pomocą zdarzenia użytkownika'
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: 1d71e69bcd0332ba7119977dcf67356a3d79a368
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377979"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="2099b-102">Instrukcje: Wyzwól odtwarzanie mediów za pomocą zdarzenia użytkownika</span><span class="sxs-lookup"><span data-stu-id="2099b-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="2099b-103">Ten przykład pokazuje, jak synchronizowanie odtwarzania nośnika ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="2099b-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2099b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2099b-104">Example</span></span>  
 <span data-ttu-id="2099b-105">W poniższym przykładzie użyto <xref:System.Windows.Controls.MediaElement> kontroli i <xref:System.Windows.Media.MediaTimeline> klasy, aby odtworzyć dźwięk, który występuje, gdy użytkownik kliknie <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="2099b-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2099b-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2099b-106">See also</span></span>
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.EventTrigger.RoutedEvent%2A>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="2099b-107">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="2099b-107">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="2099b-108">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="2099b-108">Graphics and Multimedia</span></span>](index.md)
