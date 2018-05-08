---
title: Jak ustawić właściwość po zanimowaniu jej za pomocą scenorysu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: b8e9c08075b13f8d6f701d5ac6ae4f8ea8949184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Jak ustawić właściwość po zanimowaniu jej za pomocą scenorysu
W niektórych przypadkach może się pojawić, nie można zmienić wartości właściwości po ma zostać animowany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.Storyboard> służy do animowania kolor <xref:System.Windows.Media.SolidColorBrush>. Scenorysu jest wyzwalane, gdy przycisk zostanie kliknięty. <xref:System.Windows.Media.Animation.Timeline.Completed> Zdarzenie jest obsługiwane, dzięki czemu program jest powiadamiany o po <xref:System.Windows.Media.Animation.ColorAnimation> zakończeniu.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Przykład  
 Po <xref:System.Windows.Media.Animation.ColorAnimation> zakończeniu program próbuje zmienić kolor pędzla na niebieski.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Poprzedni kod wygląda na niczego robić: żółty, pozostaje pędzla, które jest wartością dostarczonych przez <xref:System.Windows.Media.Animation.ColorAnimation> który animowany pędzla. Odpowiednia wartość właściwości (wartości podstawowej) faktycznie jest zmieniany na niebieski. Jednak nadal żółty wartość skuteczne lub bieżących, ponieważ <xref:System.Windows.Media.Animation.ColorAnimation> nadal przesłaniają wartości podstawowej. Wartość podstawowa znów wartość, należy zatrzymać animacji z wpływające na właściwość. Istnieją trzy sposoby, w tym animacje scenorysu:  
  
-   Ustawienie animacji <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Usuń całą scenorysu.  
  
-   Usuwanie animacji z poszczególnych właściwości.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Ustaw właściwość FillBehavior animacji do zatrzymania  
 Przez ustawienie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> do <xref:System.Windows.Media.Animation.FillBehavior.Stop>, poinformuj animacji przestanie wpływu na jego właściwość target po dotarciu serwerów do zakończenia okresu aktywacji.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Usuń całą scenorysu  
 Za pomocą <xref:System.Windows.Media.Animation.RemoveStoryboard> wyzwalacza lub <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metody, poinformuj animacje scenorysu, aby zatrzymać wpływających na ich właściwości obiektu docelowego. Różnica między tego podejścia i ustawienie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość jest usunięcie scenorysu w dowolnym momencie, podczas gdy <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości obowiązują wyłącznie po animacji dociera do końca okresu aktywnego.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Usuń animacji z wybranej właściwości  
 Jest użycie innej techniki przestanie animacji wpływały właściwość <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody animowanej obiektu. Określ właściwość animowanej jako pierwszego parametru oraz `null` jako drugiego.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Ta metoda działa również w animacji nie scenorysu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Techniki animacji właściwości — przegląd](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
