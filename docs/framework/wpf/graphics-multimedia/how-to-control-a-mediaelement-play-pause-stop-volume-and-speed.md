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
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984049"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Instrukcje: Sterowanie elementem MediaElement (odtwórz, pauza, zatrzymaj, głośność i szybkość)
Poniższy przykład pokazuje, jak kontrolować odtwarzanie multimediów za pomocą <xref:System.Windows.Controls.MediaElement>. Ten przykład tworzy prostą media player, który umożliwia odtwarzanie, wstrzymywanie, zatrzymać i przejdź do i z powrotem na nośniku, a także dostosować współczynnik wielkość i szybkość.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy interfejsu użytkownika.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Właściwość <xref:System.Windows.Controls.MediaElement> musi być równa `Manual` aby można było interaktywnie zatrzymać, wstrzymać, a odtwarzanie nośnika.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje funkcje przykładowe kontrolek interfejsu użytkownika. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, I <xref:System.Windows.Controls.MediaElement.Stop%2A> metody są używane do odpowiednio odtwarzania, wstrzymać lub zatrzymać nośnika. Zmiana <xref:System.Windows.Controls.MediaElement.Position%2A> właściwość <xref:System.Windows.Controls.MediaElement> umożliwia pomijanie na nośniku. Na koniec <xref:System.Windows.Controls.MediaElement.Volume%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> właściwości są używane, aby dostosować szybkość woluminu i odtwarzanie nośnika.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Sterowanie elementem MediaElement z użyciem scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md)
