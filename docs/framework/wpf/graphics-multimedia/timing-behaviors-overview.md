---
title: Przegląd Zachowania chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: a85f980a0cefaa282e9e92d533a2306a9009e3e7
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559953"
---
# <a name="timing-behaviors-overview"></a>Przegląd Zachowania chronometrażu
W tym temacie opisano zachowanie chronometrażu animacji i innych obiektów <xref:System.Windows.Media.Animation.Timeline>.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z podstawowymi funkcjami animacji. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>Typy osi czasu  
 <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu. Zawiera właściwości, które umożliwiają określenie długości tego segmentu, gdy powinien się zacząć, ile razy będzie powtarzane, jak szybko postępuje w tym segmencie i nie tylko.  
  
 Klasy dziedziczące z klasy osi czasu zapewniają dodatkowe funkcje, takie jak animacje i odtwarzanie multimediów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące typy <xref:System.Windows.Media.Animation.Timeline>.  
  
|Typ osi czasu|Opis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstrakcyjna klasa bazowa dla obiektów <xref:System.Windows.Media.Animation.Timeline>, które generują wartości wyjściowe właściwości animacji.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje dane wyjściowe z pliku multimedialnego.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|Typ <xref:System.Windows.Media.Animation.TimelineGroup>, który grupuje i kontroluje obiekty podrzędne <xref:System.Windows.Media.Animation.Timeline>.|  
|<xref:System.Windows.Media.Animation.Storyboard>|Typ <xref:System.Windows.Media.Animation.ParallelTimeline>, który zawiera informacje dotyczące określania wartości docelowej dla obiektów osi czasu, które zawiera.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstrakcyjna klasa bazowa, która definiuje zachowania chronometrażu.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Klasa abstrakcyjna dla <xref:System.Windows.Media.Animation.Timeline> obiektów, które mogą zawierać inne obiekty <xref:System.Windows.Media.Animation.Timeline>.|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>Właściwości kontrolujące Długość osi czasu  
 <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i długość osi czasu można opisać na różne sposoby. W poniższej tabeli zdefiniowano kilka warunków opisujących Długość osi czasu.  
  
|Termin|Opis|Właściwości||||  
|----------|-----------------|----------------|-|-|-|  
|Prosty czas trwania|Czas potrzebny na przetworzenie pojedynczej iteracji przez oś czasu.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jedno powtórzenie|Czas potrzebny na przetworzenie osi czasu, gdy właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ma wartość true, Odtwarzaj do tyłu jednokrotnie.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Aktywny okres|Czas, jaki zajmuje oś czasu na ukończenie wszystkich powtórzeń określonych przez właściwość <xref:System.Windows.Media.Animation.RepeatBehavior>.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Właściwość Duration  
 Jak wspomniano wcześniej, oś czasu reprezentuje segment czasu. Długość tego segmentu jest określana na podstawie <xref:System.Windows.Media.Animation.Timeline.Duration%2A>osi czasu. Gdy oś czasu osiągnie koniec swojego czasu trwania, przestanie być odtwarzane. Jeśli oś czasu ma podrzędne osie czasu, przestają również być odtwarzane. W przypadku animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> określa, jak długo animacja wymaga przejścia od wartości początkowej do jej wartości końcowej. Czas trwania osi czasu jest czasami nazywany jego *prostym czasem trwania*, aby odróżnić czas trwania pojedynczej iteracji i łączny czas odtwarzania animacji, w tym powtórzenia. Możesz określić czas trwania przy użyciu skończonej wartości czasu lub wartości specjalnych <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji powinien zostać rozpoznany jako wartość <xref:System.Windows.Duration.TimeSpan%2A>, aby można było przejść między wartościami.  
  
 Poniższy przykład pokazuje <xref:System.Windows.Media.Animation.DoubleAnimation> z <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Osie czasu kontenerów, takie jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, mają domyślny czas trwania <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że są one automatycznie kończyć się, gdy ich ostatni przestanie być odtwarzany. W poniższym przykładzie przedstawiono <xref:System.Windows.Media.Animation.Storyboard>, którego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest rozpoznawany na pięć sekund, a tym samym, ile czasu zajmie cały <xref:System.Windows.Media.Animation.DoubleAnimation> obiektów podrzędnych.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ustawiając <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu kontenera na wartość <xref:System.Windows.Duration.TimeSpan%2A>, możesz wymusić odtwarzanie dłużej lub krócej niż jego podrzędne obiekty <xref:System.Windows.Media.Animation.Timeline>. Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wartość, która jest mniejsza niż długość obiektów podrzędnych <xref:System.Windows.Media.Animation.Timeline> osi czasu kontenera, obiekty podrzędne <xref:System.Windows.Media.Animation.Timeline> przestają być odtwarzane po przetworzeniu osi czasu kontenera. W poniższym przykładzie ustawiono <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.Storyboard> z powyższych przykładów na trzy sekundy. W związku z tym pierwsze <xref:System.Windows.Media.Animation.DoubleAnimation> przerywa postęp po trzech sekundach, gdy ma animowaną szerokość prostokąta docelowego do 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>Właściwość RepeatBehavior  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> kontroluje, ile razy powtarza swój prosty czas trwania. Za pomocą właściwości <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> można określić, ile razy jest odtwarzany oś czasu (<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>iteracji), lub łączny czas, który powinien być odtwarzany (powtórz <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>). W obu przypadkach animacja przechodzi przez wiele uruchomień na początku, aby wypełnić żądaną liczbę lub czas trwania. Domyślnie osie czasu mają liczbę iteracji `1.0`, co oznacza, że są one odtwarzane i nie powtarzają się wcale.  
  
 W poniższym przykładzie zastosowano Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, aby <xref:System.Windows.Media.Animation.DoubleAnimation> odtworzyć dwa razy prosty czas trwania przez określenie liczby iteracji.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 W następnym przykładzie jest stosowana Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, która umożliwia <xref:System.Windows.Media.Animation.DoubleAnimation> odtwarzanie przez pół czasu prostego.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Właściwość <xref:System.Windows.Media.Animation.Timeline> na <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, <xref:System.Windows.Media.Animation.Timeline> powtarza się do momentu, aż zostanie zatrzymana interaktywnie lub przez system chronometrażu. W poniższym przykładzie zastosowano Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, aby <xref:System.Windows.Media.Animation.DoubleAnimation> oddziałać w nieskończoność.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Aby uzyskać dodatkowy przykład, zobacz [powtarzanie animacji](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>Właściwość autoversa  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> określa, czy <xref:System.Windows.Media.Animation.Timeline> będzie odtwarzana wstecz na końcu każdej iteracji do przodu. Poniższy przykład ustawia właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> do `true`; w efekcie są one animowane od zera do 100, a następnie od 100 do zera. Jest on odtwarzany przez sumę 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 Jeśli używasz wartości <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>, aby określić <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> i Właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> tego <xref:System.Windows.Media.Animation.Timeline> jest `true`, pojedyncze powtórzenie składa się z jednej iteracji do przodu, a następnie jednej iteracji z poprzednimi wersjami.  Poniższy przykład ustawia <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> z poprzedniego przykładu do <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> dwóch. W efekcie <xref:System.Windows.Media.Animation.DoubleAnimation> jest odtwarzany przez 20 sekund: do przodu przez pięć sekund, do tyłu przez pięć sekund, do przodu przez 5 sekund, a następnie do tyłu przez pięć sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Jeśli oś czasu kontenera ma podrzędne obiekty <xref:System.Windows.Media.Animation.Timeline>, są one odwracane po osi czasu kontenera. Aby uzyskać więcej przykładów, zobacz [Określanie, czy oś czasu jest automatycznie wycofywana](how-to-specify-whether-a-timeline-automatically-reverses.md).  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>Właściwość BeginTime  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> umożliwia określenie momentu uruchomienia osi czasu.  Czas rozpoczęcia osi czasu jest względem jej nadrzędnej osi czasu. Godzina rozpoczęcia równa zero sekund oznacza, że oś czasu zaczyna się zaraz po uruchomieniu elementu nadrzędnego; Każda inna wartość tworzy przesunięcia między momentem, gdy nadrzędna oś czasu rozpoczyna odtwarzanie i gdy jest odtwarzana podrzędna oś czasu. Na przykład czas rozpoczęcia dwóch sekund oznacza, że oś czasu rozpoczyna odtwarzanie, gdy jego element nadrzędny osiągnął czas dwóch sekund. Domyślnie wszystkie osie czasu mają godzinę rozpoczęcia równą zero sekund. Możesz również ustawić czas rozpoczęcia `null`osi czasu, co uniemożliwi uruchomienie osi czasu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]należy określić wartość null przy użyciu [rozszerzenia znacznika x:null —](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Należy zauważyć, że czas rozpoczęcia nie jest stosowany za każdym razem, gdy oś czasu jest powtarzana z powodu ustawienia <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>. Jeśli chcesz utworzyć animację z <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 sekund i <xref:System.Windows.Media.Animation.RepeatBehavior> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, będzie można uzyskać 10-sekundowe opóźnienie przed odtwarzaniem animacji po raz pierwszy, ale nie dla każdego kolejnego powtórzenia. Jeśli jednak nadrzędna oś czasu animacji została ponownie uruchomiona lub powtórzona, nastąpi opóźnienie 10 sekund.  
  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> jest przydatna do rozłożenie osi czasu. Poniższy przykład tworzy <xref:System.Windows.Media.Animation.Storyboard>, który ma dwa obiekty podrzędne <xref:System.Windows.Media.Animation.DoubleAnimation>. Pierwsza animacja ma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund, a druga ma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> o wartości 3 sekund. W przykładzie ustawiono <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> drugiej <xref:System.Windows.Media.Animation.DoubleAnimation> na 5 sekund, aby rozpocząć odtwarzanie po pierwszym <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>Właściwość FillBehavior  
 Gdy <xref:System.Windows.Media.Animation.Timeline> osiągnie koniec łącznego aktywnego czasu trwania, właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> określa, czy jej Ostatnia wartość jest zatrzymywana, czy też utrzymuje ją. Animacja z <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "utrzymuje" wartość wyjściową: Animowana Właściwość zachowuje ostatnią wartość animacji. Wartość <xref:System.Windows.Media.Animation.FillBehavior.Stop> powoduje, że animacja nie wpływa na jej Właściwość docelową po jej zakończeniu.  
  
 Poniższy przykład tworzy <xref:System.Windows.Media.Animation.Storyboard>, który ma dwa obiekty podrzędne <xref:System.Windows.Media.Animation.DoubleAnimation>. Oba obiekty <xref:System.Windows.Media.Animation.DoubleAnimation> są animowane <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> od 0 do 100. Elementy <xref:System.Windows.Shapes.Rectangle> mają Nieanimowane wartości <xref:System.Windows.FrameworkElement.Width%2A> 500 [piksele niezależne od urządzenia].  
  
- Właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pierwszego <xref:System.Windows.Media.Animation.DoubleAnimation> jest ustawiona na <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, wartość domyślną. W związku z tym szerokość prostokąta pozostaje o godzinie 100 po zakończeniu <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
- Właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> drugiej <xref:System.Windows.Media.Animation.DoubleAnimation> jest ustawiona na <xref:System.Windows.Media.Animation.FillBehavior.Stop>. W związku z tym <xref:System.Windows.FrameworkElement.Width%2A> drugiej <xref:System.Windows.Shapes.Rectangle> są przywracane do 500 po zakończeniu <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Właściwości kontrolujące prędkość osi czasu  
 Klasa <xref:System.Windows.Media.Animation.Timeline> zawiera trzy właściwości do określenia szybkości:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> — określa, że ta stawka odnosząca się do jego elementu nadrzędnego, gdy czas dla <xref:System.Windows.Media.Animation.Timeline>. Wartości większe niż jeden zwiększają szybkość <xref:System.Windows.Media.Animation.Timeline> i jego obiektów podrzędnych <xref:System.Windows.Media.Animation.Timeline>; wartości z przedziału od zera do jednego spowalniają działanie. Wartość jednego wskazuje, że <xref:System.Windows.Media.Animation.Timeline> postępów z tą samą szybkością co jego element nadrzędny. Ustawienie <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> osi czasu kontenera ma także wpływ na wszystkie obiekty podrzędne <xref:System.Windows.Media.Animation.Timeline>.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> — określa wartość procentową <xref:System.Windows.Media.Animation.Timeline.Duration%2A>j osi czasu poświęcaną na przyspieszanie. Aby zapoznać się z przykładem, zobacz [How to: Przyspiesz lub spowalniania animację](how-to-accelerate-or-decelerate-an-animation.md). 
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> — określa wartość procentową <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu poświęconej spowolnienie. Aby zapoznać się z przykładem, zobacz [How to: Przyspiesz lub spowalniania animację](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Animacja i system chronometrażu — przegląd](animation-and-timing-system-overview.md)
- [Zdarzenia chronometrażu — przegląd](timing-events-overview.md)
- [Tematy z instrukcjami](animation-and-timing-how-to-topics.md)
- [Przykład zachowania chronometrażu animacji](https://go.microsoft.com/fwlink/?LinkID=159970)
