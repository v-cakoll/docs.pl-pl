---
title: 'Instrukcje: Animuj boolean z wykorzystaniem klatek kluczowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 503e8ec8bdaf88bcba4093075b1e7216b7cd3746
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361963"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a><span data-ttu-id="32083-102">Instrukcje: Animuj boolean z wykorzystaniem klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="32083-102">How to: Animate a Boolean by Using Key Frames</span></span>
<span data-ttu-id="32083-103">W tym przykładzie pokazano, jak animować wartość właściwości typu Boolean <xref:System.Windows.Controls.Button> kontroli przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="32083-103">This example shows how to animate the Boolean property value of a <xref:System.Windows.Controls.Button> control by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32083-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="32083-104">Example</span></span>  
 <span data-ttu-id="32083-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.UIElement.IsEnabled%2A> właściwość <xref:System.Windows.Controls.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="32083-105">The following example uses the <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> class to animate the <xref:System.Windows.UIElement.IsEnabled%2A> property of a <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="32083-106">Klatek kluczowych w tym przykładzie są używane <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> klasy.</span><span class="sxs-lookup"><span data-stu-id="32083-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> class.</span></span> <span data-ttu-id="32083-107">Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, jerky przepływu animacji.</span><span class="sxs-lookup"><span data-stu-id="32083-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="32083-108">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="32083-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32083-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32083-109">See also</span></span>
- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="32083-110">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="32083-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="32083-111">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="32083-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
