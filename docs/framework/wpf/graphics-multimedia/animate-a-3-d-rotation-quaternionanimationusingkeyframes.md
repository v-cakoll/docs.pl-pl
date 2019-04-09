---
title: 'Instrukcje: Animowanie obrotu 3D przy użyciu klatek kluczowych (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: f0b46e488f5f0ff0a918d7766998528fef001794
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100109"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="78ee1-102">Instrukcje: Animowanie obrotu 3D przy użyciu klatek kluczowych (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="78ee1-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="78ee1-103">W poniższym przykładzie <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> używa w celu obracania obiektu 3D.</span><span class="sxs-lookup"><span data-stu-id="78ee1-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="78ee1-104">Ta animacja używa następujących klatek kluczowych:</span><span class="sxs-lookup"><span data-stu-id="78ee1-104">This animation uses the following key frames:</span></span>  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> <span data-ttu-id="78ee1-105">Służy do tworzenia płynne i liniowej interpolacji między wartościami.</span><span class="sxs-lookup"><span data-stu-id="78ee1-105">is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> <span data-ttu-id="78ee1-106">Służy do tworzenia nagłe "skoków" między wartościami (nie interpolacji).</span><span class="sxs-lookup"><span data-stu-id="78ee1-106">is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> <span data-ttu-id="78ee1-107">Służy do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="78ee1-107">is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="78ee1-108">W poniższym przykładzie ta część animacji rozpoczyna się poza powolne, ale w kierunku końca odcinka czasu, przyspiesza wykładniczo.</span><span class="sxs-lookup"><span data-stu-id="78ee1-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78ee1-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="78ee1-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="78ee1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78ee1-110">See also</span></span>

- [<span data-ttu-id="78ee1-111">Animowanie obrotu 3D przy użyciu scenorysów</span><span class="sxs-lookup"><span data-stu-id="78ee1-111">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="78ee1-112">Animowanie obrotu 3D przy użyciu elementu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="78ee1-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="78ee1-113">Animowanie obrotu 3D przy użyciu kwaternionów</span><span class="sxs-lookup"><span data-stu-id="78ee1-113">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="78ee1-114">Animowanie obrotu 3D przy użyciu klatek kluczowych (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="78ee1-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="78ee1-115">Przegląd Grafika 3-D</span><span class="sxs-lookup"><span data-stu-id="78ee1-115">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="78ee1-116">Przegląd Animacja kluczowych klatek</span><span class="sxs-lookup"><span data-stu-id="78ee1-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
