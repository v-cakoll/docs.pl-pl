---
title: Porady i triki animacyjne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fceebbd3da7a0643e744d80a55cb1c953eba3bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="animation-tips-and-tricks"></a>Porady i triki animacyjne
Podczas pracy z animacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], istnieje wiele porady i wskazówki, które mogą ułatwić animacji działać lepiej i zaoszczędzić frustracji spowodowanej.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Ogólne problemy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animowanie pozycja paska przewijania lub suwaka zawiesza się go  
 Animacja pozycja paska przewijania lub suwaka przy użyciu animacji, które ma <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (wartość domyślna), użytkownik nie będzie już możliwe przeniesienie paska przewijania lub suwaka. Wynika to z, nawet jeśli została zakończona Animacja, nadal jest zastąpienie wartości podstawowej właściwość target. Aby zatrzymać animacji zastępowaniu bieżącą wartość właściwości, usuń go lub nadaj <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Aby uzyskać więcej informacji i przykład zobacz [Ustaw właściwości po animacji scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Dane wyjściowe animacji animacji nie ma wpływu  
 Nie można animować obiekt, który jest wysyłany innej animacji. Na przykład, jeśli używasz <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> do animowania <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Media.RadialGradientBrush> do <xref:System.Windows.Media.SolidColorBrush>, nie można animować właściwości z <xref:System.Windows.Media.RadialGradientBrush> lub <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nie można zmienić wartości właściwości po jego animacji  
 W niektórych przypadkach może pojawiać się, że nie można zmienić wartości właściwości jest zostały animowany, nawet po zakończeniu animacji. Wynika to z, nawet jeśli została zakończona Animacja, nadal jest zastępowanie podstawową wartość właściwości. Aby zatrzymać animacji zastępowaniu bieżącą wartość właściwości, usuń go lub nadaj <xref:System.Windows.Media.Animation.FillBehavior> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Aby uzyskać więcej informacji i przykład zobacz [Ustaw właściwości po animacji scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Zmiana oś czasu nie obowiązuje  
 Mimo że większość <xref:System.Windows.Media.Animation.Timeline> są można animować właściwości i może być powiązany z danymi, zmiana wartości właściwości aktywnego <xref:System.Windows.Media.Animation.Timeline> wydaje się nie mają żadnego skutku. Jest to spowodowane tym, kiedy <xref:System.Windows.Media.Animation.Timeline> jest uruchomione, system chronometrażu tworzy kopię <xref:System.Windows.Media.Animation.Timeline> i używa jej do utworzenia <xref:System.Windows.Media.Animation.Clock> obiektu. Modyfikowanie oryginalny nie ma wpływu na system kopiowania.  
  
 Aby uzyskać <xref:System.Windows.Media.Animation.Timeline> celu odzwierciedlenia zmian, jego zegara muszą być ponownie wygenerowany i używany do zastępowania poprzednio utworzone zegara. Zegary nie są automatycznie generowane automatycznie. Poniżej przedstawiono kilka sposobów, aby zastosować zmiany osi czasu:  
  
-   Jeśli oś czasu jest lub należy do <xref:System.Windows.Media.Animation.Storyboard>, można tworzyć i odzwierciedlenia zmian przez ponowne zastosowanie przy użyciu jego scenorysu <xref:System.Windows.Media.Animation.BeginStoryboard> lub <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody. To ustawienie działa po stronie również ponownego uruchomienia animacji. W kodzie, można użyć <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> metodę scenorysu z powrotem do jego poprzedniej pozycji.  
  
-   Jeśli wybrano animację bezpośrednio do właściwości przy użyciu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody, wywołaj <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody ponownie i przekaż go animacji, które zostały zmodyfikowane.  
  
-   Podczas pracy bezpośrednio na poziomie zegara, utworzyć i zastosować nowy zestaw zegary i używać ich do zastąpienia poprzedniego zestawu wygenerowanego zegary.  
  
 Aby uzyskać więcej informacji o osiach czasu i zegary, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop nie działa zgodnie z oczekiwaniami  
 Czasami podczas ustawiania <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości <xref:System.Windows.Media.Animation.FillBehavior.Stop> wydaje się nie przyniosło żadnego skutku, takie jak kiedy jeden animacji "przekazuje" do innego, ponieważ ma on <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> ustawienie <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> Będzie animowany można przenieść <xref:System.Windows.Shapes.Rectangle> wokół <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Przykłady w tej sekcji prezentacja kilku przypadkach za pomocą poprzedniego obiektów gdzie <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości nie działają zgodnie z oczekiwaniami może go do.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Stop" i HandoffBehavior wielu animacji  
 Czasami wygląda tak, jakby ignoruje animacji jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości, gdy zostanie zastąpiony przez animację drugiego. Wykonać poniższy przykład tworzy dwa <xref:System.Windows.Media.Animation.Storyboard> obiekty i używa ich do animowania takie same <xref:System.Windows.Media.TranslateTransform> w poprzednim przykładzie.  
  
 Pierwszy <xref:System.Windows.Media.Animation.Storyboard>, `B1`, animuje <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> od 0 do 350, który przesuwa prostokąt 350 pikseli w prawo. Gdy dociera do końca jego czas trwania animacji i zatrzymuje odtwarzanie, <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość zostanie przywrócony do jego oryginalnej wartości 0. W związku z tym prostokąt przenosi do prawej 350 pikseli, a następnie przechodzi wstecz do oryginalnego położenia.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Drugi <xref:System.Windows.Media.Animation.Storyboard>, `B2`, również animuje <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość tego samego <xref:System.Windows.Media.TranslateTransform>. Ponieważ tylko <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości animacji w tym <xref:System.Windows.Media.Animation.Storyboard> jest ustawione animacji używa bieżącą wartość właściwości animuje go jako swojej wartości początkowej.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Jeśli klikniesz przycisk drugi podczas pierwszego <xref:System.Windows.Media.Animation.Storyboard> jest odtwarzany, może spodziewać następujące działania:  
  
1.  Pierwszy scenorysu kończy się i wysyła prostokąt z powrotem do oryginalnego położenia, ponieważ ma animacji <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2.  Drugi scenorysu obowiązuje i animuje z bieżącą pozycję, która jest teraz 0 do 500.  
  
 **Jednak to nie to, co się stanie.** Zamiast tego prostokąta nie przejść wstecz; nadal przesunięcie w prawo. Wynika to z drugiego animacji używa bieżącej wartości pierwszego animacji jako jego wartość początkową i animuje z tej wartości do 500. Gdy drugi animacji zastępuje pierwszy, ponieważ <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> jest używana, <xref:System.Windows.Media.Animation.FillBehavior> pierwszego animacji nie ma znaczenia.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior i zakończonego zdarzenia  
 Następny przykłady przedstawiają inny scenariusz, w którym <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> wydaje się nie mają żadnego skutku. Ponownie w przykładzie użyto scenorysu do animowania <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> od 0 do 350. Jednak teraz przykładzie rejestruje <xref:System.Windows.Media.Animation.Timeline.Completed> zdarzeń.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> Uruchamia inny proces programu obsługi zdarzeń <xref:System.Windows.Media.Animation.Storyboard> który animuje tej samej właściwości z bieżącą wartość 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Poniżej znajduje się kod znaczników, który definiuje drugi <xref:System.Windows.Media.Animation.Storyboard> jako zasób.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Po uruchomieniu <xref:System.Windows.Media.Animation.Storyboard>, może spodziewać się <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> Aby animować z zakresu od 0 do 350, przywrócenie 0 po jej zakończeniu (ponieważ ma ona <xref:System.Windows.Media.Animation.FillBehavior> ustawienie <xref:System.Windows.Media.Animation.FillBehavior.Stop>), następnie animować z zakresu od 0 do 500. Zamiast tego <xref:System.Windows.Media.TranslateTransform> animuje z zakresu od 0 do 350, a następnie do 500.  
  
 Jest to spowodowane w kolejności [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] informuje o zdarzeniach i ponieważ wartości właściwości są buforowane, a nie są obliczenia, chyba że właściwość jest unieważnione. <xref:System.Windows.Media.Animation.Timeline.Completed> Zdarzeń jest przetwarzana najpierw, ponieważ zostało wyzwolone na osi czasu głównego (pierwszy <xref:System.Windows.Media.Animation.Storyboard>). W tej chwili <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość nadal zwraca wartość animowany, ponieważ nie została unieważniona jeszcze. Drugi <xref:System.Windows.Media.Animation.Storyboard> wartość w pamięci podręcznej jest używana jako jego wartość początkową i rozpocznie się animacji.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Wydajność  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animacje kontynuować do uruchomienia po Nawigacja strony  
 Po przejściu od <xref:System.Windows.Controls.Page> zawierających animacje uruchomione, animacje te będą w dalszym ciągu odtwarzania do <xref:System.Windows.Controls.Page> jest bezużytecznych. W zależności od używanego, system nawigacji strony, która przejdź od może Pozostań w pamięci przez nieokreślony czas, jednocześnie korzysta z zasobów z jego animacji. Jest to najbardziej zauważalne, gdy strona zawiera stale uruchomione animacji ("otoczenia").  
  
 Z tego powodu jest warto użyć <xref:System.Windows.FrameworkElement.Unloaded> zdarzeń do usunięcia animacji, gdy opuścić stronę.  
  
 Istnieją różne sposoby, aby usunąć animacji. Następujące techniki może służyć do usunięcia animacji, które należą do <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Aby usunąć <xref:System.Windows.Media.Animation.Storyboard> wprowadzenie wyzwalacz zdarzeń, zobacz [porady: usuwanie scenorysu](http://msdn.microsoft.com/en-us/7fe39531-de2f-46a0-a69f-b783d04235ee).  
  
-   Aby usunąć przy użyciu kodu <xref:System.Windows.Media.Animation.Storyboard>, zobacz <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> metody.  
  
 Techniki dalej mogą być używane niezależnie od sposobu uruchomienia animacji.  
  
-   Aby usunąć animacje z określoną właściwość, należy użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody. Określ właściwość animowanej jako pierwszego parametru oraz `null` jako drugiego. Spowoduje to usunięcie wszystkich zegary animacji z właściwości.  
  
 Aby uzyskać więcej informacji o różnych sposobach animowania właściwości, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Przy użyciu tworzą HandoffBehavior wykorzystuje zasoby systemowe  
 Po zastosowaniu <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>, lub <xref:System.Windows.Media.Animation.AnimationClock> je przy użyciu właściwości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>oraz <xref:System.Windows.Media.Animation.Clock> obiekty wcześniej skojarzone z tą właściwością nadal zużywają zasoby systemowe; system czasu nie będzie Usuń zegary automatycznie.  
  
 Aby uniknąć problemów z wydajnością podczas stosowania dużej liczby zegary przy użyciu <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, tworzenie zegary należy usunąć z właściwości animowany po ich zakończeniu. Istnieje kilka sposobów, aby usunąć zegara.  
  
-   Aby usunąć wszystkie zegary z właściwości, należy użyć <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> lub <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody animowany obiektu. Określ właściwość animowanej jako pierwszego parametru oraz `null` jako drugiego. Spowoduje to usunięcie wszystkich zegary animacji z właściwości.  
  
-   Aby usunąć określony <xref:System.Windows.Media.Animation.AnimationClock> z listy zegary, użyj <xref:System.Windows.Media.Animation.Clock.Controller%2A> właściwość <xref:System.Windows.Media.Animation.AnimationClock> można pobrać <xref:System.Windows.Media.Animation.ClockController>, następnie wywołaj <xref:System.Windows.Media.Animation.ClockController.Remove%2A> metody <xref:System.Windows.Media.Animation.ClockController>. Jest to zazwyczaj wykonywane <xref:System.Windows.Media.Animation.Clock.Completed> programu obsługi zdarzeń dla zegara. Należy pamiętać, że tylko zegary głównego mogą być kontrolowane przez <xref:System.Windows.Media.Animation.ClockController>; <xref:System.Windows.Media.Animation.Clock.Controller%2A> zwróci właściwości zegara podrzędnych `null`. Należy zauważyć, że <xref:System.Windows.Media.Animation.Clock.Completed> zdarzenie nie zostanie wywołany, jeśli efektywny czas trwania zegar jest nieskończoność.  W takim przypadku użytkownik musi określić, kiedy wywołać metodę <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 To przede wszystkim problemu dla animacji na obiektach, które mają długi okres istnienia.  Gdy obiekt jest bezużytecznych, jego zegary również zostanie rozłączona i w ramach odzyskiwania pamięci.  
  
 Aby uzyskać więcej informacji o obiektach zegara, zobacz [animacji i Przegląd systemu chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
