---
title: Jak animować rotację 3D z wykorzystaniem kwaternionów
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 4c2a46aad1feeefe5c7c31ec192f46b8c891337f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556942"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="9e852-102">Jak animować rotację 3D z wykorzystaniem kwaternionów</span><span class="sxs-lookup"><span data-stu-id="9e852-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="9e852-103">W tym przykładzie przedstawiono sposób animować obrót obiektu 3-w, za pomocą quaternions.</span><span class="sxs-lookup"><span data-stu-id="9e852-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="9e852-104">Kod poniżej przedstawia <xref:System.Windows.Media.Media3D.QuaternionRotation3D> używany jako wartość <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwość <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="9e852-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="9e852-105">To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> jest animowany z <xref:System.Windows.Media.Animation.QuaternionAnimation> w <xref:System.Windows.Media.Animation.Storyboard> przy użyciu kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="9e852-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="9e852-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e852-106">Example</span></span>  
 <span data-ttu-id="9e852-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="9e852-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9e852-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e852-108">See Also</span></span>  
 [<span data-ttu-id="9e852-109">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="9e852-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9e852-110">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="9e852-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="9e852-111">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="9e852-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="9e852-112">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="9e852-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="9e852-113">Animowanie obrotu 3D przy użyciu scenorysów</span><span class="sxs-lookup"><span data-stu-id="9e852-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="9e852-114">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="9e852-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
