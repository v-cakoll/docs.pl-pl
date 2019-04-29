---
title: 'Instrukcje: Ustawianie właściwości po zanimowaniu jej za pomocą scenorysu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 2e1389392c6465ed56b2c71e53b2e3c1947acbe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651106"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="1a6e6-102">Instrukcje: Ustawianie właściwości po zanimowaniu jej za pomocą scenorysu</span><span class="sxs-lookup"><span data-stu-id="1a6e6-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="1a6e6-103">W niektórych przypadkach może pojawić się, nie można zmienić wartości właściwości po ma zostać animowany.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a6e6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a6e6-104">Example</span></span>  
 <span data-ttu-id="1a6e6-105">W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> służy animować kolor <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="1a6e6-106">Scenorys jest wyzwalana po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="1a6e6-107"><xref:System.Windows.Media.Animation.Timeline.Completed> Zdarzeń odbywa się tak, aby program jest powiadamiany po <xref:System.Windows.Media.Animation.ColorAnimation> kończy.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="1a6e6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a6e6-108">Example</span></span>  
 <span data-ttu-id="1a6e6-109">Po <xref:System.Windows.Media.Animation.ColorAnimation> ukończy, program próbuje zmienić kolor pędzla na niebieski.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="1a6e6-110">Powyższy kod nie wydaje się podejmować żadnych działań: żółty, pozostaje pędzla, czyli wartość dostarczonych przez <xref:System.Windows.Media.Animation.ColorAnimation> , animowane pędzla.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="1a6e6-111">Wartość właściwości podstawowej (wartości bazowej) faktycznie jest zmieniany na niebieski.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="1a6e6-112">Jednak pozostanie żółty wartość skuteczne lub bieżące, ponieważ <xref:System.Windows.Media.Animation.ColorAnimation> nadal zastępują wartości bazowej.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="1a6e6-113">Jeśli chcesz, aby wartości bazowej zostać wartość efektywna, należy zatrzymać animacji od wywieranie wpływu na właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="1a6e6-114">Istnieją trzy sposoby, w tym celu z animacjami scenorysu:</span><span class="sxs-lookup"><span data-stu-id="1a6e6-114">There are three ways to do this with storyboard animations:</span></span>  
  
- <span data-ttu-id="1a6e6-115">Ustawienie animacji <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości <xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="1a6e6-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
- <span data-ttu-id="1a6e6-116">Usuń całą scenorysu.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-116">Remove the entire Storyboard.</span></span>  
  
- <span data-ttu-id="1a6e6-117">Usuń animację z pojedynczej właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="1a6e6-118">Ustaw właściwość FillBehavior animacji Stop</span><span class="sxs-lookup"><span data-stu-id="1a6e6-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="1a6e6-119">Ustawiając <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, wskazujemy animacji, aby zatrzymać wpływu na jego właściwość docelowa, po osiągnięciu końca jego okresu aktywności.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="1a6e6-120">Usuń całą scenorysu</span><span class="sxs-lookup"><span data-stu-id="1a6e6-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="1a6e6-121">Za pomocą <xref:System.Windows.Media.Animation.RemoveStoryboard> wyzwalacza lub <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metody, wskazujemy animacjami scenorysu, aby zatrzymać wpływających na ich właściwości obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="1a6e6-122">Różnica między tym podejściem a ustawienie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość jest usunięcie scenorysu w dowolnym momencie podczas <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość obowiązują wyłącznie podczas animacji osiągnie koniec okresu aktywacji.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="1a6e6-123">Usuń animację z pojedynczej właściwości</span><span class="sxs-lookup"><span data-stu-id="1a6e6-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="1a6e6-124">Inna technika, aby zatrzymać animację wpływały właściwość jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody obiektu, jest animowany.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="1a6e6-125">Określa właściwość, jest animowany podczas pierwszego parametru i `null` jako drugiego.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="1a6e6-126">Ta metoda działa również w animacji nie scenorys.</span><span class="sxs-lookup"><span data-stu-id="1a6e6-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6e6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a6e6-127">See also</span></span>

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [<span data-ttu-id="1a6e6-128">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="1a6e6-128">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1a6e6-129">Techniki animacji właściwości — przegląd</span><span class="sxs-lookup"><span data-stu-id="1a6e6-129">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
