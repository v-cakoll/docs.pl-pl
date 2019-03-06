---
title: 'Instrukcje: Odtwórz z nośnika z użyciem VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2397662c79af208f2528f6eedcd5995cfac9526c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363101"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="8769a-102">Instrukcje: Odtwórz z nośnika z użyciem VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="8769a-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="8769a-103">Odtwarzanie pliku audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="8769a-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="8769a-104">Istnieją dwa sposoby, aby załadować i odtwarzanie multimediów.</span><span class="sxs-lookup"><span data-stu-id="8769a-104">There are two ways to load and play media.</span></span> <span data-ttu-id="8769a-105">Pierwsza to użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi ze sposobów jest utworzenie własnych <xref:System.Windows.Media.MediaTimeline> za pomocą <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="8769a-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8769a-106">Podczas dystrybucji multimediów za pomocą aplikacji, nie można użyć pliku multimedialnego jako zasób projektu, tak jak w przypadku obrazu.</span><span class="sxs-lookup"><span data-stu-id="8769a-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="8769a-107">W pliku projektu, należy zamiast tego ustawić typ nośnika na `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.</span><span class="sxs-lookup"><span data-stu-id="8769a-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8769a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="8769a-108">Example</span></span>  
 <span data-ttu-id="8769a-109">W poniższym przykładzie użyto <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania pliku wideo, jeden raz.</span><span class="sxs-lookup"><span data-stu-id="8769a-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="8769a-110">Aby uzyskać dodatkowe chronometrażu kontrolę nad nośnika, należy użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="8769a-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="8769a-111"><xref:System.Windows.Media.MediaTimeline> Umożliwia określenie, czy należy powtórzyć filmu wideo.</span><span class="sxs-lookup"><span data-stu-id="8769a-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8769a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8769a-112">Example</span></span>  
 <span data-ttu-id="8769a-113">W poniższym przykładzie użyto <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów powtarzanie odtwarzania filmu wideo.</span><span class="sxs-lookup"><span data-stu-id="8769a-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="8769a-114">Należy zauważyć, że gdy używasz <xref:System.Windows.Media.MediaTimeline>, możesz użyć interakcyjnego <xref:System.Windows.Media.Animation.ClockController> zwróciło <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.MediaClock> Aby kontrolować odtwarzanie multimediów zamiast metod interaktywnych <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="8769a-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8769a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8769a-115">See also</span></span>
- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="8769a-116">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="8769a-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
