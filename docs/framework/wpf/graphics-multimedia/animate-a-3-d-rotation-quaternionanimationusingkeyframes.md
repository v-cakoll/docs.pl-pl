---
title: 'Jak: Animowanie obrotu 3D za pomocą klatek kluczowych (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112300"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Jak: Animowanie obrotu 3D za pomocą klatek kluczowych (QuaternionAnimationUsingKeyFrames)
W poniższym <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> przykładzie jest używany do obracania obiektu 3D. Ta animacja używa następujących klatek kluczowych:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>służy do tworzenia płynnej, liniowej interpolacji między wartościami.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>służy do tworzenia nagłych "skoków" między wartościami (bez interpolacji).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>służy do tworzenia zmiennej przejścia między <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> wartościami w zależności od właściwości. W poniższym przykładzie ta część animacji zaczyna się powoli, ale pod koniec segmentu czasu, przyspiesza wykładniczo.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Animowanie obrotu 3D za pomocą sceno-zoka](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animowanie obrotu 3D przy użyciu kwaterników](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
