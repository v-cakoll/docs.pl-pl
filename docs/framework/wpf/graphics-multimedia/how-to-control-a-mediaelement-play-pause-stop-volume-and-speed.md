---
title: Jak kontrolować MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)
description: Sterowanie odtwarzaniem multimediów w programie Windows Presentation Foundation (WPF). Uruchamianie, zatrzymywanie, wstrzymywanie, pomijanie z tyłu i do przodu oraz dostosowywanie głośności i szybkości.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: da846299eaa1e36b6e5caab08bc1f861e9f9c46d
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853597"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Jak kontrolować MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)
Poniższy przykład pokazuje, jak sterować odtwarzaniem multimediów przy użyciu <xref:System.Windows.Controls.MediaElement> . W przykładzie tworzony jest prosty odtwarzacz multimedialny, który umożliwia odtwarzanie, wstrzymywanie, zatrzymywanie i pomijanie oraz przechodzenie do tyłu i z powrotem na nośniku, a także dostosowanie współczynnika głośności i szybkości.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy interfejs użytkownika.  
  
> [!NOTE]
> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>Właściwość <xref:System.Windows.Controls.MediaElement> musi być ustawiona na, aby `Manual` można było interaktywnie zatrzymać, wstrzymać i odtworzyć nośnik.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje funkcjonalność przykładowych kontrolek interfejsu użytkownika. <xref:System.Windows.Controls.MediaElement.Play%2A>Metody, <xref:System.Windows.Controls.MediaElement.Pause%2A> , i <xref:System.Windows.Controls.MediaElement.Stop%2A> są używane odpowiednio do odtwarzania, wstrzymywania i zatrzymywania nośnika. Zmiana <xref:System.Windows.Controls.MediaElement.Position%2A> właściwości elementu <xref:System.Windows.Controls.MediaElement> umożliwia pominięcie na nośniku. Na koniec <xref:System.Windows.Controls.MediaElement.Volume%2A> właściwości i służą <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> do dostosowywania głośności i szybkości odtwarzania nośnika.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Sterowanie elementem MediaElement z użyciem scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md)
