---
title: 'Instrukcje: Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)'
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
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930161"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Instrukcje: Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)
Poniższy przykład pokazuje, <xref:System.Windows.Controls.MediaElement>jak sterować odtwarzaniem multimediów przy użyciu. W przykładzie tworzony jest prosty odtwarzacz multimedialny, który umożliwia odtwarzanie, wstrzymywanie, zatrzymywanie i pomijanie oraz przechodzenie do tyłu i z powrotem na nośniku, a także dostosowanie współczynnika głośności i szybkości.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy interfejs użytkownika.  
  
> [!NOTE]
> Właściwość musi być ustawiona na `Manual` , aby można było interaktywnie zatrzymać, wstrzymać i odtworzyć nośnik. <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje funkcjonalność przykładowych kontrolek interfejsu użytkownika. Metody <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, i<xref:System.Windows.Controls.MediaElement.Stop%2A> są używane odpowiednio do odtwarzania, wstrzymywania i zatrzymywania nośnika. <xref:System.Windows.Controls.MediaElement.Position%2A> Zmiana właściwości<xref:System.Windows.Controls.MediaElement> elementu umożliwia pominięcie na nośniku. Na <xref:System.Windows.Controls.MediaElement.Volume%2A> koniec właściwości i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> służą do dostosowywania głośności i szybkości odtwarzania nośnika.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Sterowanie elementem MediaElement z użyciem scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md)
