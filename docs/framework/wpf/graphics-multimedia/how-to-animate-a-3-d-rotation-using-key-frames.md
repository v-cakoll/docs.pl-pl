---
title: "Jak animować rotację 3D z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad8934dacd64f31cf65d7517d8c48114522505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="0f1cc-102">Jak animować rotację 3D z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="0f1cc-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="0f1cc-103">W poniższym przykładzie <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> jest używane do obliczania obiektu 3D Obróć podczas jego oś obrotu animuje, co powoduje "wobble".</span><span class="sxs-lookup"><span data-stu-id="0f1cc-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="0f1cc-104">Ta animacja używa następujących klatek kluczowych:</span><span class="sxs-lookup"><span data-stu-id="0f1cc-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="0f1cc-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>Służy do tworzenia smooth, liniowy interpolacji między wartościami.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="0f1cc-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>Służy do tworzenia nagłym "skoków" między wartości (nie interpolacji).</span><span class="sxs-lookup"><span data-stu-id="0f1cc-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="0f1cc-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>Służy do tworzenia zmiennych przejścia między wartościami w zależności od <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="0f1cc-108">W poniższym przykładzie ta część animacji rozpoczyna się poza powolne, ale do końca segmentu czasu, znacznie szybciej.</span><span class="sxs-lookup"><span data-stu-id="0f1cc-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f1cc-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f1cc-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0f1cc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f1cc-110">See Also</span></span>  
 [<span data-ttu-id="0f1cc-111">Przegląd grafiki 3-w</span><span class="sxs-lookup"><span data-stu-id="0f1cc-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="0f1cc-112">Omówienie klucza poklatkowych</span><span class="sxs-lookup"><span data-stu-id="0f1cc-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="0f1cc-113">Animowanie obrót 3-w przy użyciu Scenorys</span><span class="sxs-lookup"><span data-stu-id="0f1cc-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="0f1cc-114">Animowanie obrót 3-w przy użyciu Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="0f1cc-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="0f1cc-115">Animowanie obrót 3-w przy użyciu Quaternions</span><span class="sxs-lookup"><span data-stu-id="0f1cc-115">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="0f1cc-116">Animowanie obrót 3-w przy użyciu klucza ramek (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="0f1cc-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
