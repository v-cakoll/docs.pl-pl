---
title: 'Instrukcje: Animuj rotację 3-D z wykorzystaniem scenorysów'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 0e5e0b4e2b991b15ff7a49da65bfe96485e66fcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589808"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="5bcc7-102">Instrukcje: Animuj rotację 3-D z wykorzystaniem scenorysów</span><span class="sxs-lookup"><span data-stu-id="5bcc7-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="5bcc7-103">Poniższy przykład pokazuje, jak należy obrócić podczas jego "wobbles", animowanie obiektu 3D <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5bcc7-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="5bcc7-104">To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu określa przekształceń obrotu obiektu 3D i dlatego animowanie właściwości tworzy efekt obrotu wymaganą.</span><span class="sxs-lookup"><span data-stu-id="5bcc7-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="5bcc7-105">W ramach serii ujęć <xref:System.Windows.Media.Animation.DoubleAnimation> jest używana animacji <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości <xref:System.Windows.Media.Animation.Vector3DAnimation> jest używana animacji <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5bcc7-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bcc7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bcc7-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5bcc7-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bcc7-107">See also</span></span>
- [<span data-ttu-id="5bcc7-108">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="5bcc7-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="5bcc7-109">Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="5bcc7-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="5bcc7-110">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="5bcc7-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="5bcc7-111">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="5bcc7-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
