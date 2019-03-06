---
title: 'Instrukcje: Animuj rotację 3D z wykorzystaniem kwaternionów'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 079358ec12da803c8aa497bce1c272fa51f1c3b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368574"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a>Instrukcje: Animuj rotację 3D z wykorzystaniem kwaternionów
W tym przykładzie pokazano, jak animować rotację 3-D z wykorzystaniem kwaternionów obiektu.  
  
 Poniższy kod przedstawia <xref:System.Windows.Media.Media3D.QuaternionRotation3D> używany jako wartość <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwość <xref:System.Windows.Media.Media3D.RotateTransform3D>.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> jest animowany z <xref:System.Windows.Media.Animation.QuaternionAnimation> w ramach <xref:System.Windows.Media.Animation.Storyboard> przy użyciu kodu poniżej.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia całej próbki.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- [Animacja — przegląd](animation-overview.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
- [Animowanie obrotu 3D przy użyciu scenorysów](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
