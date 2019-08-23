---
title: 'Instrukcje: Odtwarzanie nośnika z użyciem elementu VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956954"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="ac568-102">Instrukcje: Odtwarzanie nośnika z użyciem elementu VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="ac568-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="ac568-103">Aby odtworzyć plik audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>i.</span><span class="sxs-lookup"><span data-stu-id="ac568-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="ac568-104">Istnieją dwa sposoby ładowania i odtwarzania multimediów.</span><span class="sxs-lookup"><span data-stu-id="ac568-104">There are two ways to load and play media.</span></span> <span data-ttu-id="ac568-105">Pierwszym sposobem <xref:System.Windows.Media.MediaPlayer> jest użycie <xref:System.Windows.Media.VideoDrawing> i a przez siebie, a drugi — tworzenie <xref:System.Windows.Media.MediaPlayer> własnych <xref:System.Windows.Media.MediaTimeline> do użycia z i <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="ac568-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac568-106">Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu, takiego jak obraz.</span><span class="sxs-lookup"><span data-stu-id="ac568-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="ac568-107">W pliku projektu należy zamiast tego ustawić `Content` typ nośnika na i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always`.</span><span class="sxs-lookup"><span data-stu-id="ac568-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac568-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac568-108">Example</span></span>  
 <span data-ttu-id="ac568-109">Poniższy przykład używa <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> i, aby odtworzyć plik wideo jeden raz.</span><span class="sxs-lookup"><span data-stu-id="ac568-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="ac568-110">Aby uzyskać dodatkową kontrolę czasu na nośniku, użyj <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> z i <xref:System.Windows.Media.VideoDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ac568-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="ac568-111"><xref:System.Windows.Media.MediaTimeline> Pozwala określić, czy film wideo powinien być powtarzany.</span><span class="sxs-lookup"><span data-stu-id="ac568-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac568-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac568-112">Example</span></span>  
 <span data-ttu-id="ac568-113">W poniższym przykładzie zastosowano <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> obiekty i, <xref:System.Windows.Media.VideoDrawing> aby kilkukrotnie odtworzyć film wideo.</span><span class="sxs-lookup"><span data-stu-id="ac568-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="ac568-114">Należy pamiętać, że w przypadku korzystania <xref:System.Windows.Media.MediaTimeline>z programu można użyć interaktywnego <xref:System.Windows.Media.Animation.ClockController> powrotu <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwości do sterowania odtwarzaniem multimediów zamiast interaktywnych metod <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="ac568-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac568-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac568-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="ac568-116">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="ac568-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
