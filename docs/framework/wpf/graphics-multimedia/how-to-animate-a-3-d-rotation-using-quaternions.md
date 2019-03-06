---
title: 'Instrukcje: Animuj rotację 3D z wykorzystaniem kwaternionów'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 079358ec12da803c8aa497bce1c272fa51f1c3b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368574"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="f2d6a-102">Instrukcje: Animuj rotację 3D z wykorzystaniem kwaternionów</span><span class="sxs-lookup"><span data-stu-id="f2d6a-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="f2d6a-103">W tym przykładzie pokazano, jak animować rotację 3-D z wykorzystaniem kwaternionów obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2d6a-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="f2d6a-104">Poniższy kod przedstawia <xref:System.Windows.Media.Media3D.QuaternionRotation3D> używany jako wartość <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> właściwość <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="f2d6a-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="f2d6a-105">To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> jest animowany z <xref:System.Windows.Media.Animation.QuaternionAnimation> w ramach <xref:System.Windows.Media.Animation.Storyboard> przy użyciu kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="f2d6a-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="f2d6a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2d6a-106">Example</span></span>  
 <span data-ttu-id="f2d6a-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="f2d6a-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f2d6a-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2d6a-108">See also</span></span>
- [<span data-ttu-id="f2d6a-109">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="f2d6a-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="f2d6a-110">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="f2d6a-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="f2d6a-111">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="f2d6a-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="f2d6a-112">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="f2d6a-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="f2d6a-113">Animowanie obrotu 3D przy użyciu scenorysów</span><span class="sxs-lookup"><span data-stu-id="f2d6a-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="f2d6a-114">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="f2d6a-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
