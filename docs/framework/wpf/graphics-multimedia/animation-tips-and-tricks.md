---
title: Porady i triki animacyjne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
ms.openlocfilehash: 3a22c83eb739a735d42fa0f670716a0e75bbd54c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295955"
---
# <a name="animation-tips-and-tricks"></a>Porady i triki animacyjne
Podczas pracy z animacjami w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]kilka porad i wskazówek, które mogą ułatwić animacji działać lepiej i pozwala zaoszczędzić Rozczarowanie.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Ogólne problemy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animowanie położenia paska przewijania lub suwaka, zawiesza się go  
 Jeśli animować położenie paska przewijania lub suwaka, za pomocą animacji, który ma <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (wartość domyślna), użytkownik będzie już można przenieść paska przewijania lub suwaka. To dlatego, mimo że zakończył się animacji, nadal jest zastąpienie wartości bazowej właściwość docelowa. Aby zatrzymać animacji od zastąpienie bieżącej wartości właściwości, usuń go lub nadaj <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [ustawić właściwość po Zanimowaniu jej za pomocą scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animowanie danych wyjściowych animacji nie ma wpływu  
 Nie można animować obiekt, który znajduje się dane wyjściowe inną animację. Na przykład, jeśli używasz <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> animować <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Media.RadialGradientBrush> do <xref:System.Windows.Media.SolidColorBrush>, nie można animować właściwości z <xref:System.Windows.Media.RadialGradientBrush> lub <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nie można zmienić wartości właściwości po Zanimowaniu jej  
 W niektórych przypadkach może pojawić się, że nie można zmienić wartość właściwości jest został animowany, nawet w przypadku, po zakończeniu animacji. To, ponieważ mimo, że zakończono animacji, nadal jest zastąpienie właściwości wartości bazowej. Aby zatrzymać animacji od zastąpienie bieżącej wartości właściwości, usuń go lub nadaj <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [ustawić właściwość po Zanimowaniu jej za pomocą scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Zmiana na osi czasu nie ma wpływu  
 Mimo że większość <xref:System.Windows.Media.Animation.Timeline> właściwości są animatable i mogą być dane powiązane, zmiana wartości właściwości aktywnego <xref:System.Windows.Media.Animation.Timeline> wydaje się mieć żadnego efektu. Jest to spowodowane tym, gdy <xref:System.Windows.Media.Animation.Timeline> jest uruchomione, system chronometrażu tworzy kopię <xref:System.Windows.Media.Animation.Timeline> i używa jej do utworzenia <xref:System.Windows.Media.Animation.Clock> obiektu. Modyfikowanie oryginalnego nie ma wpływu na kopii systemu.  
  
 Aby uzyskać <xref:System.Windows.Media.Animation.Timeline> celu odzwierciedlenia zmian, jego zegara musi być ponownie wygenerowany i używany do zastępowania wcześniej utworzonej zegara. Zegary nie są generowane dla Ciebie automatycznie. Poniżej przedstawiono kilka sposobów, aby zastosować zmiany osi czasu:  
  
-   Jeśli jest na osi czasu, lub należy do <xref:System.Windows.Media.Animation.Storyboard>, możesz przekształcić ją odzwierciedlenia zmian przez ponowne wprowadzenie jego za pomocą scenorysu <xref:System.Windows.Media.Animation.BeginStoryboard> lub <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. Ma to również ponowne uruchomienie animacji efektem ubocznym. W kodzie, można użyć <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodę scenorysu z powrotem do jego poprzedniej pozycji.  
  
-   Jeśli animacji są stosowane bezpośrednio do właściwości przy użyciu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody, wywołanie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> ponownie metodą i przekaż go animacji, który został zmodyfikowany.  
  
-   Pracując bezpośrednio na poziomie zegara utworzyć i zastosować nowy zestaw zegary i używać ich w celu zastąpienia poprzedniego zestawu wygenerowanego zegary.  
  
 Aby uzyskać więcej informacji na temat osie czasu i zegary zobacz [Animacja i System chronometrażu w — Przegląd](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop nie działa zgodnie z oczekiwaniami  
 Czasami podczas ustawiania <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości <xref:System.Windows.Media.Animation.FillBehavior.Stop> wydaje się nie mają wpływu, takie jak czas jednej animacji "przekazywało" do innego, ponieważ ma ona <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> ustawienie <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> Będzie animowana przenieść <xref:System.Windows.Shapes.Rectangle> wokół <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Przykłady w tej sekcji wykorzystania poprzedniego obiektów w celu zademonstrowania kilka przypadków gdzie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości nie zachowywać się zgodnie z oczekiwaniami się.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Zatrzymaj" i HandoffBehavior za pomocą wielu animacji  
 Czasami wygląda tak, jakby ignoruje animacji jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości, gdy został zastąpiony przez drugiej animacji. Wykonaj poniższy przykład tworzy dwa <xref:System.Windows.Media.Animation.Storyboard> obiektów i używa ich, aby animować takie same <xref:System.Windows.Media.TranslateTransform> pokazano w powyższym przykładzie.  
  
 Pierwszy <xref:System.Windows.Media.Animation.Storyboard>, `B1`, animuje <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> od 0 do 350, który przesuwa pikseli prostokąt 350 po prawej stronie. Gdy dociera do końca jego czas trwania animacji i zatrzymuje odtwarzanie, <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość wraca do jego oryginalnej wartości 0. Co w efekcie prostokąta przenosi do pikseli po prawej stronie 350, a następnie skacze z powrotem do oryginalnego położenia.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Drugi <xref:System.Windows.Media.Animation.Storyboard>, `B2`, również animuje <xref:System.Windows.Media.TranslateTransform.X%2A> właściwości tego samego <xref:System.Windows.Media.TranslateTransform>. Ponieważ tylko <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości animacji w tym <xref:System.Windows.Media.Animation.Storyboard> jest ustawiony, animacji używa bieżącej wartości właściwości animuje go jako jej wartość początkową.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Jeśli klikniesz drugi przycisk, podczas pierwszego <xref:System.Windows.Media.Animation.Storyboard> jest odtwarzany, można by oczekiwać następujące zachowanie:  
  
1. Pierwszy scenorysu kończy i wysyła do jego pierwotnej pozycji prostokąt, ponieważ ma animacji <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2. Drugi scenorysu staje się skuteczny i animuje od bieżącej pozycji, która jest teraz 0 do 500.  
  
 **Ale to nie co się dzieje.** Zamiast tego prostokąta nie jest przenoszony wrócili, kontynuuje po prawej stronie. Wynika to z drugiej animacji używa bieżącej wartości animacji pierwszy jako jej wartość początkową i animuje z tej wartości do 500. Po drugiej animacji zastępuje pierwsze, ponieważ <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> jest używany, <xref:System.Windows.Media.Animation.FillBehavior> pierwszego animacji nie ma znaczenia.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior i ukończone zdarzenie  
 W następnych przykładach pokazują inny scenariusz, w którym <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> wydaje się mieć żadnego efektu. Ponownie w przykładzie użyto scenorysu, aby animować <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> od 0 do 350. Jednak tym razem przykład rejestruje <xref:System.Windows.Media.Animation.Timeline.Completed> zdarzeń.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Programu obsługi zdarzeń uruchamia inny <xref:System.Windows.Media.Animation.Storyboard> animuje, tę samą właściwość bieżącej wartości do 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Poniżej przedstawiono kod znaczników, który definiuje drugi <xref:System.Windows.Media.Animation.Storyboard> jako zasób.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Po uruchomieniu <xref:System.Windows.Media.Animation.Storyboard>, można by oczekiwać <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> animować z zakresu od 0 do 350, następnie przywróć 0 po jej zakończeniu (ponieważ ma ona <xref:System.Windows.Media.Animation.FillBehavior> ustawienie <xref:System.Windows.Media.Animation.FillBehavior.Stop>), a następnie animować z zakresu od 0 do 500. Zamiast tego <xref:System.Windows.Media.TranslateTransform> animuje z zakresu od 0 do 350, a następnie do 500.  
  
 Jest to spowodowane kolejność, w której [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wywołuje zdarzenia, a ponieważ wartości właściwości są buforowane, a nie są ponownie obliczane, chyba że właściwość zostaje unieważniony. <xref:System.Windows.Media.Animation.Timeline.Completed> Zdarzeń jest przetwarzana najpierw, ponieważ została wyzwolona przez oś czasu głównego (pierwszy <xref:System.Windows.Media.Animation.Storyboard>). W tej chwili <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość nadal zwraca wartość animowany, ponieważ nie zostały unieważnione jeszcze. Drugi <xref:System.Windows.Media.Animation.Storyboard> używa wartość w pamięci podręcznej jako jej wartość początkową i rozpoczyna się animowanie.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Wydajność  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animacje w dalszym uruchamiania po przejściu do strony  
 Po przejściu od <xref:System.Windows.Controls.Page> zawierającą uruchamianie animacji, te animacje będą w dalszym ciągu odtwarzanie do momentu <xref:System.Windows.Controls.Page> jest bezużyteczne. W zależności od używanego, system nawigacji strony, który możesz przejść od może pobytu w pamięci przez czas nieokreślony czas jednocześnie korzystanie z zasobów przy użyciu jego animacji. Jest to najbardziej zauważalne w przypadku, gdy strona zawiera stale uruchomione animacji ("otoczenia").  
  
 Z tego powodu jest dobry pomysł, aby użyć <xref:System.Windows.FrameworkElement.Unloaded> zdarzenie, aby usunąć animacji, gdy przejdziesz do innej strony.  
  
 Istnieją różne sposoby, aby usunąć animacji. Następujące techniki może służyć do usunięcia animacji, należących do <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Aby usunąć <xref:System.Windows.Media.Animation.Storyboard> wprowadzenie wyzwalacz zdarzenia, zobacz [jak: Usuń Scenorys](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
-   Aby użyć kodu, aby usunąć <xref:System.Windows.Media.Animation.Storyboard>, zobacz <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> metody.  
  
 Technika dalej, mogą być używane niezależnie od tego, jak animacja została uruchomiona.  
  
-   Aby usunąć animacji z określoną właściwość, należy użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody. Określa właściwość, jest animowany podczas pierwszego parametru i `null` jako drugiego. Spowoduje to usunięcie wszystkie zegary animacji z właściwości.  
  
 Aby uzyskać więcej informacji na temat różnych sposobów, aby animować właściwości, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Za pomocą narzędzia Compose HandoffBehavior wykorzystuje zasoby systemowe  
 Po zastosowaniu <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, lub <xref:System.Windows.Media.Animation.AnimationClock> za pomocą właściwości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>, any <xref:System.Windows.Media.Animation.Clock> obiektów była poprzednio skojarzona z tą właściwością, kontynuując zużywanie zasobów systemowych; nie będzie system chronometrażu automatyczne usuwanie zegary.  
  
 Aby uniknąć problemów z wydajnością, po zastosowaniu dużej liczby zegary przy użyciu <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, tworzenie zegary należy usunąć z animowanych właściwości po ich zakończeniu. Istnieje kilka sposobów, aby usunąć zegara.  
  
-   Aby usunąć wszystkie zegary z właściwością, należy użyć <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> lub <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metoda obiekt animowany. Określa właściwość, jest animowany podczas pierwszego parametru i `null` jako drugiego. Spowoduje to usunięcie wszystkie zegary animacji z właściwości.  
  
-   Aby usunąć określony <xref:System.Windows.Media.Animation.AnimationClock> z listy zegary, użyj <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.Animation.AnimationClock> można pobrać <xref:System.Windows.Media.Animation.ClockController>, następnie wywołać <xref:System.Windows.Media.Animation.ClockController.Remove%2A> metody <xref:System.Windows.Media.Animation.ClockController>. Jest to zazwyczaj wykonywane <xref:System.Windows.Media.Animation.Clock.Completed> program obsługi zdarzeń dla zegara. Należy pamiętać, że tylko zegary głównego można kontrolować, <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> zwróci właściwość zegara podrzędnych `null`. Należy zauważyć, że <xref:System.Windows.Media.Animation.Clock.Completed> zdarzenie nie zostanie wywołana, jeśli efektywnym czasem trwania zegara jest nieskończona.  W takim przypadku użytkownik musi określić, kiedy wywołać metodę <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Jest to głównie problemu dla animacji na obiekty, które mają długi okres istnienia.  Gdy obiekt jest bezużyteczne, jego zegary również zostanie odłączona i wyrzucania.  
  
 Aby uzyskać więcej informacji o obiektach zegara, zobacz [Animacja i System chronometrażu w — Przegląd](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
