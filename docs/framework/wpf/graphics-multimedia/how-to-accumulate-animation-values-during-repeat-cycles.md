---
title: "Jak gromadzić wartości animacji podczas cykli powtórzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a91856cdfcf1ca7ae87e8e571306170feecb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="da19f-102">Jak gromadzić wartości animacji podczas cykli powtórzeń</span><span class="sxs-lookup"><span data-stu-id="da19f-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="da19f-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> gromadzone przez powtarzające się cykle animacji wartości dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="da19f-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da19f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="da19f-104">Example</span></span>  
 <span data-ttu-id="da19f-105">Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości gromadzone przez powtarzające się cykle wartości podstawowe animacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="da19f-106">Na przykład ustawić powtarzanie 9 razy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") i ustaw właściwość do animowania od 10 do 15 (z = 10 = 15), właściwość animuje od 10 do 15 podczas pierwszego cyklu od 15 do 20 podczas drugiego cyklu , 20 – 25 podczas cyklu trzeci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="da19f-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="da19f-107">W związku z tym cyklu animacji używa wartości końcowej animacji od poprzedniego cyklu animacji jako jego wartość podstawową.</span><span class="sxs-lookup"><span data-stu-id="da19f-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="da19f-108">Można użyć `IsCumulative` właściwości z najprostszych animacji i większości klatek kluczowych animacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="da19f-109">Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da19f-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="da19f-110">W poniższym przykładzie pokazano to zachowanie przez szerokość cztery prostokąty animacji.</span><span class="sxs-lookup"><span data-stu-id="da19f-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="da19f-111">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da19f-111">The example:</span></span>  
  
-   <span data-ttu-id="da19f-112">Animuje pierwszy prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="da19f-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="da19f-113">Animuje drugi prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości wartość domyślna wynosząca `false`.</span><span class="sxs-lookup"><span data-stu-id="da19f-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="da19f-114">Animuje trzeci prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="da19f-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="da19f-115">Animuje ostatniego prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="da19f-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="da19f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da19f-116">See Also</span></span>  
 [<span data-ttu-id="da19f-117">Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji</span><span class="sxs-lookup"><span data-stu-id="da19f-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [<span data-ttu-id="da19f-118">Powtarzanie animacji</span><span class="sxs-lookup"><span data-stu-id="da19f-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [<span data-ttu-id="da19f-119">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="da19f-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="da19f-120">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="da19f-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="da19f-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="da19f-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
