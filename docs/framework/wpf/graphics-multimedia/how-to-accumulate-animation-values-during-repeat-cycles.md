---
title: 'Instrukcje: Gromadź wartości animacji podczas cykli powtórzeń'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: e38e1601e2f4eeab2b53918924bc21e05163d948
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357264"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="1fbda-102">Instrukcje: Gromadź wartości animacji podczas cykli powtórzeń</span><span class="sxs-lookup"><span data-stu-id="1fbda-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="1fbda-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwość gromadzenie wartości animacji w cyklach.</span><span class="sxs-lookup"><span data-stu-id="1fbda-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fbda-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fbda-104">Example</span></span>  
 <span data-ttu-id="1fbda-105">Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości są gromadzone podstawowej wartości animacji w cyklach.</span><span class="sxs-lookup"><span data-stu-id="1fbda-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="1fbda-106">Na przykład jeśli ustawisz powtarzanie 9 razy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") i ustaw właściwość animować od 10 do 15 (z = 10 = 15), animuje właściwość od 10 do 15 podczas pierwszego cyklu w 15-20 podczas drugiego cyklu , 20 – 25 podczas cyklu trzeci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1fbda-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="1fbda-107">Z tego powodu cyklu animacji używa końcową wartość animacji od poprzedniego cyklu animacji jako jego wartości bazowej.</span><span class="sxs-lookup"><span data-stu-id="1fbda-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="1fbda-108">Możesz użyć `IsCumulative` właściwość najbardziej podstawowym animacje i większości klatek kluczowych animacji.</span><span class="sxs-lookup"><span data-stu-id="1fbda-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="1fbda-109">Aby uzyskać więcej informacji, zobacz [Przegląd animacja](animation-overview.md) i [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1fbda-109">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="1fbda-110">Poniższy przykład przedstawia tego zachowania, animowanie szerokość cztery prostokąty.</span><span class="sxs-lookup"><span data-stu-id="1fbda-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="1fbda-111">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1fbda-111">The example:</span></span>  
  
-   <span data-ttu-id="1fbda-112">Animuje pierwszy prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="1fbda-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="1fbda-113">Animuje drugi prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimation> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> właściwości wartość domyślna `false`.</span><span class="sxs-lookup"><span data-stu-id="1fbda-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="1fbda-114">Animuje trzeci prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="1fbda-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="1fbda-115">Animuje ostatniego prostokąt z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> i ustawia <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="1fbda-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1fbda-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fbda-116">See also</span></span>
- [<span data-ttu-id="1fbda-117">Dodawanie wartości danych wyjściowych animacji do wartości początkowej animacji</span><span class="sxs-lookup"><span data-stu-id="1fbda-117">Add an Animation Output Value to an Animation Starting Value</span></span>](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [<span data-ttu-id="1fbda-118">Powtarzanie animacji</span><span class="sxs-lookup"><span data-stu-id="1fbda-118">Repeat an Animation</span></span>](how-to-repeat-an-animation.md)
- [<span data-ttu-id="1fbda-119">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="1fbda-119">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1fbda-120">Animacje kluczowych klatek — przegląd</span><span class="sxs-lookup"><span data-stu-id="1fbda-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1fbda-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="1fbda-121">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
