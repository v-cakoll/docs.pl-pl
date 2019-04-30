---
title: 'Instrukcje: Animuj rotację 3D z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: e72ec94f830f0f5001a77e7492aa1326a47b309d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762153"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>Instrukcje: Animuj rotację 3D z wykorzystaniem klatek kluczowych
W poniższym przykładzie <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> jest używane do utworzenia obiektu 3D Obróć podczas jego osi obrotu animuje skutkuje "wobble". Ta animacja używa następujących klatek kluczowych:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> Służy do tworzenia płynne i liniowej interpolacji między wartościami.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> Służy do tworzenia nagłe "skoków" między wartościami (nie interpolacji).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> Służy do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> właściwości. W poniższym przykładzie ta część animacji rozpoczyna się poza powolne, ale w kierunku końca odcinka czasu, przyspiesza wykładniczo.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Grafika 3D — przegląd](3-d-graphics-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animowanie obrotu 3D przy użyciu scenorysów](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animowanie obrotu 3D przy użyciu kwaternionów](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animowanie obrotu 3D przy użyciu klatek kluczowych (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
