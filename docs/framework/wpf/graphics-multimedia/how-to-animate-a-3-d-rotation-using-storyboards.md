---
title: 'Jak: Animowanie obrotu 3D za pomocą scenostrunacji'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112219"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a>Jak: Animowanie obrotu 3D za pomocą scenostrunacji
W poniższym przykładzie pokazano, jak sprawić, aby obiekt 3D obracał <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> się, gdy <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> "chwieje się", animując właściwości obiektu. Ten <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiekt określa przekłęcie obrotu obiektu 3D, a więc animowanie jego właściwości tworzy efekt obrotu pragnienia. W scenorysie służy do <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> animowania <xref:System.Windows.Media.Animation.Vector3DAnimation> właściwości, <xref:System.Windows.Media.Animation.DoubleAnimation> podczas <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> gdy jest używany do animowania właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz też

- [Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Przegląd Scenorysy](storyboards-overview.md)
