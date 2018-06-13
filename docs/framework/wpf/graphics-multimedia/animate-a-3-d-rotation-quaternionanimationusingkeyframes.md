---
title: Jak animować rotację 3-D z wykorzystaniem klatek kluczowych (QuaternionAnimationUsingKeyFrames)
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 59514dcd617f73cc8c8e458dc13880b3521c0fb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557072"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Jak animować rotację 3-D z wykorzystaniem klatek kluczowych (QuaternionAnimationUsingKeyFrames)
W poniższym przykładzie <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> używa w celu obracania obiektu 3D. Ta animacja używa następujących klatek kluczowych:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> Służy do tworzenia smooth, liniowy interpolacji między wartościami.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> Służy do tworzenia nagłym "skoków" między wartości (nie interpolacji).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> Służy do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> właściwości. W poniższym przykładzie ta część animacji rozpoczyna się poza powolne, ale do końca segmentu czasu, znacznie szybciej.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie obrotu 3D przy użyciu scenorysów](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animowanie obrotu 3D przy użyciu kwaternionów](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
