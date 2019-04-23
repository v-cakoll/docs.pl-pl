---
title: 'Instrukcje: Animowanie obrotu 3D przy użyciu scenorysów'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146201"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="9f1c6-102">Instrukcje: Animowanie obrotu 3D przy użyciu scenorysów</span><span class="sxs-lookup"><span data-stu-id="9f1c6-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="9f1c6-103">Poniższy przykład pokazuje, jak należy obrócić podczas jego "wobbles", animowanie obiektu 3D <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9f1c6-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="9f1c6-104">To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu określa przekształceń obrotu obiektu 3D i dlatego animowanie właściwości tworzy efekt obrotu wymaganą.</span><span class="sxs-lookup"><span data-stu-id="9f1c6-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="9f1c6-105">W ramach serii ujęć <xref:System.Windows.Media.Animation.DoubleAnimation> jest używana animacji <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości <xref:System.Windows.Media.Animation.Vector3DAnimation> jest używana animacji <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9f1c6-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f1c6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f1c6-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9f1c6-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f1c6-107">See also</span></span>

- [<span data-ttu-id="9f1c6-108">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="9f1c6-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="9f1c6-109">Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="9f1c6-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="9f1c6-110">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="9f1c6-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="9f1c6-111">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="9f1c6-111">Storyboards Overview</span></span>](storyboards-overview.md)
