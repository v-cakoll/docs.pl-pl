---
title: 'Instrukcje: Animuj rotację 3D z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 90e982838cb5d5b4488185c041e946c15d1e61e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369139"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="3983a-102">Instrukcje: Animuj rotację 3D z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="3983a-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="3983a-103">W poniższym przykładzie <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> jest używane do utworzenia obiektu 3D Obróć podczas jego osi obrotu animuje skutkuje "wobble".</span><span class="sxs-lookup"><span data-stu-id="3983a-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="3983a-104">Ta animacja używa następujących klatek kluczowych:</span><span class="sxs-lookup"><span data-stu-id="3983a-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="3983a-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> Służy do tworzenia płynne i liniowej interpolacji między wartościami.</span><span class="sxs-lookup"><span data-stu-id="3983a-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="3983a-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> Służy do tworzenia nagłe "skoków" między wartościami (nie interpolacji).</span><span class="sxs-lookup"><span data-stu-id="3983a-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="3983a-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> Służy do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3983a-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="3983a-108">W poniższym przykładzie ta część animacji rozpoczyna się poza powolne, ale w kierunku końca odcinka czasu, przyspiesza wykładniczo.</span><span class="sxs-lookup"><span data-stu-id="3983a-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3983a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3983a-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3983a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3983a-110">See also</span></span>
- [<span data-ttu-id="3983a-111">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="3983a-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="3983a-112">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="3983a-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="3983a-113">Animowanie obrotu 3D przy użyciu scenorysów</span><span class="sxs-lookup"><span data-stu-id="3983a-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="3983a-114">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="3983a-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="3983a-115">Animowanie obrotu 3D przy użyciu kwaternionów</span><span class="sxs-lookup"><span data-stu-id="3983a-115">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="3983a-116">Animowanie obrotu 3D przy użyciu klatek kluczowych (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="3983a-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
