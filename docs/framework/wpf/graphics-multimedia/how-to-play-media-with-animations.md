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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921670"
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="6c15f-102">Instrukcje: Odtwarzanie multimediów z animacjami</span><span class="sxs-lookup"><span data-stu-id="6c15f-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="6c15f-103">W tym przykładzie pokazano, jak odtwarzanie multimediów i animacji w tym samym czasie za pomocą <xref:System.Windows.Media.MediaTimeline> i <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klas w tym samym <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="6c15f-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c15f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c15f-104">Example</span></span>  
 <span data-ttu-id="6c15f-105">Można użyć co najmniej jeden <xref:System.Windows.Media.MediaTimeline> obiekty w <xref:System.Windows.Media.Animation.Storyboard> wraz z innymi <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.</span><span class="sxs-lookup"><span data-stu-id="6c15f-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="6c15f-106">Poniższy przykład ustawia <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Storyboard> wartości `Slip`, która określa, że animacja postępu do czasu trwania nośnika (klip wideo, w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="6c15f-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="6c15f-107">Ta funkcja może być pożądane, jeśli odtwarzania multimediów jest opóźnione z powodu czas ładowania.</span><span class="sxs-lookup"><span data-stu-id="6c15f-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6c15f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c15f-108">See also</span></span>

- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [<span data-ttu-id="6c15f-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6c15f-109">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="6c15f-110">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="6c15f-110">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="6c15f-111">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="6c15f-111">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="6c15f-112">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="6c15f-112">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="6c15f-113">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="6c15f-113">Graphics and Multimedia</span></span>](index.md)
