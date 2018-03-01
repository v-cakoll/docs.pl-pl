---
title: "Jak ustawić właściwość po zanimowaniu jej za pomocą scenorysu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ffc534549f5b114a07f09326be72c1968d178a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="e83e4-102">Jak ustawić właściwość po zanimowaniu jej za pomocą scenorysu</span><span class="sxs-lookup"><span data-stu-id="e83e4-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="e83e4-103">W niektórych przypadkach może się pojawić, nie można zmienić wartości właściwości po ma zostać animowany.</span><span class="sxs-lookup"><span data-stu-id="e83e4-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e83e4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e83e4-104">Example</span></span>  
 <span data-ttu-id="e83e4-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> służy do animowania kolor <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="e83e4-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="e83e4-106">Scenorysu jest wyzwalane, gdy przycisk zostanie kliknięty.</span><span class="sxs-lookup"><span data-stu-id="e83e4-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="e83e4-107"><xref:System.Windows.Media.Animation.Timeline.Completed> Zdarzenie jest obsługiwane, dzięki czemu program jest powiadamiany o po <xref:System.Windows.Media.Animation.ColorAnimation> zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e83e4-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="e83e4-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e83e4-108">Example</span></span>  
 <span data-ttu-id="e83e4-109">Po <xref:System.Windows.Media.Animation.ColorAnimation> zakończeniu program próbuje zmienić kolor pędzla na niebieski.</span><span class="sxs-lookup"><span data-stu-id="e83e4-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="e83e4-110">Poprzedni kod wygląda na niczego robić: żółty, pozostaje pędzla, które jest wartością dostarczonych przez <xref:System.Windows.Media.Animation.ColorAnimation> który animowany pędzla.</span><span class="sxs-lookup"><span data-stu-id="e83e4-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="e83e4-111">Odpowiednia wartość właściwości (wartości podstawowej) faktycznie jest zmieniany na niebieski.</span><span class="sxs-lookup"><span data-stu-id="e83e4-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="e83e4-112">Jednak nadal żółty wartość skuteczne lub bieżących, ponieważ <xref:System.Windows.Media.Animation.ColorAnimation> nadal przesłaniają wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e83e4-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="e83e4-113">Wartość podstawowa znów wartość, należy zatrzymać animacji z wpływające na właściwość.</span><span class="sxs-lookup"><span data-stu-id="e83e4-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="e83e4-114">Istnieją trzy sposoby, w tym animacje scenorysu:</span><span class="sxs-lookup"><span data-stu-id="e83e4-114">There are three ways to do this with storyboard animations:</span></span>  
  
-   <span data-ttu-id="e83e4-115">Ustawienie animacji <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości<xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="e83e4-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
-   <span data-ttu-id="e83e4-116">Usuń całą scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e83e4-116">Remove the entire Storyboard.</span></span>  
  
-   <span data-ttu-id="e83e4-117">Usuwanie animacji z poszczególnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="e83e4-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="e83e4-118">Ustaw właściwość FillBehavior animacji do zatrzymania</span><span class="sxs-lookup"><span data-stu-id="e83e4-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="e83e4-119">Przez ustawienie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, poinformuj animacji przestanie wpływu na jego właściwość target po dotarciu serwerów do zakończenia okresu aktywacji.</span><span class="sxs-lookup"><span data-stu-id="e83e4-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="e83e4-120">Usuń całą scenorysu</span><span class="sxs-lookup"><span data-stu-id="e83e4-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="e83e4-121">Za pomocą <xref:System.Windows.Media.Animation.RemoveStoryboard> wyzwalacza lub <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metody, poinformuj animacje scenorysu, aby zatrzymać wpływających na ich właściwości obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e83e4-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="e83e4-122">Różnica między tego podejścia i ustawienie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość jest usunięcie scenorysu w dowolnym momencie, podczas gdy <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości obowiązują wyłącznie po animacji dociera do końca okresu aktywnego.</span><span class="sxs-lookup"><span data-stu-id="e83e4-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="e83e4-123">Usuń animacji z wybranej właściwości</span><span class="sxs-lookup"><span data-stu-id="e83e4-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="e83e4-124">Jest użycie innej techniki przestanie animacji wpływały właściwość <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody animowanej obiektu.</span><span class="sxs-lookup"><span data-stu-id="e83e4-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="e83e4-125">Określ właściwość animowanej jako pierwszego parametru oraz `null` jako drugiego.</span><span class="sxs-lookup"><span data-stu-id="e83e4-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="e83e4-126">Ta metoda działa również w animacji nie scenorysu.</span><span class="sxs-lookup"><span data-stu-id="e83e4-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83e4-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e83e4-127">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [<span data-ttu-id="e83e4-128">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="e83e4-128">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e83e4-129">Techniki animacji właściwości — przegląd</span><span class="sxs-lookup"><span data-stu-id="e83e4-129">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
