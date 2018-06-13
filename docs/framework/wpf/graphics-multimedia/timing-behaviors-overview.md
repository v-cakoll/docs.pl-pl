---
title: Przegląd Zachowania chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 31a6b7d3b92e886d9c90fc39d69f31cf72b99666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566327"
---
# <a name="timing-behaviors-overview"></a>Przegląd Zachowania chronometrażu
W tym temacie opisano zachowania chronometrażu animacji i innych <xref:System.Windows.Media.Animation.Timeline> obiektów.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z funkcjami podstawowe animacji. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Typy osi czasu  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu. Zapewnia właściwości, które umożliwiają określenie tego segmentu, gdy jej powinna zaczynać się, ile razy powtarza, szybkość postępu czasu w tym segmencie i inne.  
  
 Klasy, które dziedziczą z klasy osi czasu zapewniają dodatkowe funkcje, takie jak odtwarzanie animacji i nośnika. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące <xref:System.Windows.Media.Animation.Timeline> typów.  
  
|Typ osi czasu|Opis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstrakcyjna klasa podstawowa dla <xref:System.Windows.Media.Animation.Timeline> obiektów, które generują dane wyjściowe wartości dla właściwości animacji.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje dane wyjściowe z pliku multimedialnego.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Typ <xref:System.Windows.Media.Animation.TimelineGroup> tej grupy i formantów podrzędnych <xref:System.Windows.Media.Animation.Timeline> obiektów.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Typ <xref:System.Windows.Media.Animation.ParallelTimeline> zawierające informacje określania wartości docelowej dla osi czasu zawarte w nim obiekty.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstrakcyjna klasa podstawowa, który definiuje zachowania chronometrażu.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Abstrakcyjna klasa dla <xref:System.Windows.Media.Animation.Timeline> obiektów, które mogą zawierać inne <xref:System.Windows.Media.Animation.Timeline> obiektów.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Właściwości sterujące długości osi czasu  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długości osi czasu, można przedstawić na różne sposoby. W poniższej tabeli opisano kilka warunków dla opisu długości osi czasu.  
  
|Termin|Opis|Właściwości||||  
|----------|-----------------|----------------|-|-|-|  
|Czas trwania proste|Czas osi czasu zajmuje aby pojedynczy iteracji do przodu.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jeden powtórzenia|Czas potrzebny na osi czasu w celu odtwarzania do przodu po, a jeśli <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość ma wartość true, odtwarzanie wstecz raz.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Okres aktywności|Czas potrzebny na osi czasu w celu ukończenia wszystkich powtórzeń określony przez jego <xref:System.Windows.Media.Animation.RepeatBehavior> właściwości.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Wartość właściwości Duration  
 Jak wcześniej wspomniano osi czasu reprezentuje segment czasu. Długość danego segmentu jest określona na osi czasu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Gdy osi czasu osiągnie koniec jego czas trwania, zatrzymuje odtwarzanie. Jeśli osi podrzędnych osi czasu, ich zatrzymać odtwarzanie również. W przypadku animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Określa, jak długo animacji umożliwia przejście ze swojej wartości początkowej, do jego wartości końcowej. Czas trwania osi czasu jest czasami nazywany jego *proste czas trwania*, aby rozróżnić w czasie trwania jednej iteracji i całkowita długość czasu, w tym powtórzeń odtwarzania animacji. Można określić czas trwania, używając wartości skończonego czasu lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji powinien być rozpoznawany <xref:System.Windows.Duration.TimeSpan%2A> wartości, więc może przejść między wartościami.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Media.Animation.DoubleAnimation> z <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Kontener osi czasu, takich jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, ma domyślny okres <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie. W poniższym przykładzie przedstawiono <xref:System.Windows.Media.Animation.Storyboard> których <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest rozpoznawana jako pięć sekund, czas trwania jego podrzędny <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów, aby zakończyć.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Przez ustawienie <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu kontenera, aby <xref:System.Windows.Duration.TimeSpan%2A> wartości, możesz wymusić odtwarzania dłuższy lub krótszy niż jego podrzędny <xref:System.Windows.Media.Animation.Timeline> odtworzona obiektów. Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> na wartość, która jest mniejsza od długości osi czasu kontenera podrzędnego <xref:System.Windows.Media.Animation.Timeline> obiektów, obiekt podrzędny <xref:System.Windows.Media.Animation.Timeline> obiektów zatrzymać odtwarzanie, gdy nie istniał na osi czasu kontenera. W poniższym przykładzie <xref:System.Windows.Media.Animation.Timeline.Duration%2A> z <xref:System.Windows.Media.Animation.Storyboard> z powyższych przykładach do trzech sekund. W związku z tym pierwszym <xref:System.Windows.Media.Animation.DoubleAnimation> zatrzymuje postępu po trzy sekundy, gdy animowany szerokość prostokąta docelowych do 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>Właściwość RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, ile razy powtarza się jego długość proste. Przy użyciu <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości, można określić, ile razy pełni osi czasu (iteracji <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) lub całkowita długość czasu powinna być odtwarzana (powtórzeniem <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). W obu przypadkach animacji przechodzi przez podczas działania niezbędne do wypełnienia żądana liczba lub czas trwania wielu początku do końca. Domyślnie osiach czasu mają iteracji liczba `1.0`, co oznacza Odtwórz raz i nie powtarzaj w ogóle.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości, aby <xref:System.Windows.Media.Animation.DoubleAnimation> odtworzyć na dwa razy proste okres przez określenie liczby iteracji.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 W następnym przykładzie użyto <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości, aby <xref:System.Windows.Media.Animation.DoubleAnimation> odtwarzania połowa proste czas.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> jest powtarzany aż do zatrzymania interakcyjnego lub przez system chronometrażu. W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości, aby <xref:System.Windows.Media.Animation.DoubleAnimation> odtwarzanie w nieskończoność.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Na przykład dodatkowe zobacz [powtarzanie animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>Właściwość AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Właściwość określa, czy <xref:System.Windows.Media.Animation.Timeline> odtwarzania wstecz na końcu każdej iteracji do przodu. Poniższy przykład przedstawia <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> do `true`; w związku z tym animuje go od 0 do 100, a następnie od 100 do zera. Odtwarzania łącznie 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Korzystając <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> wartość określającą <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwości tego <xref:System.Windows.Media.Animation.Timeline> jest `true`, pojedynczy powtarzania składa się z jednego do przodu iteracji następuje jeden wstecz iteracji.  W poniższym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation> z poprzedniego przykładu do <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> liczby dwa. W związku z tym <xref:System.Windows.Media.Animation.DoubleAnimation> odgrywa 20 sekund: przesyłania dalej dla przekazywania pięć sekund, wstecz przez pięć sekund, 5 sekund ponownie, a następnie wstecz przez pięć sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Jeśli harmonogram kontenera podrzędnego <xref:System.Windows.Media.Animation.Timeline> obiektów i ich wstecznego, gdy kontener oś czasu nie. Aby uzyskać dodatkowe przykłady, zobacz [Określ, czy oś czasu automatycznie cofa](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>Właściwość BeginTime  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Właściwość umożliwia określenie, kiedy rozpoczyna się osi czasu.  Oś czasu godzina rozpoczęcia jest określana względem nadrzędnego osi czasu. Czas rozpoczęcia, zero sekund oznacza, że oś czasu rozpoczyna się zaraz po jego element nadrzędny uruchamiania; wszelkie inne wartości tworzy przesunięcie po nadrzędnej osi czasu rozpoczyna odtwarzanie i podczas odtwarzania osi podrzędnej. Na przykład czasem dwie sekundy oznacza oś czasu rozpoczyna odtwarzanie podczas jego element nadrzędny został osiągnięty czas dwóch sekund. Domyślnie wszystkie osiach czasu mają czasu rozpoczęcia, zero sekund. Można również ustawić osi czasu czas rozpoczęcia `null`, co uniemożliwia uruchomienie osi czasu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], należy ją określić za pomocą wartości null [x: Null — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
 Należy pamiętać, że czas rozpoczęcia nie jest stosowane zawsze powtarza osi czasu z powodu jego <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ustawienie. Jeśli masz zamiar utworzyć animację z <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund i <xref:System.Windows.Media.Animation.RepeatBehavior> z <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, byłoby 10-sekundowe opóźnienie przed animacji odtworzony po raz pierwszy, ale nie dla każdego kolejnych powtarzania. Jednakże gdyby animacji nadrzędnej osi czasu ponownego uruchomienia lub powtórz 10-sekundowe opóźnienie może mieć miejsce.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Właściwość jest przydatna do rozłożenie osi czasu. Poniższy przykład tworzy <xref:System.Windows.Media.Animation.Storyboard> ma dwa podrzędnych <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów. Pierwszy animacja ma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund, a dla drugiego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wynoszącym 3 sekundy. Ustawia przykład <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> drugiego <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund, tak że rozpoczęcia odtwarzania po pierwszym <xref:System.Windows.Media.Animation.DoubleAnimation> kończy się.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>Właściwość FillBehavior  
 Gdy <xref:System.Windows.Media.Animation.Timeline> dociera do końca jego całkowita długość active <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość określa, czy zatrzymuje lub zawiera jej ostatnią wartość. Animacja z <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "zawiera" wartość jego dane wyjściowe: animowanej właściwości zachowuje ostatnią wartość animacji. Wartość <xref:System.Windows.Media.Animation.FillBehavior.Stop> powoduje który stop animacji wpływu na jego właściwość target po jej zakończeniu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.Animation.Storyboard> ma dwa podrzędnych <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów. Zarówno <xref:System.Windows.Media.Animation.DoubleAnimation> Animowanie obiektów <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> z zakresu od 0 do 100. <xref:System.Windows.Shapes.Rectangle> Elementy mają z systemem innym niż animowany <xref:System.Windows.FrameworkElement.Width%2A> wartości 500 [pikselach niezależnych od urządzenia].  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwości pierwszego <xref:System.Windows.Media.Animation.DoubleAnimation> ma ustawioną wartość <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, wartością domyślną. W związku z tym szerokość prostokąta pozostaje na 100 po <xref:System.Windows.Media.Animation.DoubleAnimation> kończy się.  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwości drugiego <xref:System.Windows.Media.Animation.DoubleAnimation> ma ustawioną wartość <xref:System.Windows.Media.Animation.FillBehavior.Stop>. W związku z tym <xref:System.Windows.FrameworkElement.Width%2A> drugiego <xref:System.Windows.Shapes.Rectangle> wraca do 500 po <xref:System.Windows.Media.Animation.DoubleAnimation> kończy się.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Właściwości sterujące szybkości osi czasu  
 <xref:System.Windows.Media.Animation.Timeline> Klasa zawiera trzy właściwości w celu określenia jego prędkości:  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> — Umożliwia określenie tego kursu względem jego elementu nadrzędnego, jaką czas postępu dla <xref:System.Windows.Media.Animation.Timeline>. Wartości większej niż jeden zwiększania szybkości działania <xref:System.Windows.Media.Animation.Timeline> i jej podrzędne <xref:System.Windows.Media.Animation.Timeline> obiektów; wartości od zera do jednego spowolnić jej. Wartość jednego wskazuje, że <xref:System.Windows.Media.Animation.Timeline> realizowany w tym samym poziomie jak jego obiekt nadrzędny. <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> Osi czasu kontenera dotyczy wszystkich jego elementu podrzędnego <xref:System.Windows.Media.Animation.Timeline> również obiektów.  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> — Umożliwia określenie wartości procentowej <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu poświęconego przyspieszenia. Na przykład zobacz [porady: przyspieszanie lub zwalnia animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md). 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> — Umożliwia określenie wartości procentowej <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu poświęconego decelerating. Na przykład zobacz [porady: przyspieszanie lub zwalnia animacji](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacja i system chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Zdarzenia chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Przykład zachowania chronometrażu animacji](http://go.microsoft.com/fwlink/?LinkID=159970)
