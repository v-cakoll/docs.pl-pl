---
title: "Jak odtworzyć z nośnika z animacjami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44ebb89c25fc37292f82533c929aae44854db5c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="231b1-102">Jak odtworzyć z nośnika z animacjami</span><span class="sxs-lookup"><span data-stu-id="231b1-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="231b1-103">W tym przykładzie pokazano, jak odtwarzanie multimediów i animacji w tym samym czasie przy użyciu <xref:System.Windows.Media.MediaTimeline> i <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klas w tym samym <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="231b1-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="231b1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="231b1-104">Example</span></span>  
 <span data-ttu-id="231b1-105">Można użyć co najmniej jeden <xref:System.Windows.Media.MediaTimeline> obiekty w <xref:System.Windows.Media.Animation.Storyboard> wraz z innymi <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.</span><span class="sxs-lookup"><span data-stu-id="231b1-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="231b1-106">W poniższym przykładzie <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Storyboard> wartość `Slip`, który określa, że animacja nie postępu aż do realizowany nośnika (klip wideo w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="231b1-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="231b1-107">Ta funkcja może być konieczna, jeśli odtwarzanie multimediów jest opóźnione z powodu czasu ładowania.</span><span class="sxs-lookup"><span data-stu-id="231b1-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="231b1-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="231b1-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="231b1-109">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="231b1-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="231b1-110">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="231b1-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="231b1-111">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="231b1-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="231b1-112">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="231b1-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="231b1-113">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="231b1-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
