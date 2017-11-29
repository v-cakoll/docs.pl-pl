---
title: "Jak animować rotację 3-D z wykorzystaniem scenorysów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56839dfc5382f5dd56ec0b26d4aabe42536bf04e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Jak animować rotację 3-D z wykorzystaniem scenorysów
Poniższy przykład przedstawia sposób obiektu 3D, obracanie podczas jego "wobbles" przez animację <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu. To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu określa przekształcenia obrotu 3W obiektu i dlatego animowania właściwości tworzy efektu obrotu desire. W ramach scenorysu <xref:System.Windows.Media.Animation.DoubleAnimation> służy do animowania <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości podczas <xref:System.Windows.Media.Animation.Vector3DAnimation> służy do animowania <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie obrót 3-w przy użyciu Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animowanie obrót 3-w przy użyciu klucza ramek (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [Przegląd grafiki 3-w](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Scenorys — omówienie](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
