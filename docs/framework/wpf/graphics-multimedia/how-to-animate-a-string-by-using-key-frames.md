---
title: 'Instrukcje: Animowanie ciągu przy użyciu klatek kluczowych'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651431"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a><span data-ttu-id="0a48f-102">Instrukcje: Animowanie ciągu przy użyciu klatek kluczowych</span><span class="sxs-lookup"><span data-stu-id="0a48f-102">How to: Animate a String by Using Key Frames</span></span>
<span data-ttu-id="0a48f-103">W tym przykładzie pokazano, jak animować ciąg, który w tym przykładzie jest <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button> kontroli przy użyciu klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="0a48f-103">This example shows how to animate a string, which in this example is the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a48f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a48f-104">Example</span></span>  
 <span data-ttu-id="0a48f-105">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> klasy, aby animować <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="0a48f-105">The following example uses the <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="0a48f-106">Klatek kluczowych w tym przykładzie są używane <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> klasy, ponieważ animacji ciąg, który jest tworzony z użyciem klatek kluczowych można używać tylko dyskretnych klatek kluczowych.</span><span class="sxs-lookup"><span data-stu-id="0a48f-106">All the key frames in this example use an instance of the <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> class because a string animation that is created with key frames can only use discrete key frames.</span></span> <span data-ttu-id="0a48f-107">Dyskretne klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> tworzenie nagłe skoki między wartości, oznacza to, zmiany w animacji wystąpić szybko i nie są subtelne.</span><span class="sxs-lookup"><span data-stu-id="0a48f-107">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> create sudden jumps between values, that is, changes to the animation occur quickly and are not subtle.</span></span>  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0a48f-108">Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="0a48f-108">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a48f-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a48f-109">See also</span></span>

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [<span data-ttu-id="0a48f-110">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="0a48f-110">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0a48f-111">Klatki kluczowe — tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0a48f-111">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
