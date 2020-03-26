---
title: 'Jak: Animowanie obrotu 3D za pomocą klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112313"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a>Jak: Animowanie obrotu 3D za pomocą klatek kluczowych
W poniższym <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> przykładzie służy do obracania obiektu 3D, podczas gdy jego oś obrotu animuje się, co powoduje "chwiejność". Ta animacja używa następujących klatek kluczowych:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>służy do tworzenia płynnej, liniowej interpolacji między wartościami.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>służy do tworzenia nagłych "skoków" między wartościami (bez interpolacji).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>służy do tworzenia zmiennej przejścia między <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> wartościami w zależności od właściwości. W poniższym przykładzie ta część animacji zaczyna się powoli, ale pod koniec segmentu czasu, przyspiesza wykładniczo.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Animowanie obrotu 3D za pomocą sceno-zoka](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animowanie obrotu 3D przy użyciu kwaterników](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animowanie obrotu 3D przy użyciu klatek kluczowych (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
