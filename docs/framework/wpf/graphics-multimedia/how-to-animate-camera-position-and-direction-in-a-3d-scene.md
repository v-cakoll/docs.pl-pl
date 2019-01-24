---
title: 'Instrukcje: Animuj położenie kamery i kierunek w scenie 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 18941f32de02b6e281df6c2c54c6c666dae63197
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564175"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Instrukcje: Animuj położenie kamery i kierunek w scenie 3D
Poniższy przykład pokazuje, jak animować położenie kamery i kierunek w scenie 3D wskazuje animować. Jest to wykonywane przy użyciu <xref:System.Windows.Media.Animation.Point3DAnimation> i <xref:System.Windows.Media.Animation.Vector3DAnimation> animować <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> właściwości odpowiednio <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Można użyć animacji, tak aby zmienić widok onlooker sceny w odpowiedzi na zdarzenie.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [Animowanie położenia kamery i kierunku z użyciem klatek kluczowych](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)
- [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
