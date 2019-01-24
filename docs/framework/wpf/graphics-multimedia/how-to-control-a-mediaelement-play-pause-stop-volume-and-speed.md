---
title: 'Instrukcje: Kontroluj MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)'
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
ms.openlocfilehash: e9939c2d3d740bfe9296c23e47ef8ea09d837e01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498924"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Instrukcje: Kontroluj MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)
Poniższy przykład pokazuje, jak kontrolować odtwarzanie multimediów za pomocą <xref:System.Windows.Controls.MediaElement>. Ten przykład tworzy prostą media player, który umożliwia odtwarzanie, wstrzymywanie, zatrzymać i przejdź do i z powrotem na nośniku, a także dostosować współczynnik wielkość i szybkość.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy interfejsu użytkownika.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Właściwość <xref:System.Windows.Controls.MediaElement> musi być równa `Manual` aby można było interaktywnie zatrzymać, wstrzymać, a odtwarzanie nośnika.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje funkcje przykładowe kontrolek interfejsu użytkownika. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, I <xref:System.Windows.Controls.MediaElement.Stop%2A> metody są używane do odpowiednio odtwarzania, wstrzymać lub zatrzymać nośnika. Zmiana <xref:System.Windows.Controls.MediaElement.Position%2A> właściwość <xref:System.Windows.Controls.MediaElement> umożliwia pomijanie na nośniku. Na koniec <xref:System.Windows.Controls.MediaElement.Volume%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> właściwości są używane, aby dostosować szybkość woluminu i odtwarzanie nośnika.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Sterowanie elementem MediaElement z użyciem scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
