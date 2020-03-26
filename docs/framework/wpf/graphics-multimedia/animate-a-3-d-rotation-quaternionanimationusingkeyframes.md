---
title: 'Jak: Animowanie obrotu 3D za pomocą klatek kluczowych (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112300"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="f7f6f-102">Jak: Animowanie obrotu 3D za pomocą klatek kluczowych (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="f7f6f-102">How to: Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="f7f6f-103">W poniższym <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> przykładzie jest używany do obracania obiektu 3D.</span><span class="sxs-lookup"><span data-stu-id="f7f6f-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="f7f6f-104">Ta animacja używa następujących klatek kluczowych:</span><span class="sxs-lookup"><span data-stu-id="f7f6f-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="f7f6f-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>służy do tworzenia płynnej, liniowej interpolacji między wartościami.</span><span class="sxs-lookup"><span data-stu-id="f7f6f-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="f7f6f-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>służy do tworzenia nagłych "skoków" między wartościami (bez interpolacji).</span><span class="sxs-lookup"><span data-stu-id="f7f6f-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="f7f6f-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>służy do tworzenia zmiennej przejścia między <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> wartościami w zależności od właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7f6f-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="f7f6f-108">W poniższym przykładzie ta część animacji zaczyna się powoli, ale pod koniec segmentu czasu, przyspiesza wykładniczo.</span><span class="sxs-lookup"><span data-stu-id="f7f6f-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7f6f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7f6f-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f7f6f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7f6f-110">See also</span></span>

- [<span data-ttu-id="f7f6f-111">Animowanie obrotu 3D za pomocą sceno-zoka</span><span class="sxs-lookup"><span data-stu-id="f7f6f-111">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="f7f6f-112">Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja</span><span class="sxs-lookup"><span data-stu-id="f7f6f-112">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="f7f6f-113">Animowanie obrotu 3D przy użyciu kwaterników</span><span class="sxs-lookup"><span data-stu-id="f7f6f-113">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="f7f6f-114">Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="f7f6f-114">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="f7f6f-115">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="f7f6f-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="f7f6f-116">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="f7f6f-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
