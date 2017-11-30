---
title: "Jak animować rotację 3-D z wykorzystaniem klatek kluczowych (QuaternionAnimationUsingKeyFrames)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61968c13d395187d1190c7a2eaaa2bfe3f6072e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Jak animować rotację 3-D z wykorzystaniem klatek kluczowych (QuaternionAnimationUsingKeyFrames)
W poniższym przykładzie <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> używa w celu obracania obiektu 3D. Ta animacja używa następujących klatek kluczowych:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>Służy do tworzenia smooth, liniowy interpolacji między wartościami.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>Służy do tworzenia nagłym "skoków" między wartości (nie interpolacji).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>Służy do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> właściwości. W poniższym przykładzie ta część animacji rozpoczyna się poza powolne, ale do końca segmentu czasu, znacznie szybciej.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie obrót 3-w przy użyciu Scenorys](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Animowanie obrót 3-w przy użyciu Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animowanie obrót 3-w przy użyciu Quaternions](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [Animowanie obrót 3-w przy użyciu klucza ramek (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Omówienie klucza poklatkowych](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
