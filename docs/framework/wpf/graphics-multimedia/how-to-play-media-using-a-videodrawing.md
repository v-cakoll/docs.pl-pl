---
title: 'Instrukcje: Odtwarzanie nośnika z użyciem elementu VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 186c9ae8167dafd09f029418c1d23f81f7a9e906
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203616"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="21b78-102">Instrukcje: Odtwarzanie nośnika z użyciem elementu VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="21b78-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="21b78-103">Odtwarzanie pliku audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="21b78-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="21b78-104">Istnieją dwa sposoby, aby załadować i odtwarzanie multimediów.</span><span class="sxs-lookup"><span data-stu-id="21b78-104">There are two ways to load and play media.</span></span> <span data-ttu-id="21b78-105">Pierwsza to użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi ze sposobów jest utworzenie własnych <xref:System.Windows.Media.MediaTimeline> za pomocą <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="21b78-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21b78-106">Podczas dystrybucji multimediów za pomocą aplikacji, nie można użyć pliku multimedialnego jako zasób projektu, tak jak w przypadku obrazu.</span><span class="sxs-lookup"><span data-stu-id="21b78-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="21b78-107">W pliku projektu, należy zamiast tego ustawić typ nośnika na `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.</span><span class="sxs-lookup"><span data-stu-id="21b78-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21b78-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="21b78-108">Example</span></span>  
 <span data-ttu-id="21b78-109">W poniższym przykładzie użyto <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania pliku wideo, jeden raz.</span><span class="sxs-lookup"><span data-stu-id="21b78-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="21b78-110">Aby uzyskać dodatkowe chronometrażu kontrolę nad nośnika, należy użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów.</span><span class="sxs-lookup"><span data-stu-id="21b78-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="21b78-111"><xref:System.Windows.Media.MediaTimeline> Umożliwia określenie, czy należy powtórzyć filmu wideo.</span><span class="sxs-lookup"><span data-stu-id="21b78-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21b78-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="21b78-112">Example</span></span>  
 <span data-ttu-id="21b78-113">W poniższym przykładzie użyto <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów powtarzanie odtwarzania filmu wideo.</span><span class="sxs-lookup"><span data-stu-id="21b78-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="21b78-114">Należy zauważyć, że gdy używasz <xref:System.Windows.Media.MediaTimeline>, możesz użyć interakcyjnego <xref:System.Windows.Media.Animation.ClockController> zwróciło <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.MediaClock> Aby kontrolować odtwarzanie multimediów zamiast metod interaktywnych <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="21b78-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b78-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21b78-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="21b78-116">Rysowanie obiektów — przegląd</span><span class="sxs-lookup"><span data-stu-id="21b78-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
