---
title: 'Instrukcje: Animowanie obrotu 3D przy użyciu scenorysów'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024758"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Instrukcje: Animowanie obrotu 3D przy użyciu scenorysów
Poniższy przykład pokazuje, jak należy obrócić podczas jego "wobbles", animowanie obiektu 3D <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu. To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu określa przekształceń obrotu obiektu 3D i dlatego animowanie właściwości tworzy efekt obrotu wymaganą. W ramach serii ujęć <xref:System.Windows.Media.Animation.DoubleAnimation> jest używana animacji <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości <xref:System.Windows.Media.Animation.Vector3DAnimation> jest używana animacji <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- [Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
