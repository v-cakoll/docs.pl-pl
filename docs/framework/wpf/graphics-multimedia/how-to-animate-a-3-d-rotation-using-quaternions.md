---
title: 'Jak: Animowanie obrotu 3D za pomocą kwaterników'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112248"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a>Jak: Animowanie obrotu 3D za pomocą kwaterników
W tym przykładzie pokazano, jak animować obrót obiektu 3D przy użyciu kwaterników.  
  
 Poniższy kod <xref:System.Windows.Media.Media3D.QuaternionRotation3D> przedstawia używany jako <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> wartość właściwości <xref:System.Windows.Media.Media3D.RotateTransform3D>. .  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Jest <xref:System.Windows.Media.Media3D.QuaternionRotation3D> to animowane <xref:System.Windows.Media.Animation.QuaternionAnimation> <xref:System.Windows.Media.Animation.Storyboard> z w ramach przy użyciu kodu poniżej.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia cały przykład.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Tworzenie sceny 3D](how-to-create-a-3-d-scene.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Przekształcenia — przegląd](transforms-overview.md)
- [Animowanie obrotu 3D za pomocą sceno-zoka](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
