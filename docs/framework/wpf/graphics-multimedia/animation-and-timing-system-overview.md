---
title: Przegląd Animacja i system chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: f64431e7804ba6e068a3d05f512c6ead089d7712
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079321"
---
# <a name="animation-and-timing-system-overview"></a>Przegląd Animacja i system chronometrażu
W tym temacie opisano, jak korzysta z system chronometrażu animacji, <xref:System.Windows.Media.Animation.Timeline>, i <xref:System.Windows.Media.Animation.Clock> klasy, aby animować właściwości.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, powinno być możliwe do użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji, aby animować właściwości zgodnie z opisem w [Przegląd animacja](animation-overview.md). Pozwala ona również należy zapoznać się z właściwości zależności; Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Osie czasu i zegary  
 [Przegląd animacja](animation-overview.md) opisany sposób <xref:System.Windows.Media.Animation.Timeline> reprezentuje odcinek czasu, a także animację jest typem <xref:System.Windows.Media.Animation.Timeline> która wytwarza wartości danych wyjściowych. Przez siebie <xref:System.Windows.Media.Animation.Timeline>, nic nie robi inny niż segmentu czasu jego opis. Jest to oś czasu <xref:System.Windows.Media.Animation.Clock> obiekt, który wykonuje rzeczywistą pracę. Podobnie, animacja nie faktycznie animować właściwości: klasa animacji w tym artykule opisano sposób obliczania wartości danych wyjściowych, ale jest <xref:System.Windows.Media.Animation.Clock> utworzony podczas tworzenia animacji, który dyski danych wyjściowych animacji i stosuje je do właściwości.  
  
 A <xref:System.Windows.Media.Animation.Clock> to specjalny typ obiektu, który przechowuje związany stan czasu wykonywania dla <xref:System.Windows.Media.Animation.Timeline>. Zapewnia trzy bity informacji, które są niezbędne do Animacja i system chronometrażu: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, i <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> określa jego bieżący czas, postępu i stanu przy użyciu zachowania chronometrażu opisanego przez jego <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>i tak dalej.  
  
 W większości przypadków <xref:System.Windows.Media.Animation.Clock> jest tworzona automatycznie na osi czasu. Gdy animowanie za pomocą <xref:System.Windows.Media.Animation.Storyboard> lub <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zegary są automatycznie utworzone dla osi czasu i animacje i dotyczą ich właściwości docelowych. Można również utworzyć <xref:System.Windows.Media.Animation.Clock> jawnie przy użyciu <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metody usługi <xref:System.Windows.Media.Animation.Timeline>. <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> Metoda tworzy zegara dla odpowiednich typów <xref:System.Windows.Media.Animation.Timeline> , na którym jest wywoływana. Jeśli <xref:System.Windows.Media.Animation.Timeline> zawiera podrzędnych osi czasu, tworzy on <xref:System.Windows.Media.Animation.Clock> obiekty dla nich. Wartość wynikowa <xref:System.Windows.Media.Animation.Clock> obiektów jest rozmieszczonych w drzewach, które zgodna ze strukturą <xref:System.Windows.Media.Animation.Timeline> drzewa obiektów, z którego są tworzone.  
  
 Istnieją różne rodzaje zegary dla różnych typów osi czasu. W poniższej tabeli przedstawiono <xref:System.Windows.Media.Animation.Clock> typy, które odpowiadają różnych <xref:System.Windows.Media.Animation.Timeline> typów.  
  
|Typ osi czasu|Typ zegara|Cel zegara|  
|-------------------|----------------|-------------------|  
|Animacji (dziedziczy <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Generuje dane wyjściowe wartości dla właściwości zależności.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Przetwarza plik multimedialny.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupy i formanty jego podrzędny <xref:System.Windows.Media.Animation.Clock> obiektów|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupy i formanty jego podrzędny <xref:System.Windows.Media.Animation.Clock> obiektów|  
  
 Można zastosować dowolną <xref:System.Windows.Media.Animation.AnimationClock> obiekty właściwości zależności zgodne tworzone przy użyciu <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> metody.  
  
 W scenariuszach intensywnie korzystających z wydajności, takich jak animowanie dużej liczby podobnych obiektów zarządzania własnych <xref:System.Windows.Media.Animation.Clock> Użyj zapewniają korzyści wydajności.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Zegary i Menedżer czas  
 Gdy Animowanie obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jest Menedżer czas, który zarządza <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiektów dla swojej osi czasu. Menedżer czas jest głównym drzewa <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiektów i przepływem czas w drzewie.  Menedżer czas jest tworzona automatycznie dla każdego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji i jest niewidoczna dla dewelopera aplikacji. Menedżer czas "znaczników" wiele razy na sekundę; Rzeczywista liczba znaczników, które występują, każdy drugi różni się w zależności od dostępnych zasobów systemowych. Podczas każdej z nich te taktów Menedżer czas oblicza stan wszystkich <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> obiektów w drzewie chronometrażu.  
  
 Na poniższej ilustracji przedstawiono relacje między Menedżer czas i <xref:System.Windows.Media.Animation.AnimationClock>i właściwość zależności animowany.  
  
 ![Czasy składników systemu](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animowanie właściwości  
  
 Menedżer czas znaczniki, aktualizuje czasie co <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> w aplikacji. Jeśli <xref:System.Windows.Media.Animation.Clock> jest <xref:System.Windows.Media.Animation.AnimationClock>, używa ona <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metody <xref:System.Windows.Media.Animation.AnimationTimeline> z której została utworzona w celu obliczania bieżącym danych wyjściowych wartość. <xref:System.Windows.Media.Animation.AnimationClock> Dostarcza <xref:System.Windows.Media.Animation.AnimationTimeline> z bieżącym czasem lokalnym, wartości wejściowej, która jest zwykle podstawowej wartości właściwości i wartość domyślną docelowego. Podczas pobierania wartości animowany przy użyciu właściwości <xref:System.Windows.DependencyObject.GetValue%2A> metody lub jego metoda dostępu do środowiska CLR, otrzymasz dane wyjściowe jego <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Grupy zegara  
 Poprzedniej sekcji opisano, jak istnieją różne rodzaje <xref:System.Windows.Media.Animation.Clock> obiektów dla różnych typów osi czasu. Na poniższej ilustracji przedstawiono relacje między Menedżer czas <xref:System.Windows.Media.Animation.ClockGroup>, <xref:System.Windows.Media.Animation.AnimationClock>i właściwość zależności animowany. A <xref:System.Windows.Media.Animation.ClockGroup> jest tworzona dla osi czasu, które grupy innych osi czasu, takich jak <xref:System.Windows.Media.Animation.Storyboard> klasy, która grupuje animacji i innych osi czasu.  
  
 ![Czasy składników systemu](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
A ClockGroup  
  
#### <a name="composition"></a>Kompozycja  
 Może się zdarzyć, aby skojarzyć wiele zegary przy użyciu pojedynczej właściwości, w którym to przypadku każdy używa zegara wartość danych wyjściowych poprzedniego zegara jako jego podstawowej wartości. Na poniższej ilustracji przedstawiono trzy <xref:System.Windows.Media.Animation.AnimationClock> obiektów zastosowanych do tej samej właściwości. Clock1 używa wartości bazowej animowany właściwości jako dane wejściowe i używa go w celu wygenerowania danych wyjściowych. Clock2 pobiera dane wyjściowe z Clock1 jako dane wejściowe i używa ich do generowania danych wyjściowych. Clock3 pobiera dane wyjściowe z Clock2 jako dane wejściowe i używa ich do generowania danych wyjściowych. Zegary wielu wpływać na tę samą właściwość jednocześnie, są określane w łańcuchu kompozycji.  
  
 ![Czasy składników systemu](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Łańcuch kompozycji  
  
 Należy zauważyć, że tworzona jest relacja między dane wejściowe i wyjściowe <xref:System.Windows.Media.Animation.AnimationClock> obiekty w łańcuchu kompozycji nie wpływają na ich zachowania chronometrażu; <xref:System.Windows.Media.Animation.Clock> obiektów (w tym <xref:System.Windows.Media.Animation.AnimationClock> obiektów) są hierarchiczne zależne od ich nadrzędnej <xref:System.Windows.Media.Animation.Clock> obiektów.  
  
 Aby zastosować wiele zegary w tej samej właściwości, należy użyć <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> podczas stosowania <xref:System.Windows.Media.Animation.Storyboard>, animacji, lub <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Znaczniki osi i konsolidacji zdarzeń  
 Oprócz obliczanie wartości danych wyjściowych, Menedżer czas działa inne za każdym razem, gdy jej znaczniki: Określa stan każdego zegara i wywołuje zdarzenia, zgodnie z potrzebami.  
  
 Gdy impulsów występuje często, istnieje możliwość, że wiele rzeczy do wykonania między taktami. Na przykład <xref:System.Windows.Media.Animation.Clock> może można zatrzymać, uruchamiać i zatrzymywać ponownie, w którym to przypadku jego <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> wartość zostanie zmieniona trzy razy. Teoretycznie <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzeń może zostać podniesiony wiele razy w jednym znaczników; jednak aparat chronometrażu konsoliduje zdarzenia, tak aby <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzenie może zostać wywołane co najwyżej raz na jednostkę skali. Ta zasada obowiązuje dla wszystkich zdarzeń czasu: każdego typu co najwyżej jedno zdarzenie jest wywoływane dla danego <xref:System.Windows.Media.Animation.Clock> obiektu.  
  
 Gdy <xref:System.Windows.Media.Animation.Clock> zmienia Stany i zwraca z powrotem do pierwotnego stanu między taktami (takie jak zmienianie docelowej z <xref:System.Windows.Media.Animation.ClockState.Active> do <xref:System.Windows.Media.Animation.ClockState.Stopped> i z powrotem do <xref:System.Windows.Media.Animation.ClockState.Active>), nadal występuje w skojarzonym zdarzeniu.  
  
 Aby uzyskać więcej informacji na temat zdarzenia chronometrażu zobacz [zdarzenia chronometrażu — Przegląd](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Bieżące wartości i wartości podstawowe właściwości  
 Właściwość animatable może mieć dwie wartości: wartości bazowej i bieżącą wartość. Po ustawieniu właściwości przy użyciu jego metoda dostępu CLR lub <xref:System.Windows.DependencyObject.SetValue%2A> metody, ustawiamy jej wartość podstawowy. Właściwość nie jest animowany, jego podstawowej i bieżących wartości są takie same.  
  
 Kiedy animujemy właściwość <xref:System.Windows.Media.Animation.AnimationClock> ustawia właściwość *bieżącego* wartość. Podczas pobierania wartości właściwości, za pośrednictwem jego metoda dostępu CLR lub <xref:System.Windows.DependencyObject.GetValue%2A> metoda zwraca dane wyjściowe <xref:System.Windows.Media.Animation.AnimationClock> podczas <xref:System.Windows.Media.Animation.AnimationClock> jest <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling>. Podstawowa wartość właściwości można pobrać za pomocą <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> metody.  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Zdarzenia chronometrażu — przegląd](timing-events-overview.md)
- [Zachowania chronometrażu — przegląd](timing-behaviors-overview.md)
