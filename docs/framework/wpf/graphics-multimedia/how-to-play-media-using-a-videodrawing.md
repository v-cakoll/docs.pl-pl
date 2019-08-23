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
# <a name="how-to-play-media-using-a-videodrawing"></a>Instrukcje: Odtwarzanie nośnika z użyciem elementu VideoDrawing
Aby odtworzyć plik audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>i. Istnieją dwa sposoby ładowania i odtwarzania multimediów. Pierwszym sposobem <xref:System.Windows.Media.MediaPlayer> jest użycie <xref:System.Windows.Media.VideoDrawing> i a przez siebie, a drugi — tworzenie <xref:System.Windows.Media.MediaPlayer> własnych <xref:System.Windows.Media.MediaTimeline> do użycia z i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
> Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu, takiego jak obraz. W pliku projektu należy zamiast tego ustawić `Content` typ nośnika na i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer> i, aby odtworzyć plik wideo jeden raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkową kontrolę czasu na nośniku, użyj <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> z i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline> Pozwala określić, czy film wideo powinien być powtarzany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> obiekty i, <xref:System.Windows.Media.VideoDrawing> aby kilkukrotnie odtworzyć film wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy pamiętać, że w przypadku korzystania <xref:System.Windows.Media.MediaTimeline>z programu można użyć interaktywnego <xref:System.Windows.Media.Animation.ClockController> powrotu <xref:System.Windows.Media.MediaClock> z <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwości do sterowania odtwarzaniem multimediów zamiast interaktywnych metod <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.VideoDrawing>
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
