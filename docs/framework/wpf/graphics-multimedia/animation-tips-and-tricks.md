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
ms.openlocfilehash: ef59631663e6cf1c98adfed77a2dbdb6ca124fa1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636032"
---
# <a name="animation-tips-and-tricks"></a>Porady i triki animacyjne
Podczas pracy z animacjami w języku WPF istnieje kilka porad i wskazówek, które mogą usprawnić wykonywanie animacji i zaoszczędzić frustrację.  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>Ogólne problemy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animowanie położenia paska przewijania lub suwaka powoduje jego zablokowanie  
 W przypadku animowania położenia paska przewijania lub suwaka przy użyciu animacji, która ma <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> (wartość domyślna), użytkownik nie będzie już mógł przenosić paska przewijania ani suwaka. To dlatego, że mimo że animacja zakończyła się, nadal zastępuje wartość bazową właściwości docelowej. Aby zatrzymać animację zastępującą bieżącą wartość właściwości, usuń ją lub nadaj <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [Ustawianie właściwości po animacji przy użyciu scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animowanie danych wyjściowych animacji nie ma żadnego wpływu  
 Nie można animować obiektu, który jest wyjściem innej animacji. Na przykład w przypadku użycia <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> do animowania <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Media.RadialGradientBrush> do <xref:System.Windows.Media.SolidColorBrush>nie można animować właściwości <xref:System.Windows.Media.RadialGradientBrush> ani <xref:System.Windows.Media.SolidColorBrush>.  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nie można zmienić wartości właściwości po jej animacji  
 W niektórych przypadkach może się zdarzyć, że nie można zmienić wartości właściwości po jej animowaniu, nawet po zakończeniu animacji. To dlatego, że mimo że animacja zakończyła się, nadal zastępuje wartość podstawową właściwości. Aby zatrzymać animację zastępującą bieżącą wartość właściwości, usuń ją lub nadaj <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [Ustawianie właściwości po animacji przy użyciu scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Zmiana osi czasu nie ma wpływu  
 Chociaż większość <xref:System.Windows.Media.Animation.Timeline> właściwości są animowane i mogą być powiązane z danymi, zmiana wartości właściwości aktywnego <xref:System.Windows.Media.Animation.Timeline> wydaje się nie mieć żadnego efektu. Dzieje się tak, ponieważ po rozpoczęciu <xref:System.Windows.Media.Animation.Timeline>, system chronometrażu tworzy kopię <xref:System.Windows.Media.Animation.Timeline> i używa jej do utworzenia obiektu <xref:System.Windows.Media.Animation.Clock>. Modyfikowanie oryginału nie ma wpływu na kopię systemu.  
  
 Aby <xref:System.Windows.Media.Animation.Timeline> odzwierciedlały zmiany, jego zegar musi być ponownie wygenerowany i użyty do zamienienia wcześniej utworzonego zegara. Zegary nie są ponownie generowane automatycznie. Poniżej przedstawiono kilka sposobów stosowania zmian osi czasu:  
  
- Jeśli oś czasu jest lub należy do <xref:System.Windows.Media.Animation.Storyboard>, możesz wprowadzić zmiany przez ponowne zastosowanie jej scenorysu przy użyciu metody <xref:System.Windows.Media.Animation.BeginStoryboard> lub <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>. Powoduje to również ponowne uruchomienie animacji. W kodzie, można użyć metody <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>, aby przejść do poprzedniej pozycji scenorysu.  
  
- Jeśli zastosowano animację bezpośrednio do właściwości przy użyciu metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>, należy ponownie wywołać metodę <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> i przekazać ją do zmodyfikowanej animacji.  
  
- Jeśli pracujesz bezpośrednio na poziomie zegara, Utwórz i Zastosuj nowy zestaw zegarów i użyj ich, aby zastąpić poprzedni zestaw generowanych zegarami.  
  
 Aby uzyskać więcej informacji na temat osi czasu i zegarów, zobacz [Omówienie animacji i systemu chronometrażu](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior. Stop nie działa zgodnie z oczekiwaniami  
 Istnieją przypadki, gdy ustawienie właściwości <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> na <xref:System.Windows.Media.Animation.FillBehavior.Stop> prawdopodobnie nie ma żadnego efektu, na przykład gdy jedna animacja "jest wyłączona", ponieważ ma <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> ustawienie <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Shapes.Rectangle> i <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.TranslateTransform> będzie animowany, aby przenieść <xref:System.Windows.Shapes.Rectangle> wokół <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 W przykładach w tej sekcji użyto powyższych obiektów do zademonstrowania kilku przypadków, w których właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> nie zachowuje się, ponieważ może to oczekiwać.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior = "Stop" i HandoffBehavior z wieloma animacjami  
 Czasami wydaje się, że animacja ignoruje swoją właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>, gdy zostanie zastąpiona przez drugą animację. Zrób Poniższy przykład, który tworzy dwa <xref:System.Windows.Media.Animation.Storyboard> obiekty i używa ich do animowania tego samego <xref:System.Windows.Media.TranslateTransform> pokazanego w poprzednim przykładzie.  
  
 Pierwszy <xref:System.Windows.Media.Animation.Storyboard>, `B1`, Animuj Właściwość <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> od 0 do 350, co przenosi prostokąt 350 pikseli w prawo. Gdy animacja osiągnie koniec czasu trwania i zakończy odtwarzanie, właściwość <xref:System.Windows.Media.TranslateTransform.X%2A> przywraca oryginalną wartość, 0. W związku z tym prostokąt przechodzi do prawej 350 pikseli, a następnie przechodzi z powrotem do oryginalnego położenia.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Druga <xref:System.Windows.Media.Animation.Storyboard>, `B2`, Animuj również właściwość <xref:System.Windows.Media.TranslateTransform.X%2A> tego samego <xref:System.Windows.Media.TranslateTransform>. Ponieważ ustawiana jest tylko Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> animacji w tym <xref:System.Windows.Media.Animation.Storyboard>, animacja używa bieżącej wartości właściwości, którą Animuj jako jej wartość początkową.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Jeśli klikniesz drugi przycisk podczas odtwarzania pierwszej <xref:System.Windows.Media.Animation.Storyboard>, możesz oczekiwać, że następujące zachowanie:  
  
1. Pierwszy scenorys kończy się i wysyła prostokąt z powrotem do jego oryginalnego położenia, ponieważ animacja ma <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.Stop>.  
  
2. Drugi scenorys zacznie obowiązywać i Animuj od bieżącego położenia, czyli od 0 do 500.  
  
 **Ale tak się nie dzieje.** Zamiast tego prostokąt nie przeskoczy do tyłu; kontynuuje przejście w prawo. Wynika to z faktu, że druga animacja używa bieżącej wartości pierwszej animacji jako wartości początkowej i Animuj od tej wartości do 500. Gdy druga animacja zastępuje pierwszą, ponieważ jest używana <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace><xref:System.Windows.Media.Animation.HandoffBehavior>, <xref:System.Windows.Media.Animation.FillBehavior> pierwszej animacji nie ma znaczenia.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior i ukończone zdarzenie  
 W następnych przykładach przedstawiono inny scenariusz, w którym <xref:System.Windows.Media.Animation.FillBehavior.Stop><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> wydaje się, że nie ma żadnego wpływu. Ponownie, w przykładzie używa scenorysu do animowania właściwości <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> z 0 do 350. Jednak ten czas rejestruje przykład dla zdarzenia <xref:System.Windows.Media.Animation.Timeline.Completed>.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Procedura obsługi zdarzeń <xref:System.Windows.Media.Animation.Timeline.Completed> uruchamia kolejną <xref:System.Windows.Media.Animation.Storyboard>, która animować tę samą właściwość z bieżącej wartości do 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Poniżej znajduje się znacznik, który definiuje drugi <xref:System.Windows.Media.Animation.Storyboard> jako zasób.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Po uruchomieniu <xref:System.Windows.Media.Animation.Storyboard>można oczekiwać, że właściwość <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform> była Animuj z 0 na 350, a następnie wraca do 0 po zakończeniu (ponieważ ma ustawienie <xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.FillBehavior.Stop>), a następnie Animuj od 0 do 500. Zamiast tego <xref:System.Windows.Media.TranslateTransform> jest animowany od 0 do 350, a następnie do 500.  
  
 Wynika to z kolejności, w której WPF zgłasza zdarzenia i ponieważ wartości właściwości są buforowane i nie są ponownie obliczane, chyba że właściwość jest unieważniona. Zdarzenie <xref:System.Windows.Media.Animation.Timeline.Completed> jest przetwarzane jako pierwsze, ponieważ zostało wyzwolone przez główną oś czasu (pierwszy <xref:System.Windows.Media.Animation.Storyboard>). W tej chwili Właściwość <xref:System.Windows.Media.TranslateTransform.X%2A> nadal zwraca wartość animowaną, ponieważ nie została jeszcze unieważniona. Druga <xref:System.Windows.Media.Animation.Storyboard> używa wartości z pamięci podręcznej jako wartości początkowej i rozpoczyna animację.  
  
<a name="performancesection"></a>   
## <a name="performance"></a>Wydajność  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animacje są nadal uruchamiane po przejściu ze strony  
 Gdy przejdziesz do <xref:System.Windows.Controls.Page>, który zawiera uruchomione animacje, te animacje będą nadal odtwarzane do momentu, gdy <xref:System.Windows.Controls.Page> nie zostaną pobrane jako elementy bezużyteczne. W zależności od używanego systemu nawigacji, Strona, do której się odszedł, może pozostawać w pamięci przez czas nieokreślony, a wszystkie zasoby zużywające te animacje. Jest to najbardziej zauważalne, gdy strona zawiera stale działające ("otoczenia") animacje.  
  
 Z tego powodu dobrym pomysłem jest użycie zdarzenia <xref:System.Windows.FrameworkElement.Unloaded>, aby usunąć animacje w przypadku opuszczenia strony.  
  
 Istnieją różne sposoby usuwania animacji. Poniższe techniki mogą służyć do usuwania animacji, które należą do <xref:System.Windows.Media.Animation.Storyboard>.  
  
- Aby usunąć <xref:System.Windows.Media.Animation.Storyboard> rozpoczęte z wyzwalaczem zdarzeń, zobacz [How to: Remove an scenorys](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Aby użyć kodu do usunięcia <xref:System.Windows.Media.Animation.Storyboard>, zobacz <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> metody.  
  
 Następny technikę można zastosować niezależnie od sposobu uruchomienia animacji.  
  
- Aby usunąć animacje z określonej właściwości, użyj metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>. Określ animowaną właściwość jako pierwszy parametr, a `null` jako sekundę. Spowoduje to usunięcie wszystkich zegarów animacji z właściwości.  
  
 Aby uzyskać więcej informacji na temat różnych sposobów animacji właściwości, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Korzystanie z HandoffBehavior redagowania zużywa zasoby systemowe  
 Po zastosowaniu <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.Animation.AnimationTimeline>lub <xref:System.Windows.Media.Animation.AnimationClock> do właściwości przy użyciu <xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>wszystkie obiekty <xref:System.Windows.Media.Animation.Clock> wcześniej skojarzone z tą właściwością nadal zużywają zasoby systemowe; System chronometrażu nie spowoduje automatycznego usunięcia tych zegarów.  
  
 Aby uniknąć problemów z wydajnością podczas stosowania dużej liczby zegarów przy użyciu <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>, należy usunąć zegary redagowania z właściwości animowanej po ich zakończeniu. Istnieje kilka sposobów usunięcia zegara.  
  
- Aby usunąć wszystkie zegary z właściwości, użyj metody <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> lub <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> animowanego obiektu. Określ animowaną właściwość jako pierwszy parametr, a `null` jako sekundę. Spowoduje to usunięcie wszystkich zegarów animacji z właściwości.  
  
- Aby usunąć określony <xref:System.Windows.Media.Animation.AnimationClock> z listy zegarów, użyj właściwości <xref:System.Windows.Media.Animation.Clock.Controller%2A> <xref:System.Windows.Media.Animation.AnimationClock>, aby pobrać <xref:System.Windows.Media.Animation.ClockController>, a następnie Wywołaj metodę <xref:System.Windows.Media.Animation.ClockController.Remove%2A> <xref:System.Windows.Media.Animation.ClockController>. Jest to zazwyczaj wykonywane w obsłudze zdarzeń <xref:System.Windows.Media.Animation.Clock.Completed> dla zegara. Należy pamiętać, że tylko zegary główne mogą być kontrolowane przez <xref:System.Windows.Media.Animation.ClockController>; Właściwość <xref:System.Windows.Media.Animation.Clock.Controller%2A> zegara podrzędnego zwróci `null`. Należy zauważyć, że zdarzenie <xref:System.Windows.Media.Animation.Clock.Completed> nie zostanie wywołane, jeśli czynny czas trwania zegara jest nieograniczona.  W takim przypadku użytkownik będzie musiał określić, kiedy ma być wywoływana <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Jest to szczególnie problem w przypadku animacji na obiektach, które mają długi okres istnienia.  Gdy obiekt jest odzyskiwany, jego zegary również zostaną rozłączone i zostaną pobrane jako elementy bezużyteczne.  
  
 Aby uzyskać więcej informacji na temat obiektów zegara, zobacz [animacje i system chronometrażu — przegląd](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
