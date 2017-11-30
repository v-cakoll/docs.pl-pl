---
title: "Jak odtworzyć z nośnika z użyciem VideoDrawing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2753db8e06c8c1b50c6e5cee17330d421e88511f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Jak odtworzyć z nośnika z użyciem VideoDrawing
Do odtwarzania pliku audio i wideo, użyj <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer>. Istnieją dwa sposoby do ładowania i odtwarzanie multimediów. Pierwsza to użycie <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> przez siebie, a drugi sposób polega na utworzeniu własnych <xref:System.Windows.Media.MediaTimeline> do użycia z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Do rozpowszechniania nośnika z aplikacji, nie można użyć pliku multimedialnego jako zasób projektu, jak w przypadku obrazu. W pliku projektu, należy zamiast tego ustawić typ nośnika `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VideoDrawing> i <xref:System.Windows.Media.MediaPlayer> do odtwarzania plików wideo raz.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać dodatkowe chronometrażu kontrolę nad nośnik, użyj <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów. <xref:System.Windows.Media.MediaTimeline> Umożliwia określenie, czy należy powtórzyć wideo.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.MediaTimeline> z <xref:System.Windows.Media.MediaPlayer> i <xref:System.Windows.Media.VideoDrawing> obiektów do odtwarzanie wideo.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Należy zauważyć, że gdy używasz <xref:System.Windows.Media.MediaTimeline>, możesz użyć interakcyjnego <xref:System.Windows.Media.Animation.ClockController> zwrócony z <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.MediaClock> odtwarzanie multimediów formantu zamiast metody interakcyjne <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.VideoDrawing>  
 [Rysowanie obiekty — omówienie](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
