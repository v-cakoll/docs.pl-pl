---
title: Jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 7f60a3cd3fc88c5bb2460864be6cee008dc672fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557629"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="ac824-102">Jak dodawać wartość danych wyjściowych animacji do wartości początkowej animacji</span><span class="sxs-lookup"><span data-stu-id="ac824-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="ac824-103">W tym przykładzie przedstawiono sposób dodawania wartość wyjściowa animacji na wartość początkową animacji.</span><span class="sxs-lookup"><span data-stu-id="ac824-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac824-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac824-104">Example</span></span>  
 <span data-ttu-id="ac824-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Właściwość określa, czy wartość wyjściowa dodane do początkowej wartości (podstawa) animowanej właściwości animacji.</span><span class="sxs-lookup"><span data-stu-id="ac824-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="ac824-106">Można użyć <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> właściwości z najprostszych animacji i większości klatek kluczowych animacji.</span><span class="sxs-lookup"><span data-stu-id="ac824-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="ac824-107">Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ac824-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="ac824-108">W poniższym przykładzie przedstawiono efekt użycia <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> właściwości o <xref:System.Windows.Media.Animation.DoubleAnimation> i przy użyciu <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> właściwości o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="ac824-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ac824-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac824-109">See Also</span></span>  
 [<span data-ttu-id="ac824-110">Gromadzenie wartości animacji podczas cykli powtórzeń</span><span class="sxs-lookup"><span data-stu-id="ac824-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="ac824-111">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="ac824-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ac824-112">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="ac824-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="ac824-113">Synchronizację</span><span class="sxs-lookup"><span data-stu-id="ac824-113">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="ac824-114">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ac824-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
