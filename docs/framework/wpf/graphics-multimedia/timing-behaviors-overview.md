---
title: Przegląd Zachowania chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 3bb42ddd991d3ae1221cc794afdd4aafc74a6046
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145400"
---
# <a name="timing-behaviors-overview"></a>Przegląd Zachowania chronometrażu
W tym temacie opisano zachowania chronometrażu animacji i innych <xref:System.Windows.Media.Animation.Timeline> obiektów.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z podstawowymi funkcjami animacji. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="timelinetypes"></a>
## <a name="timeline-types"></a>Typy osi czasu  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu. Zawiera właściwości, które umożliwiają określenie długości tego segmentu, kiedy należy uruchomić, ile razy będzie powtarzać, jak szybko postępuje w tym segmencie i więcej.  
  
 Klasy, które dziedziczą z klasy osi czasu zapewniają dodatkowe funkcje, takie jak animacji i odtwarzania multimediów. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera następujące <xref:System.Windows.Media.Animation.Timeline> typy.  
  
|Typ osi czasu|Opis|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|Abstrakcyjna klasa <xref:System.Windows.Media.Animation.Timeline> podstawowa dla obiektów, które generują wartości wyjściowe dla animowania właściwości.|  
|<xref:System.Windows.Media.MediaTimeline>|Generuje dane wyjściowe z pliku multimedialnego.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.TimelineGroup> Typ, który grupuje <xref:System.Windows.Media.Animation.Timeline> i steruje obiektami podrzędnymi.|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ParallelTimeline> Typ, który zawiera informacje o określaniunie celów dla obiektów Osi czasu, które zawiera.|  
|<xref:System.Windows.Media.Animation.Timeline>|Abstrakcyjna klasa podstawowa definiująca zachowania chronometrażu.|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|Klasa abstrakcyjna dla <xref:System.Windows.Media.Animation.Timeline> obiektów, które mogą zawierać inne <xref:System.Windows.Media.Animation.Timeline> obiekty.|  
  
<a name="propertiesthatcontroltimelinelength"></a>
## <a name="properties-that-control-the-length-of-a-timeline"></a>Właściwości sterujące długością osi czasu  
 A <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu, a długość osi czasu można opisać na różne sposoby. W poniższej tabeli zdefiniowano kilka terminów opisujących długość osi czasu.  
  
|Termin|Opis|Właściwości||||  
|----------|-----------------|----------------|-|-|-|  
|Prosty czas trwania|Czas trwania osi czasu do wykonania jednej iteracji do przodu.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|Jedno powtórzenie|Czas potrzebny na odtworzeń osi czasu do przodu <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> raz, a jeśli właściwość jest prawdziwa, odtworzyć do tyłu raz.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|Aktywny okres|Czas potrzebny na osi czasu, aby zakończyć wszystkie powtórzenia <xref:System.Windows.Media.Animation.RepeatBehavior> określone przez jego właściwości.|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>, <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>
### <a name="the-duration-property"></a>Właściwość czas trwania  
 Jak wcześniej wspomniano, oś czasu reprezentuje segment czasu. Długość tego segmentu zależy od osi <xref:System.Windows.Media.Animation.Timeline.Duration%2A>czasu . Gdy oś czasu dobiegnie końca, przestanie być odtwarzana. Jeśli oś czasu ma osi czasu podrzędnych, przestają grać, jak również. W przypadku animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> określa, jak długo trwa animacja do przejścia od jego wartości początkowej do jego wartości zakończenia. Czas trwania osi czasu jest czasami nazywany jej *prostym czasem trwania,* aby odróżnić czas trwania pojedynczej iteracji od całkowitego czasu odtwarzania animacji, w tym powtórzeń. Czas trwania można określić przy użyciu skończonej wartości czasu lub wartości <xref:System.Windows.Duration.Automatic%2A> specjalnych lub <xref:System.Windows.Duration.Forever%2A>. Czas trwania animacji powinien <xref:System.Windows.Duration.TimeSpan%2A> rozwiązać wartość, dzięki czemu można przejść między wartościami.  
  
 W poniższym <xref:System.Windows.Media.Animation.DoubleAnimation> przykładzie <xref:System.Windows.Media.Animation.Timeline.Duration%2A> przedstawiono a z pięciu sekund.  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 Osi czasu kontenera, takich jak <xref:System.Windows.Media.Animation.Storyboard> i <xref:System.Windows.Media.Animation.ParallelTimeline>, mają domyślny czas trwania <xref:System.Windows.Duration.Automatic%2A>, co oznacza, że automatycznie kończy się, gdy ich ostatnie dziecko przestaje grać. W poniższym <xref:System.Windows.Media.Animation.Storyboard> przykładzie pokazano, którego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> rozpoznaje do pięciu sekund, czas potrzebny wszystkie jego obiekty podrzędne, <xref:System.Windows.Media.Animation.DoubleAnimation> aby zakończyć.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 Ustawiając <xref:System.Windows.Media.Animation.Timeline.Duration%2A> oś czasu kontenera <xref:System.Windows.Duration.TimeSpan%2A> na wartość, można wymusić odtwarzanie dłużej lub krócej niż jego obiekty podrzędne <xref:System.Windows.Media.Animation.Timeline> będą odtwarzane. Jeśli ustawisz <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wartość, która jest mniejsza niż długość obiektów <xref:System.Windows.Media.Animation.Timeline> podrzędnych osi <xref:System.Windows.Media.Animation.Timeline> czasu kontenera, obiekty podrzędne przestaną być odtwarzane, gdy nie ma osi czasu kontenera. Poniższy przykład <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ustawia <xref:System.Windows.Media.Animation.Storyboard> z poprzednich przykładów do trzech sekund. W rezultacie pierwszy <xref:System.Windows.Media.Animation.DoubleAnimation> zatrzymuje się po trzech sekundach, gdy ma animowane szerokość prostokąta docelowego do 60.  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>
### <a name="the-repeatbehavior-property"></a>Właściwość RepeatBehavior  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> formanty <xref:System.Windows.Media.Animation.Timeline> ile razy powtarza jego prosty czas trwania. Za <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> pomocą właściwości można określić, ile razy odtwarzana <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>jest oś czasu (iteracja) <xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>lub całkowita długość czasu, przez jaki powinna być odtwarzana (powtórzenie). W obu przypadkach animacji przechodzi przez tyle przebiegów od początku do końca, jak to konieczne do wypełnienia żądanej liczby lub czas trwania. Domyślnie osie czasu mają liczbę `1.0`iteracji , co oznacza, że grają raz i w ogóle się nie powtarzają.  
  
 W poniższym <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> właściwości, aby odtworzyć dwukrotnie jego prosty czas trwania, określając liczbę iteracji.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 W następnym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> używa właściwości, aby <xref:System.Windows.Media.Animation.DoubleAnimation> grać na połowę jego prosty czas trwania.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 Jeśli <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ustawisz właściwość a <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline> , powtarza się, <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>dopóki nie zostanie zatrzymana interaktywnie lub przez system chronometrażu. W poniższym przykładzie <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> użyto <xref:System.Windows.Media.Animation.DoubleAnimation> właściwości, aby grać przez czas nieokreślony.  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 Aby uzyskać dodatkowy przykład, zobacz [Powtarzanie animacji](how-to-repeat-an-animation.md).  
  
<a name="autoreverseproperty"></a>
### <a name="the-autoreverse-property"></a>Właściwość AutoReverse  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> określa, <xref:System.Windows.Media.Animation.Timeline> czy będzie odtwarzać do tyłu na końcu każdej iteracji do przodu. Poniższy przykład ustawia <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> `true`do ; w rezultacie animuje od zera do 100, a następnie od 100 do zera. Gra w sumie przez 10 sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 W przypadku <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> użycia wartości <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> do <xref:System.Windows.Media.Animation.Timeline> określenia <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> a i <xref:System.Windows.Media.Animation.Timeline> `true`właściwości, która jest, pojedyncze powtórzenie składa się z jednej iteracji do przodu, a następnie jednej iteracji wstecznej.  Poniższy przykład <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ustawia <xref:System.Windows.Media.Animation.DoubleAnimation> z poprzedniego przykładu <xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A> do z dwóch. W rezultacie <xref:System.Windows.Media.Animation.DoubleAnimation> gra przez 20 sekund: do przodu przez pięć sekund, do tyłu przez pięć sekund, do przodu przez 5 sekund ponownie, a następnie do tyłu przez pięć sekund.  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 Jeśli oś czasu <xref:System.Windows.Media.Animation.Timeline> kontenera ma obiekty podrzędne, odwracają się, gdy robi to oś czasu kontenera. Aby uzyskać dodatkowe przykłady, zobacz [Określanie, czy oś czasu automatycznie odwraca](how-to-specify-whether-a-timeline-automatically-reverses.md)się .  
  
<a name="timelinebegin"></a>
## <a name="the-begintime-property"></a>Właściwość BeginTime  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> umożliwia określenie, kiedy rozpoczyna się oś czasu.  Czas rozpoczęcia osi czasu jest względny do jej nadrzędnej osi czasu. Godzina rozpoczęcia zero sekund oznacza, że oś czasu rozpoczyna się natychmiast po uruchomieniu elementu nadrzędnego; każda inna wartość tworzy przesunięcie między rozpoczęciem odtwarzania osi czasu nadrzędnego a odtwarzaniem osi czasu podrzędnego. Na przykład czas rozpoczęcia dwóch sekund oznacza, że oś czasu rozpoczyna odtwarzanie, gdy jej nadrzędny osiągnie czas dwóch sekund. Domyślnie wszystkie osie czasu mają czas rozpoczęcia zero sekund. Można również ustawić czas rozpoczęcia osi `null`czasu na , co uniemożliwia rozpoczęcie osi czasu. W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obszarze , należy określić wartość null przy użyciu [rozszerzenia znaczników x:Null](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
 Należy zauważyć, że czas rozpoczęcia nie jest stosowany za <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> każdym razem, gdy oś czasu jest powtarzana ze względu na jej ustawienie. Jeśli chcesz utworzyć animację <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> z 10 sekund <xref:System.Windows.Media.Animation.RepeatBehavior> <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>i a , byłoby 10-sekundowe opóźnienie przed animacji odtwarzane po raz pierwszy, ale nie dla każdego kolejnego powtórzenia. Jeśli jednak nadrzędna oś czasu animacji miałaby zostać ponownie uruchomiona lub powtórzony, wystąpiłoby 10-sekundowe opóźnienie.  
  
 Właściwość <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> jest przydatna do rozłąki terminów. Poniższy przykład <xref:System.Windows.Media.Animation.Storyboard> tworzy, który <xref:System.Windows.Media.Animation.DoubleAnimation> ma dwa obiekty podrzędne. Pierwsza animacja <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ma pięć sekund, a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> druga 3 sekundy. W przykładzie <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ustawia <xref:System.Windows.Media.Animation.DoubleAnimation> się drugi do 5 sekund, tak <xref:System.Windows.Media.Animation.DoubleAnimation> aby rozpoczyna się odtwarzanie po pierwszym zakończeniu.  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>
## <a name="the-fillbehavior-property"></a>Właściwość FillBehavior  
 Gdy <xref:System.Windows.Media.Animation.Timeline> osiągnie koniec całkowitego aktywnego czasu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> trwania, właściwość określa, czy zatrzymuje lub przechowuje swoją ostatnią wartość. Animacja <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> "trzyma" jego wartość wyjściowa: właściwość animowana zachowuje ostatnią wartość animacji. Wartość <xref:System.Windows.Media.Animation.FillBehavior.Stop> powoduje, że animacja zatrzymać wpływ na jego właściwość docelową po jej zakończeniu.  
  
 Poniższy przykład <xref:System.Windows.Media.Animation.Storyboard> tworzy, który <xref:System.Windows.Media.Animation.DoubleAnimation> ma dwa obiekty podrzędne. Oba <xref:System.Windows.Media.Animation.DoubleAnimation> obiekty <xref:System.Windows.FrameworkElement.Width%2A> animują <xref:System.Windows.Shapes.Rectangle> od 0 do 100. Elementy <xref:System.Windows.Shapes.Rectangle> mają nieanimowane <xref:System.Windows.FrameworkElement.Width%2A> wartości 500 [piksele niezależne od urządzenia].  
  
- Właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pierwszego <xref:System.Windows.Media.Animation.DoubleAnimation> jest ustawiona na <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>wartość domyślną. W rezultacie szerokość prostokąta pozostaje na poziomie 100 <xref:System.Windows.Media.Animation.DoubleAnimation> po zakończeniu.  
  
- Właściwość <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> drugiego <xref:System.Windows.Media.Animation.DoubleAnimation> jest ustawiona na <xref:System.Windows.Media.Animation.FillBehavior.Stop>. W rezultacie drugi <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> powraca do 500 po <xref:System.Windows.Media.Animation.DoubleAnimation> zakończeniu.  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>
## <a name="properties-that-control-the-speed-of-a-timeline"></a>Właściwości, które kontrolują szybkość osi czasu  
 Klasa <xref:System.Windows.Media.Animation.Timeline> zawiera trzy właściwości określające jego prędkość:  
  
- <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>– Określa, że szybkość, w stosunku do jego <xref:System.Windows.Media.Animation.Timeline>nadrzędnego, w którym czasie postępuje dla . Wartości większe niż jeden zwiększają <xref:System.Windows.Media.Animation.Timeline> szybkość <xref:System.Windows.Media.Animation.Timeline> obiektów podrzędnych i jego podrzędnych; wartości między zerem a jednym spowolnić. Wartość jednego wskazuje, <xref:System.Windows.Media.Animation.Timeline> że postępuje w tym samym tempie co jego element nadrzędny. Ustawienie <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> osi czasu kontenera wpływa również <xref:System.Windows.Media.Animation.Timeline> na wszystkie jego obiekty podrzędne.  
  
- <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>– Określa procent osi <xref:System.Windows.Media.Animation.Timeline.Duration%2A> czasu spędzonej na przyspieszaniu. Na przykład zobacz [Jak: Przyspiesz lub spowolnić animację](how-to-accelerate-or-decelerate-an-animation.md).
  
- <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>- Określa procent <xref:System.Windows.Media.Animation.Timeline.Duration%2A> osi czasu spuszczania. Na przykład zobacz [Jak: Przyspiesz lub spowolnić animację](how-to-accelerate-or-decelerate-an-animation.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Przegląd Animacja i system chronometrażu](animation-and-timing-system-overview.md)
- [Zdarzenia chronometrażu — przegląd](timing-events-overview.md)
- [Tematy in jakże](animation-and-timing-how-to-topics.md)
- [Przykład zachowania chronometrażu animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
