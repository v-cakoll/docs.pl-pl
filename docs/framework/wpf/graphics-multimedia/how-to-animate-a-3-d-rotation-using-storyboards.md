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
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="79d40-102">Jak animować rotację 3-D z wykorzystaniem scenorysów</span><span class="sxs-lookup"><span data-stu-id="79d40-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="79d40-103">Poniższy przykład przedstawia sposób obiektu 3D, obracanie podczas jego "wobbles" przez animację <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu.</span><span class="sxs-lookup"><span data-stu-id="79d40-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="79d40-104">To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> obiektu określa przekształcenia obrotu 3W obiektu i dlatego animowania właściwości tworzy efektu obrotu desire.</span><span class="sxs-lookup"><span data-stu-id="79d40-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="79d40-105">W ramach scenorysu <xref:System.Windows.Media.Animation.DoubleAnimation> służy do animowania <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> właściwości podczas <xref:System.Windows.Media.Animation.Vector3DAnimation> służy do animowania <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="79d40-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79d40-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="79d40-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="79d40-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79d40-107">See Also</span></span>  
 [<span data-ttu-id="79d40-108">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="79d40-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="79d40-109">Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="79d40-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="79d40-110">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="79d40-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="79d40-111">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="79d40-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
