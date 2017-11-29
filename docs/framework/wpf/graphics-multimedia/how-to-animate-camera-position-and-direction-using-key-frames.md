---
title: "Jak animować położenie kamery i kierunek z użyciem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbac99770b5cbb7dacb0468e1a892956fda6b79c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Jak animować położenie kamery i kierunek z użyciem klatek kluczowych
W poniższym przykładzie <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> służy do animowania pozycja <xref:System.Windows.Media.Media3D.PerspectiveCamera> sceny 3W. Ponadto <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> służy do animowania kierunek wskazuje aparatu w scenę 3D. Oba te animacje użyć kilku klatek kluczowych, co spowoduje utworzenie serii efekty animacji:  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>i <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> są używane do tworzenia smooth, liniowy interpolacji między wartościami.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>i <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> są używane do tworzenia nagłym "skoków" między wartości (nie interpolacji).  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>i <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> są używane do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> właściwości. W poniższym przykładzie animacji rozpoczyna się poza powolne, ale do końca segmentu czasu, znacznie szybciej.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie pozycji kamery i kierunek scenę 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
