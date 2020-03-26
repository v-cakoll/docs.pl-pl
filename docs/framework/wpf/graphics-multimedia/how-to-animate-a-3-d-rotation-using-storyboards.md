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
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a><span data-ttu-id="fe0b5-102">Jak: Animowanie obrotu 3D za pomocą scenostrunacji</span><span class="sxs-lookup"><span data-stu-id="fe0b5-102">How to: Animate a 3D Rotation Using Storyboards</span></span>
<span data-ttu-id="fe0b5-103">W poniższym przykładzie pokazano, jak sprawić, aby obiekt 3D obracał <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> się, gdy <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> "chwieje się", animując właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe0b5-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="fe0b5-104">Ten <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiekt określa przekłęcie obrotu obiektu 3D, a więc animowanie jego właściwości tworzy efekt obrotu pragnienia.</span><span class="sxs-lookup"><span data-stu-id="fe0b5-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="fe0b5-105">W scenorysie służy do <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> animowania <xref:System.Windows.Media.Animation.Vector3DAnimation> właściwości, <xref:System.Windows.Media.Animation.DoubleAnimation> podczas <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> gdy jest używany do animowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe0b5-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe0b5-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe0b5-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fe0b5-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe0b5-107">See also</span></span>

- [<span data-ttu-id="fe0b5-108">Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja</span><span class="sxs-lookup"><span data-stu-id="fe0b5-108">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="fe0b5-109">Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="fe0b5-109">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="fe0b5-110">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="fe0b5-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="fe0b5-111">Przegląd Scenorysy</span><span class="sxs-lookup"><span data-stu-id="fe0b5-111">Storyboards Overview</span></span>](storyboards-overview.md)
