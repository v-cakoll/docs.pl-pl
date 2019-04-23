---
title: 'Instrukcje: Animowanie położenia kamery i kierunku w scenie 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: b64263a495ffe845a76317aad8f5b4a14e11b31e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146006"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="9ff02-102">Instrukcje: Animowanie położenia kamery i kierunku w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="9ff02-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="9ff02-103">Poniższy przykład pokazuje, jak animować położenie kamery i kierunek w scenie 3D wskazuje animować.</span><span class="sxs-lookup"><span data-stu-id="9ff02-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="9ff02-104">Jest to wykonywane przy użyciu <xref:System.Windows.Media.Animation.Point3DAnimation> i <xref:System.Windows.Media.Animation.Vector3DAnimation> animować <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> właściwości odpowiednio <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="9ff02-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="9ff02-105">Można użyć animacji, tak aby zmienić widok onlooker sceny w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9ff02-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ff02-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ff02-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9ff02-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ff02-107">See also</span></span>

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="9ff02-108">Animowanie położenia kamery i kierunku z użyciem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="9ff02-108">Animate Camera Position and Direction Using Key Frames</span></span>](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="9ff02-109">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="9ff02-109">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
