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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188321"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Instrukcje: Ustawianie właściwości po zanimowaniu jej za pomocą scenorysu
W niektórych przypadkach może pojawić się, nie można zmienić wartości właściwości po ma zostać animowany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> służy animować kolor <xref:System.Windows.Media.SolidColorBrush>. Scenorys jest wyzwalana po kliknięciu przycisku. <xref:System.Windows.Media.Animation.Timeline.Completed> Zdarzeń odbywa się tak, aby program jest powiadamiany po <xref:System.Windows.Media.Animation.ColorAnimation> kończy.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Przykład  
 Po <xref:System.Windows.Media.Animation.ColorAnimation> ukończy, program próbuje zmienić kolor pędzla na niebieski.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Powyższy kod nie wydaje się podejmować żadnych działań: żółty, pozostaje pędzla, czyli wartość dostarczonych przez <xref:System.Windows.Media.Animation.ColorAnimation> , animowane pędzla. Wartość właściwości podstawowej (wartości bazowej) faktycznie jest zmieniany na niebieski. Jednak pozostanie żółty wartość skuteczne lub bieżące, ponieważ <xref:System.Windows.Media.Animation.ColorAnimation> nadal zastępują wartości bazowej. Jeśli chcesz, aby wartości bazowej zostać wartość efektywna, należy zatrzymać animacji od wywieranie wpływu na właściwości. Istnieją trzy sposoby, w tym celu z animacjami scenorysu:  
  
-   Ustawienie animacji <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Usuń całą scenorysu.  
  
-   Usuń animację z pojedynczej właściwości.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Ustaw właściwość FillBehavior animacji Stop  
 Ustawiając <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, wskazujemy animacji, aby zatrzymać wpływu na jego właściwość docelowa, po osiągnięciu końca jego okresu aktywności.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Usuń całą scenorysu  
 Za pomocą <xref:System.Windows.Media.Animation.RemoveStoryboard> wyzwalacza lub <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metody, wskazujemy animacjami scenorysu, aby zatrzymać wpływających na ich właściwości obiektu docelowego. Różnica między tym podejściem a ustawienie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość jest usunięcie scenorysu w dowolnym momencie podczas <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość obowiązują wyłącznie podczas animacji osiągnie koniec okresu aktywacji.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Usuń animację z pojedynczej właściwości  
 Inna technika, aby zatrzymać animację wpływały właściwość jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody obiektu, jest animowany. Określa właściwość, jest animowany podczas pierwszego parametru i `null` jako drugiego.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Ta metoda działa również w animacji nie scenorys.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Techniki animacji właściwości](property-animation-techniques-overview.md)
