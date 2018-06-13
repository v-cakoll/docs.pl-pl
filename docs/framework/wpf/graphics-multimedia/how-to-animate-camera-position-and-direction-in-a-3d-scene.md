---
title: Jak animować położenie kamery i kierunek w scenie 3D
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 429139da809a78474f4f6a082fb6e3c08c72d431
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558881"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="5f949-102">Jak animować położenie kamery i kierunek w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="5f949-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="5f949-103">Poniższy przykład pokazuje, jak animować pozycja kamery i animować kierunku, który wskazuje sceny 3W.</span><span class="sxs-lookup"><span data-stu-id="5f949-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="5f949-104">Jest to zrobić za pomocą <xref:System.Windows.Media.Animation.Point3DAnimation> i <xref:System.Windows.Media.Animation.Vector3DAnimation> do animowania <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> i <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> właściwości odpowiednio <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="5f949-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="5f949-105">Aby zmienić widok onlooker sceny w odpowiedzi na zdarzenia można użyć animacji następująco.</span><span class="sxs-lookup"><span data-stu-id="5f949-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f949-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f949-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5f949-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f949-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [<span data-ttu-id="5f949-108">Animowanie położenia kamery i kierunku z użyciem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="5f949-108">Animate Camera Position and Direction Using Key Frames</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [<span data-ttu-id="5f949-109">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="5f949-109">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
