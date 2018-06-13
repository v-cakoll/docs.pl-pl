---
title: Jak animować boolean z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: d6273c08881e802595e831cafe120a5bec841c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556929"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="3b29d-102">Jak animować boolean z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="3b29d-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="3b29d-103">W tym przykładzie pokazano, jak do animowania właściwości typu Boolean wartość <xref:System.Windows.Controls.Button> formantu przy użyciu klucza ramki.</span><span class="sxs-lookup"><span data-stu-id="3b29d-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b29d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b29d-104">Example</span></span>  
 <span data-ttu-id="3b29d-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.UIElement.IsEnabled%2A> właściwość <xref:System.Windows.Controls.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="3b29d-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="3b29d-106">Klatek kluczowych w tym przykładzie są używane <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> klasy.</span><span class="sxs-lookup"><span data-stu-id="3b29d-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="3b29d-107">Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> utworzyć nagłym przechodzi między wartościami, oznacza to, ruch animacji jest jerky.</span><span class="sxs-lookup"><span data-stu-id="3b29d-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="3b29d-108">Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="3b29d-108">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b29d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b29d-109">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>  
 <xref:System.Windows.UIElement.IsEnabled%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="3b29d-110">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="3b29d-110">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="3b29d-111">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="3b29d-111">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
