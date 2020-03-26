---
title: Jak animować położenie kamery i kierunek w scenie 3D
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112217"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Jak animować położenie kamery i kierunek w scenie 3D
W poniższym przykładzie pokazano, jak animować położenie kamery i animować kierunek, w jakim jest ona skierowana w scenie 3D. Odbywa się to <xref:System.Windows.Media.Animation.Point3DAnimation> <xref:System.Windows.Media.Animation.Vector3DAnimation> za pomocą <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> animować i <xref:System.Windows.Media.Media3D.PerspectiveCamera>właściwości odpowiednio . Możesz użyć animacji takiej jak ta, aby zmienić widok obserwatora sceny w odpowiedzi na zdarzenie.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [Animowanie położenia kamery i kierunku z użyciem klatek kluczowych](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
