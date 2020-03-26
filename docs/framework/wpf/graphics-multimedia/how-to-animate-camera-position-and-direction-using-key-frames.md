---
title: Jak animować położenie kamery i kierunek z użyciem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112170"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Jak animować położenie kamery i kierunek z użyciem klatek kluczowych
W poniższym <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> przykładzie jest używany do <xref:System.Windows.Media.Media3D.PerspectiveCamera> animowania pozycji w scenie 3D. Ponadto służy <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> do animowania kierunku, w jakim kamera wskazuje w scenie 3D. Obie te animacje używają kilku klatek kluczowych, które tworzą serię efektów animacji:  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>i <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> są używane do tworzenia płynnej, liniowej interpolacji między wartościami.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>i <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> są używane do tworzenia nagłych "skoków" między wartościami (bez interpolacji).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>i <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> są używane do tworzenia zmiennej <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> przejścia między wartościami w zależności od właściwości. W poniższym przykładzie animacja rozpoczyna się powoli, ale pod koniec segmentu czasu, przyspiesza wykładniczo.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Animowanie położenia kamery i kierunku w scenie 3D](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
