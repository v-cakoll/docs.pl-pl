---
title: 'Instrukcje: Animowanie położenia kamery i kierunku z użyciem klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 44464cc314d649516998338e36c1b523101ac4e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651340"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Instrukcje: Animowanie położenia kamery i kierunku z użyciem klatek kluczowych
W poniższym przykładzie <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> służy do animowanie położenia <xref:System.Windows.Media.Media3D.PerspectiveCamera> w scenie 3D. Ponadto <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> służy do animowanie kierunku kamery wskazuje w scenie 3D. Oba te animacji użyć kilku klatek kluczowych, które tworzą szereg efektów animacji:  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> i <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> są używane do tworzenia płynne i liniowej interpolacji między wartościami.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> i <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> są używane do tworzenia nagłe "skoków" między wartościami (nie interpolacji).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> i <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> są używane do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> właściwości. W poniższym przykładzie animacji rozpoczyna się poza powolne, ale w kierunku końca odcinka czasu, przyspiesza wykładniczo.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie położenia kamery i kierunku w scenie 3D](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
