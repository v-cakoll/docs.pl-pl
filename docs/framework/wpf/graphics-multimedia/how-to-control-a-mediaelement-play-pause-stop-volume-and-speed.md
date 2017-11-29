---
title: "Jak kontrolować MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7362c57afa3d5615ffaa0616823a954a2d577cfe
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Jak kontrolować MediaElement (odtwórz, pauza, zatrzymaj, głośność i prędkość)
Poniższy przykład przedstawia sposób odtwarzaniem nośnika przy użyciu <xref:System.Windows.Controls.MediaElement>. W przykładzie jest tworzony proste media player, który służy do odtwarzania, wstrzymać, zatrzymać i pominąć i z powrotem na nośniku, a także dopasować stosunek wolumin i szybkości.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy interfejsu użytkownika.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Właściwość <xref:System.Windows.Controls.MediaElement> musi mieć ustawioną `Manual` aby można było interaktywnie zatrzymać, wstrzymywanie i odtwarzanie multimediów.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje funkcje próbka formantów interfejsu użytkownika. <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, I <xref:System.Windows.Controls.MediaElement.Stop%2A> metody są używane do odpowiednio odtwarzania, wstrzymywanie i zatrzymywanie nośnika. Zmiana <xref:System.Windows.Controls.MediaElement.Position%2A> właściwość <xref:System.Windows.Controls.MediaElement> pozwala na pominięcie na nośniku. Na koniec <xref:System.Windows.Controls.MediaElement.Volume%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> właściwości są używane do dostosowywania woluminu i odtwarzania szybkość nośnika.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie MediaElement przy użyciu scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
