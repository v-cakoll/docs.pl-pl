---
title: Przegląd Zachowania chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: c3403a8602cc874e993bd649851b77d7bf652cce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002342"
---
# <a name="timing-behaviors-overview"></a>Przegląd Zachowania chronometrażu
W tym temacie opisano zachowania chronometrażu animacji i innych <xref:System.Windows.Media.Animation.Timeline> obiektów.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy zapoznać się z funkcjami podstawowa Animacja. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Typy osi czasu  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu. Zapewnia właściwości, które umożliwiają określenie długości tego segmentu, gdy go na początek, ile razy będzie powtarzane, jak szybko w miarę czasu w tym segmencie i nie tylko.  
  
 Klasy, które dziedziczą z klasy osi czasu zapewnia dodatkowe funkcje, takie jak odtwarzanie animacji i media. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące <xref:System.Windows.Media.Animation.Timeline> typów.  
  
|Typ osi czasu|Opis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstrakcyjna klasa bazowa dla <xref:System.Windows.Media.Animation.Timeline> obiekty, które generują wartości wyjściowe animowania właściwości.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje dane wyjściowe z pliku multimedialnego.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Rodzaj <xref:System.Windows.Media.Animation.TimelineGroup> tej grupy i formanty podrzędne <xref:System.Windows.Media.Animation.Timeline> obiektów.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Rodzaj <xref:System.Windows.Media.Animation.ParallelTimeline> zawierające informacje określania wartości docelowej dla osi czasu w nim obiekty.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstrakcyjna klasa bazowa, który definiuje zachowania chronometrażu.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Abstrakcyjna klasa dla <xref:System.Windows.Media.Animation.Timeline> obiektów, które mogą zawierać inne <xref:System.Windows.Media.Animation.Timeline> obiektów.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Właściwości określające długości osi czasu  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długości osi czasu można opisać w różny sposób. W poniższej tabeli opisano kilka warunków do opisywania długości osi czasu.  
  
|Termin|Opis|Właściwości||||  
|----------|-----------------|----------------|-|-|-|  
|Czas trwania prosty|Czas osi czasu zajmuje się jednej iteracji do przodu.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Powtarzanie co|Czas potrzebny na osi czasu w celu odtwarzania do przodu po, a jeśli <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość ma wartość true, odtwarzanie wstecz raz.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Okres aktywności|Czas potrzebny na osi czasu w celu ukończenia wszystkich powtórzeń określony przez jego <xref:System.Windows.Media.Animation.RepeatBehavior> właściwości.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Właściwość czasu trwania  
 Jak wspomniano wcześniej oś czasu reprezentuje segment czasu. Długość tego segmentu jest określany na osi czasu <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Oś czasu osiągnie koniec jego czas trwania, zatrzymuje, odtwarzanie. Oś czasu ma podrzędnych osi czasu, ich Zatrzymaj odtwarzanie także. W przypadku animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> określa animacji czas przejścia z jej wartość początkową wartość końcową. Czas trwania osi czasu jest czasami nazywane jego *proste czas trwania*, aby rozróżnić czas trwania jednej iteracji i całkowita długość czasu animacji w tym powtórzeń. Można określić czas trwania, używając wartości skończony czas lub specjalnych wartości <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji powinna być rozwiązywana na <xref:System.Windows.Duration.TimeSpan%2A> wartości, dzięki czemu można przejść między wartościami.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Media.Animation.DoubleAnimation> z <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Kontener osi czasu, takich jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, mają domyślny czas trwania <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że zakończeniu ich automatycznie po ich ostatnim elementem podrzędnym zatrzymuje odtwarzanie. W poniższym przykładzie przedstawiono <xref:System.Windows.Media.Animation.Storyboard> którego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest rozpoznawana jako pięć sekund, długość czasu jego podrzędny <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów, aby zakończyć.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ustawiając <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu kontenera, aby <xref:System.Windows.Duration.TimeSpan%2A> wartości, możesz wymusić grać dłuższy lub krótszy niż jego podrzędny <xref:System.Windows.Media.Animation.Timeline> odtworzona obiektów. Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wartość, która jest mniejsza niż długość podrzędnych osi czasu kontenera <xref:System.Windows.Media.Animation.Timeline> obiektów, element podrzędny <xref:System.Windows.Media.Animation.Timeline> obiektów Zatrzymaj odtwarzanie, gdy jest na osi czasu kontenera. Poniższy przykład ustawia <xref:System.Windows.Media.Animation.Timeline.Duration%2A> z <xref:System.Windows.Media.Animation.Storyboard> z powyższych przykładach do trzech sekund. W wyniku pierwsze <xref:System.Windows.Media.Animation.DoubleAnimation> zatrzymuje postęp po trzy sekundy, kiedy animowane 60 i szerokości prostokąta docelowego.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>Właściwość RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> Określa, ile razy powtarza się proste czas jego trwania. Za pomocą <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwości, można określić, ile razy odtwarzania osi czasu (iteracji <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) lub całkowita długość czasu powinna być odtwarzana (Powtórz <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). W obu przypadkach animacji przechodzi przez podczas gdy jest to konieczne do wypełnienia żądana liczba lub czas trwania działania wielu początku do końca. Domyślnie, osie czasu mają iteracji liczbę `1.0`, co oznacza, że Odtwórz raz, a nie powtarzają w ogóle.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość się <xref:System.Windows.Media.Animation.DoubleAnimation> odtwarzania przez dwa razy proste czas trwania, określając liczbę iteracji.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 W następnym przykładzie użyto <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość się <xref:System.Windows.Media.Animation.DoubleAnimation> odtwarzanie w wysokości równej połowie proste czas.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Timeline> do <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> jest powtarzany aż do zatrzymania interakcyjnego lub przez system chronometrażu. W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> właściwość się <xref:System.Windows.Media.Animation.DoubleAnimation> odtwarzania na czas nieokreślony.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Na przykład dodatkowe zobacz [powtarzanie animacji](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse właściwość  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Właściwość określa, czy <xref:System.Windows.Media.Animation.Timeline> będzie tyłu odtwarzany na końcu każdej iteracji do przodu. Poniższy przykład ustawia <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> do `true`; w związku z jego animuje od 0 do 100, a następnie od 100 do zera. Jest odtwarzany łącznie przez 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Podczas korzystania <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> wartością do określenia <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.Timeline> i <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość, która <xref:System.Windows.Media.Animation.Timeline> jest `true`, pojedynczy powtórzenia składa się z jednego do przodu iteracji następuje jedna wstecz iteracji.  Poniższy przykład ustawia <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> z <xref:System.Windows.Media.Animation.DoubleAnimation> z poprzedniego przykładu, aby <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> dwie metody. W wyniku <xref:System.Windows.Media.Animation.DoubleAnimation> odgrywa 20 sekund: do przodu dla pięciu sekundach wstecz pięć sekund, przekazywać 5 sekund, a następnie wstecz przez pięć sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Jeśli na osi czasu w kontenerze ma element podrzędny <xref:System.Windows.Media.Animation.Timeline> obiektów i ich cofała się gdy jest na osi czasu w kontenerze. Aby uzyskać więcej przykładów, zobacz [określić, czy oś czasu automatycznie odtwarzana od końca](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>Właściwość BeginTime  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Właściwość umożliwia określenie, kiedy rozpoczyna się osi czasu.  Czas rozpoczęcia osi czasu są określane względem jego nadrzędnego osi czasu. Czas rozpoczęcia, oznacza zero sekund, oś czasu uruchomienia zaraz po jego nadrzędnej uruchamiania; Dowolna inna wartość tworzy przesunięcia między podczas uruchamiania odtwarzania osi czasu w nadrzędnej i podczas odtwarzania osi podrzędnej. Na przykład czas rozpoczęcia, dwóch sekund oznacza, że oś czasu uruchamiania odtwarzania, gdy jego element nadrzędny osiągnie czas dwóch sekund. Domyślnie wszystkie osie czasu ma czas rozpoczęcia, zero sekund. Możesz też ustawić opcję osi czasu rozpoczęcia, czas `null`, co uniemożliwia uruchamianie osi czasu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], określ, o wartości null przy użyciu [x: Null — rozszerzenie znaczników](../../xaml-services/x-null-markup-extension.md).  
  
 Należy zauważyć, że czas rozpoczęcia nie jest stosowane zawsze, oś czasu powtarza się z powodu jego <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ustawienie. Jeśli masz zamiar utworzyć animację <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund i <xref:System.Windows.Media.Animation.RepeatBehavior> z <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, będzie istnieć 10-sekundowe opóźnienie przed animacji jest odtwarzany po raz pierwszy, ale nie dla poszczególnych kolejnych powtórzenia. Jednakże gdyby osi czasu animacji w nadrzędnej można ponownie uruchomić lub powtórz 10 sekund opóźnienia operacja zostanie wykonana.  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> Właściwość jest przydatne w przypadku zróżnicować godziny rozpoczęcia osi czasu. Poniższy przykład tworzy <xref:System.Windows.Media.Animation.Storyboard> ma dwa podrzędnych <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów. Pierwszy animacja ma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund, a druga ma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wynoszącym 3 sekundy. Przykład ustawia <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> drugiego <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund, tak że rozpoczęcia odtwarzania po pierwszym <xref:System.Windows.Media.Animation.DoubleAnimation> kończy.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior właściwość  
 Gdy <xref:System.Windows.Media.Animation.Timeline> osiągnie koniec całkowity czas aktywności <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwość określa, czy przestaje czy przechowuje wartość ostatniego. Animację <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "przechowuje" wartość danych wyjściowych: właściwości, jest animowany przechowuje ostatnią wartość animacji. Wartość <xref:System.Windows.Media.Animation.FillBehavior.Stop> powoduje, że, Zatrzymaj animacji wpływu na jego właściwość target po jej zakończeniu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.Animation.Storyboard> ma dwa podrzędnych <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów. Zarówno <xref:System.Windows.Media.Animation.DoubleAnimation> Animowanie obiektów <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> z zakresu od 0 do 100. <xref:System.Windows.Shapes.Rectangle> Elementy mają inne niż animowane <xref:System.Windows.FrameworkElement.Width%2A> wartości 500 [pikselach niezależnych od urządzenia].  
  
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwości pierwszego <xref:System.Windows.Media.Animation.DoubleAnimation> ustawiono <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, wartością domyślną. W rezultacie szerokość prostokąta pozostaje na 100 po <xref:System.Windows.Media.Animation.DoubleAnimation> kończy.  
  
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Właściwość drugiej <xref:System.Windows.Media.Animation.DoubleAnimation> ustawiono <xref:System.Windows.Media.Animation.FillBehavior.Stop>. W rezultacie <xref:System.Windows.FrameworkElement.Width%2A> drugiego <xref:System.Windows.Shapes.Rectangle> powraca do 500 po <xref:System.Windows.Media.Animation.DoubleAnimation> kończy.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Właściwości określające prędkość w osi czasu  
 <xref:System.Windows.Media.Animation.Timeline> Klasa udostępnia trzy właściwości do określenia jej szybkość działania:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> — Umożliwia określenie tego kursu, względem jego elementu nadrzędnego, w którym czasu w miarę dla <xref:System.Windows.Media.Animation.Timeline>. Wartości jest większa niż jeden przyspieszenie <xref:System.Windows.Media.Animation.Timeline> i jej podrzędne <xref:System.Windows.Media.Animation.Timeline> obiektów; wartości z zakresu od zera do jednego spowolnić jej. Wartość 1 oznacza, że <xref:System.Windows.Media.Animation.Timeline> realizowany przy użyciu stawki stosowanej jako klasy nadrzędnej. <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> Ustawienie na osi czasu w kontenerze ma wpływ na wszystkie jego podrzędny <xref:System.Windows.Media.Animation.Timeline> także obiekty.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> — Określa wartość procentową <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu poświęconego przyspieszenia. Aby uzyskać przykład, zobacz [jak: Przyspieszanie lub zwalnianie animacji](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -Określa wartość procentową <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu poświęconego spowolnienie. Aby uzyskać przykład, zobacz [jak: Przyspieszanie lub zwalnianie animacji](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Animacja i system chronometrażu — przegląd](animation-and-timing-system-overview.md)
- [Zdarzenia chronometrażu — przegląd](timing-events-overview.md)
- [Tematy z instrukcjami](animation-and-timing-how-to-topics.md)
- [Przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970)
