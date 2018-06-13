---
title: Jak animować rotację 3-D z wykorzystaniem scenorysów
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: a6cc8774c14d4b393b0d04822216c894e486ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556708"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Jak animować rotację 3-D z wykorzystaniem scenorysów
Poniższy przykład przedstawia sposób obiektu 3D, obracanie podczas jego "wobbles" przez animację <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu. To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu określa przekształcenia obrotu 3W obiektu i dlatego animowania właściwości tworzy efektu obrotu desire. W ramach scenorysu <xref:System.Windows.Media.Animation.DoubleAnimation> służy do animowania <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości podczas <xref:System.Windows.Media.Animation.Vector3DAnimation> służy do animowania <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [Grafika 3D — przegląd](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
