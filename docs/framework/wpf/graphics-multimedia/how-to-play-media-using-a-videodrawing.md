---
title: 'Instrukcje: Odtwórz z nośnika z użyciem VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 81f8dfc46dad07f34e50aac39e6cfde16de608a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644875"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Instrukcje: Odtwórz z nośnika z użyciem VideoDrawing
Odtwarzanie pliku audio lub wideo, należy użyć <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>. Istnieją dwa sposoby, aby załadować i odtwarzanie multimediów. Pierwsza to użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi ze sposobów jest utworzenie własnych <xref:System.Windows.Media.MediaTimeline> za pomocą <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Podczas dystrybucji multimediów za pomocą aplikacji, nie można użyć pliku multimedialnego jako zasób projektu, tak jak w przypadku obrazu. W pliku projektu, należy zamiast tego ustawić typ nośnika na `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania pliku wideo, jeden raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkowe chronometrażu kontrolę nad nośnika, należy użyć <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline> Umożliwia określenie, czy należy powtórzyć filmu wideo.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów powtarzanie odtwarzania filmu wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy zauważyć, że gdy używasz <xref:System.Windows.Media.MediaTimeline>, możesz użyć interakcyjnego <xref:System.Windows.Media.Animation.ClockController> zwróciło <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.MediaClock> Aby kontrolować odtwarzanie multimediów zamiast metod interaktywnych <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.VideoDrawing>
- [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
