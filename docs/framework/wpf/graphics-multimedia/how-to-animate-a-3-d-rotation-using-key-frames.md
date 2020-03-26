---
title: 'Jak: Animowanie obrotu 3D za pomocą klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112313"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a><span data-ttu-id="61441-102">Jak: Animowanie obrotu 3D za pomocą klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="61441-102">How to: Animate a 3D Rotation Using Key Frames</span></span>
<span data-ttu-id="61441-103">W poniższym <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> przykładzie służy do obracania obiektu 3D, podczas gdy jego oś obrotu animuje się, co powoduje "chwiejność".</span><span class="sxs-lookup"><span data-stu-id="61441-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="61441-104">Ta animacja używa następujących klatek kluczowych:</span><span class="sxs-lookup"><span data-stu-id="61441-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="61441-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>służy do tworzenia płynnej, liniowej interpolacji między wartościami.</span><span class="sxs-lookup"><span data-stu-id="61441-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="61441-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>służy do tworzenia nagłych "skoków" między wartościami (bez interpolacji).</span><span class="sxs-lookup"><span data-stu-id="61441-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="61441-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>służy do tworzenia zmiennej przejścia między <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> wartościami w zależności od właściwości.</span><span class="sxs-lookup"><span data-stu-id="61441-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="61441-108">W poniższym przykładzie ta część animacji zaczyna się powoli, ale pod koniec segmentu czasu, przyspiesza wykładniczo.</span><span class="sxs-lookup"><span data-stu-id="61441-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61441-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="61441-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="61441-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61441-110">See also</span></span>

- [<span data-ttu-id="61441-111">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="61441-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="61441-112">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="61441-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="61441-113">Animowanie obrotu 3D za pomocą sceno-zoka</span><span class="sxs-lookup"><span data-stu-id="61441-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="61441-114">Animowanie obrotu 3D za pomocą funkcji Rotation3DAnimacja</span><span class="sxs-lookup"><span data-stu-id="61441-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="61441-115">Animowanie obrotu 3D przy użyciu kwaterników</span><span class="sxs-lookup"><span data-stu-id="61441-115">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="61441-116">Animowanie obrotu 3D przy użyciu klatek kluczowych (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="61441-116">Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
