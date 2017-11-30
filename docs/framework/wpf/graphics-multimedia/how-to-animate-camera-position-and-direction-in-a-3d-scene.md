---
title: "Jak animować położenie kamery i kierunek w scenie 3D"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 790260f974dcb0be398af202cc7156fc91efed91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Jak animować położenie kamery i kierunek w scenie 3D
Poniższy przykład pokazuje, jak animować pozycja kamery i animować kierunku, który wskazuje sceny 3W. Jest to zrobić za pomocą <xref:System.Windows.Media.Animation.Point3DAnimation> i <xref:System.Windows.Media.Animation.Vector3DAnimation> do animowania <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> właściwości odpowiednio <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Aby zmienić widok onlooker sceny w odpowiedzi na zdarzenia można użyć animacji następująco.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [Animowanie pozycji kamery i kierunek za pomocą klucza ramek](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
