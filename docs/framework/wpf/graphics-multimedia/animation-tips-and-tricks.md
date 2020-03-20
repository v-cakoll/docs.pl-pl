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
ms.openlocfilehash: 6b540448599c1e1083ed367a312ef60fceacd0d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187653"
---
# <a name="animation-tips-and-tricks"></a>Porady i triki animacyjne
Podczas pracy z animacjami w WPF, istnieje wiele wskazówek i wskazówek, które mogą sprawić, że animacje działają lepiej i zaoszczędzić frustrację.  
  
<a name="generalissuessection"></a>
## <a name="general-issues"></a>Ogólne problemy  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>Animowanie pozycji paska przewijania lub suwaka zawiesza go  
 Jeśli animujesz położenie paska przewijania lub suwaka <xref:System.Windows.Media.Animation.FillBehavior> przy <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> użyciu animacji, która ma (wartość domyślną), użytkownik nie będzie już mógł przesuwać paska przewijania lub suwaka. To dlatego, że mimo że animacja została zakończona, nadal zastępuje wartość bazową właściwości docelowej. Aby zatrzymać animację przed zastąpieniem bieżącej wartości właściwości, usuń <xref:System.Windows.Media.Animation.FillBehavior> ją <xref:System.Windows.Media.Animation.FillBehavior.Stop>lub nadaj jej wartość . Aby uzyskać więcej informacji i przykład, zobacz [Ustawianie właściwości po animowaniu jej za pomocą scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>Animowanie danych wyjściowych animacji nie ma wpływu  
 Nie można animować obiektu, który jest wynikiem innej animacji. Na przykład, jeśli <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> używasz do <xref:System.Windows.Shapes.Shape.Fill%2A> animowania <xref:System.Windows.Media.RadialGradientBrush> a <xref:System.Windows.Media.SolidColorBrush>od a <xref:System.Windows.Shapes.Rectangle> do , nie można <xref:System.Windows.Media.RadialGradientBrush> animować żadnych właściwości lub . <xref:System.Windows.Media.SolidColorBrush>  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>Nie można zmienić wartości właściwości po jej animowaniu  
 W niektórych przypadkach może się wydawać, że nie można zmienić wartości właściwości po jej animowane, nawet po zakończeniu animacji. To dlatego, że mimo że animacja została zakończona, nadal zastępuje wartość podstawową właściwości. Aby zatrzymać animację przed zastąpieniem bieżącej wartości właściwości, usuń <xref:System.Windows.Media.Animation.FillBehavior> ją <xref:System.Windows.Media.Animation.FillBehavior.Stop>lub nadaj jej wartość . Aby uzyskać więcej informacji i przykład, zobacz [Ustawianie właściwości po animowaniu jej za pomocą scenorysu](how-to-set-a-property-after-animating-it-with-a-storyboard.md).  
  
### <a name="changing-a-timeline-has-no-effect"></a>Zmiana osi czasu nie ma wpływu  
 Chociaż <xref:System.Windows.Media.Animation.Timeline> większość właściwości są animatable i mogą być powiązane z <xref:System.Windows.Media.Animation.Timeline> danymi, zmiana wartości właściwości active wydaje się nie mieć wpływu. To dlatego, że <xref:System.Windows.Media.Animation.Timeline> po rozpoczęciu, system chronometrażu sprawia, że kopię <xref:System.Windows.Media.Animation.Timeline> i używa go do utworzenia <xref:System.Windows.Media.Animation.Clock> obiektu. Modyfikacja oryginału nie ma wpływu na kopię systemu.  
  
 Aby <xref:System.Windows.Media.Animation.Timeline> odzwierciedlić zmiany, jego zegar musi być ponownie wygenerowany i używany do zastąpienia wcześniej utworzonego zegara. Zegary nie są generowane automatycznie. Oto kilka sposobów stosowania zmian osi czasu:  
  
- Jeśli oś czasu jest <xref:System.Windows.Media.Animation.Storyboard>lub należy do programu , można ją odzwierciedlić, ponownie stosując jej scenorys przy użyciu <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody lub metody. Ma to efekt uboczny również ponowne uruchomienie animacji. W kodzie można <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> użyć metody, aby przejść scenorysu z powrotem do poprzedniej pozycji.  
  
- Jeśli zastosowano animację bezpośrednio do <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> właściwości przy <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> użyciu metody, wywołaj metodę ponownie i przekaż ją animacji, która została zmodyfikowana.  
  
- Jeśli pracujesz bezpośrednio na poziomie zegara, utwórz i zastosuj nowy zestaw zegarów i użyj ich do zastąpienia poprzedniego zestawu wygenerowanych zegarów.  
  
 Aby uzyskać więcej informacji na temat osi czasu i zegarów, zobacz [Omówienie systemu animacji i chronometrażu](animation-and-timing-system-overview.md).  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop nie działa zgodnie z oczekiwaniami  
 Istnieją chwile, gdy <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ustawienie <xref:System.Windows.Media.Animation.FillBehavior.Stop> właściwości wydaje się nie mieć wpływu, na przykład gdy jedna <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> animacja "ręce off" do innego, ponieważ ma ustawienie <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.  
  
 Poniższy przykład <xref:System.Windows.Controls.Canvas>tworzy <xref:System.Windows.Shapes.Rectangle> , <xref:System.Windows.Media.TranslateTransform>a i . Będzie <xref:System.Windows.Media.TranslateTransform> animowany, aby <xref:System.Windows.Shapes.Rectangle> poruszać <xref:System.Windows.Controls.Canvas>się wokół .  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 Przykłady w tej sekcji użyć poprzednich obiektów, aby <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> zademonstrować kilka przypadków, w których właściwość nie zachowuje się tak, jak można oczekiwać.  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>FillBehavior="Stop" i HandoffBehavior z wieloma animacjami  
 Czasami wydaje się, że animacja ignoruje jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości, gdy jest zastępowany przez drugą animację. Weźmy następujący przykład, <xref:System.Windows.Media.Animation.Storyboard> który tworzy dwa obiekty i <xref:System.Windows.Media.TranslateTransform> używa ich do animowania tego samego pokazano w poprzednim przykładzie.  
  
 Pierwszy <xref:System.Windows.Media.Animation.Storyboard>, `B1`animuje <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform> od 0 do 350, która przesuwa prostokąt 350 pikseli w prawo. Gdy animacja osiągnie koniec czasu trwania i <xref:System.Windows.Media.TranslateTransform.X%2A> przestaje grać, właściwość powraca do pierwotnej wartości, 0. W rezultacie prostokąt przesuwa się w prawo 350 pikseli, a następnie przeskakuje z powrotem do swojej pierwotnej pozycji.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 Drugi <xref:System.Windows.Media.Animation.Storyboard>, `B2`również animuje <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość <xref:System.Windows.Media.TranslateTransform>tego samego . Ponieważ ustawiono <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> tylko właściwość <xref:System.Windows.Media.Animation.Storyboard> animacji w tym, animacja używa bieżącej wartości właściwości, która animuje jako swoją wartość początkową.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 Jeśli klikniesz drugi <xref:System.Windows.Media.Animation.Storyboard> przycisk podczas odtwarzania pierwszego, możesz spodziewać się następującego zachowania:  
  
1. Pierwsza scenorysu kończy się i wysyła prostokąt z powrotem <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> do <xref:System.Windows.Media.Animation.FillBehavior.Stop>jego pierwotnej pozycji, ponieważ animacja ma .  
  
2. Drugi scenorysu staje się skuteczne i animuje z bieżącej pozycji, która jest teraz 0, do 500.  
  
 **Ale tak się nie dzieje.** Zamiast tego prostokąt nie przeskakuje z powrotem; nadal przesuwa się w prawo. To dlatego, że druga animacja używa bieżącej wartości pierwszej animacji jako wartości początkowej i animuje od tej wartości do 500. Gdy druga animacja zastępuje pierwszą, <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior> ponieważ <xref:System.Windows.Media.Animation.FillBehavior> jest używana, pierwsza animacja nie ma znaczenia.  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior i zakończone wydarzenie  
 Następne przykłady pokazują inny scenariusz, <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> w którym wydaje się nie mieć wpływu. Ponownie w przykładzie używa scenorysu <xref:System.Windows.Media.TranslateTransform.X%2A> do <xref:System.Windows.Media.TranslateTransform> animowania właściwości od 0 do 350. Jednak tym razem przykład rejestruje <xref:System.Windows.Media.Animation.Timeline.Completed> dla zdarzenia.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 Program <xref:System.Windows.Media.Animation.Timeline.Completed> obsługi zdarzeń <xref:System.Windows.Media.Animation.Storyboard> rozpoczyna inny, który animuje tę samą właściwość od jego bieżącej wartości do 500.  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 Poniżej znajduje się znaczników, <xref:System.Windows.Media.Animation.Storyboard> który definiuje drugi jako zasób.  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 Po uruchomieniu <xref:System.Windows.Media.Animation.Storyboard>, <xref:System.Windows.Media.TranslateTransform.X%2A> można <xref:System.Windows.Media.TranslateTransform> oczekiwać, że właściwość do animowania od 0 do 350, a następnie <xref:System.Windows.Media.Animation.FillBehavior> powrócić <xref:System.Windows.Media.Animation.FillBehavior.Stop>do 0 po zakończeniu (ponieważ ma ustawienie ), a następnie animować od 0 do 500. Zamiast tego <xref:System.Windows.Media.TranslateTransform> animuje od 0 do 350, a następnie do 500.  
  
 Wynika to z kolejności, w której WPF WPF wywołuje zdarzenia i ponieważ wartości właściwości są buforowane i nie są ponownie obliczane, chyba że właściwość jest unieważniona. Zdarzenie <xref:System.Windows.Media.Animation.Timeline.Completed> jest przetwarzane najpierw, ponieważ zostało wywołane przez <xref:System.Windows.Media.Animation.Storyboard>główną oś czasu (pierwszy ). W tej chwili <xref:System.Windows.Media.TranslateTransform.X%2A> właściwość nadal zwraca jego animowaną wartość, ponieważ nie została jeszcze unieważniona. Drugi <xref:System.Windows.Media.Animation.Storyboard> używa buforowanej wartości jako wartości początkowej i rozpoczyna animowanie.  
  
<a name="performancesection"></a>
## <a name="performance"></a>Wydajność  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>Animacje nadal działać po nawigowaniu z dala od strony  
 Po przejściu <xref:System.Windows.Controls.Page> od animacji, która zawiera uruchomione animacje, <xref:System.Windows.Controls.Page> te animacje będą nadal odtwarzane, dopóki nie jest zbierane śmieci. W zależności od używanego systemu nawigacji strona, z której możesz się odejść, może pozostać w pamięci przez nieokreślony czas, a jednocześnie zużywa zasoby z animacjami. Jest to najbardziej zauważalne, gdy strona zawiera stale uruchomione ("otoczenie") animacje.  
  
 Z tego powodu warto użyć zdarzenia do <xref:System.Windows.FrameworkElement.Unloaded> usuwania animacji podczas odejdy ze strony.  
  
 Istnieją różne sposoby usuwania animacji. Następujące techniki mogą być używane do usuwania <xref:System.Windows.Media.Animation.Storyboard>animacji, które należą do pliku .  
  
- Aby usunąć <xref:System.Windows.Media.Animation.Storyboard> rozpoczęty od wyzwalacza zdarzenia, zobacz [Jak: Usuwanie scenorysu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749412(v=vs.90)).  
  
- Aby użyć kodu, <xref:System.Windows.Media.Animation.Storyboard>aby <xref:System.Windows.Media.Animation.Storyboard.Remove%2A> usunąć , zobacz metodę.  
  
 Następna technika może być używana niezależnie od sposobu rozpoczęcia animacji.  
  
- Aby usunąć animacje z określonej <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> właściwości, użyj metody. Określ właściwość animowaną jako `null` pierwszy parametr i jako drugi. Spowoduje to usunięcie wszystkich zegarów animacji z właściwości.  
  
 Aby uzyskać więcej informacji na temat różnych sposobów animowania właściwości, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>Korzystanie z funkcji KomponowanieZastosowanie zużywa zasoby systemowe  
 Po zastosowaniu <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.AnimationTimeline>, <xref:System.Windows.Media.Animation.AnimationClock> lub do właściwości <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>przy <xref:System.Windows.Media.Animation.Clock> użyciu , wszystkie obiekty wcześniej skojarzone z tą właściwością nadal zużywają zasoby systemowe; system pomiaru czasu nie usunie tych zegarów automatycznie.  
  
 Aby uniknąć problemów z wydajnością podczas stosowania <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>dużej liczby zegarów przy użyciu , należy usunąć zegary redagowania z animowanej właściwości po ich zakończeniu. Istnieje kilka sposobów, aby usunąć zegar.  
  
- Aby usunąć wszystkie zegary z <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> właściwości, użyj lub <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metody animowanego obiektu. Określ właściwość animowaną jako `null` pierwszy parametr i jako drugi. Spowoduje to usunięcie wszystkich zegarów animacji z właściwości.  
  
- Aby usunąć <xref:System.Windows.Media.Animation.AnimationClock> określony z listy zegarów, <xref:System.Windows.Media.Animation.Clock.Controller%2A> użyj <xref:System.Windows.Media.Animation.AnimationClock> właściwości, aby <xref:System.Windows.Media.Animation.ClockController>pobrać , <xref:System.Windows.Media.Animation.ClockController.Remove%2A> a <xref:System.Windows.Media.Animation.ClockController>następnie wywołać metodę . Jest to zazwyczaj wykonywane <xref:System.Windows.Media.Animation.Clock.Completed> w programie obsługi zdarzeń dla zegara. Należy zauważyć, że tylko zegary <xref:System.Windows.Media.Animation.ClockController>główne mogą być kontrolowane przez ; właściwość <xref:System.Windows.Media.Animation.Clock.Controller%2A> zegara dziecka `null`powróci . Należy również <xref:System.Windows.Media.Animation.Clock.Completed> zauważyć, że zdarzenie nie zostanie wywołane, jeśli efektywny czas trwania zegara jest na zawsze.  W takim przypadku użytkownik będzie musiał określić, kiedy zadzwonić <xref:System.Windows.Media.Animation.ClockController.Remove%2A>.  
  
 Jest to przede wszystkim problem dla animacji na obiektach, które mają długi okres istnienia.  Gdy obiekt jest zbierane śmieci, jego zegary będą również odłączone i śmieci zebrane.  
  
 Aby uzyskać więcej informacji na temat obiektów zegara, zobacz [Omówienie systemu animacji i chronometrażu](animation-and-timing-system-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
