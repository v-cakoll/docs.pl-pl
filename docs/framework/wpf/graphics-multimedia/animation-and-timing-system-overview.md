---
title: Przegląd Animacja i system chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: bfb9a337a604fe8d86d208344d4371748e28f285
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="animation-and-timing-system-overview"></a>Przegląd Animacja i system chronometrażu
W tym temacie opisano, jak system chronometrażu używa animacji, <xref:System.Windows.Media.Animation.Timeline>, i <xref:System.Windows.Media.Animation.Clock> klasy do animowania właściwości.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, można używać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacje do animowania właściwości, zgodnie z opisem w [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Pomaga również należy zapoznać się z właściwości zależności; Aby uzyskać więcej informacji, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>Osie czasu i zegary  
 [Omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) opisano sposób <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu i animacji jest typem <xref:System.Windows.Media.Animation.Timeline> daje wartości danych wyjściowych. Samodzielnie <xref:System.Windows.Media.Animation.Timeline>, nie są wykonywane inne niż opisać odcinka czasu. Jest na osi czasu <xref:System.Windows.Media.Animation.Clock> obiekt, który wykonuje rzeczywistą pracę. Podobnie, animacji nie faktycznie animowania właściwości: klasa animacji w tym artykule opisano sposób obliczania wartości danych wyjściowych, ale jest <xref:System.Windows.Media.Animation.Clock> utworzony dla animacji, które dyski danych wyjściowych animacji i stosuje je do właściwości.  
  
 A <xref:System.Windows.Media.Animation.Clock> to specjalny typ obiektu, który zachowuje związany z czasem stan czasu wykonywania dla <xref:System.Windows.Media.Animation.Timeline>. Zapewnia trzy usługi bits informacji, które są niezbędne do zapewnienia animacji i chronometrażu systemu: <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>, <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>, i <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>. A <xref:System.Windows.Media.Animation.Clock> określa jego bieżący czas, postęp i stan za pomocą zachowań chronometrażu opisanego przez jego <xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>i tak dalej.  
  
 W większości przypadków <xref:System.Windows.Media.Animation.Clock> jest tworzona automatycznie dla osi czasu. Gdy animować przy użyciu <xref:System.Windows.Media.Animation.Storyboard> lub <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zegary są automatycznie tworzone dla osi czasu i animacji i stosowane do ich właściwości docelowej. Można również utworzyć <xref:System.Windows.Media.Animation.Clock> jawnie za pomocą <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> metody z <xref:System.Windows.Media.Animation.Timeline>. <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> Metoda tworzy zegara odpowiedniego typu dla <xref:System.Windows.Media.Animation.Timeline> , na którym jest wywoływana. Jeśli <xref:System.Windows.Media.Animation.Timeline> zawiera podrzędnych osi czasu, tworzy <xref:System.Windows.Media.Animation.Clock> obiektów dla nich również. Powstałe w ten sposób <xref:System.Windows.Media.Animation.Clock> obiekty ułożone w drzewach, które zgodna ze strukturą <xref:System.Windows.Media.Animation.Timeline> drzewa obiektów, z której są tworzone.  
  
 Istnieją różne typy zegary dla różnych typów osi czasu. W poniższej tabeli przedstawiono <xref:System.Windows.Media.Animation.Clock> typy, które odpowiadają różnych <xref:System.Windows.Media.Animation.Timeline> typów.  
  
|Typ osi czasu|Typ zegara|Cel zegara|  
|-------------------|----------------|-------------------|  
|Animacja (dziedziczy <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Generuje dane wyjściowe wartości dla właściwości zależności.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Przetwarza pliku multimedialnego.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupy i kontrolki podrzędnej <xref:System.Windows.Media.Animation.Clock> obiektów|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupy i kontrolki podrzędnej <xref:System.Windows.Media.Animation.Clock> obiektów|  
  
 Można zastosować dowolną <xref:System.Windows.Media.Animation.AnimationClock> obiektów za pomocą tworzenia właściwości zależności zgodne <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> metody.  
  
 W scenariuszach intensywnie wydajności, takich jak animacji dużą liczbą obiektów podobne Zarządzanie własne <xref:System.Windows.Media.Animation.Clock> Użyj zapewniają korzyści wydajności.  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>Zegary i Menedżera czasu  
 Gdy Animowanie obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jest Menedżera czas, który zarządza <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiektów dla sieci osi czasu. Menedżer czasu jest elementem głównym drzewa <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiekty i sterując przepływem czasu, w tym drzewie.  Menedżer czasu jest automatycznie tworzony dla każdego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji i jest niewidoczny dla dewelopera aplikacji. Menedżer czasu parametrem "ticks" wiele razy na sekundę; Rzeczywista liczba Takty występujących każdego drugi zależy od dostępnych zasobów systemowych. Podczas każdej z nich te znaczników czasu Menedżera oblicza stan wszystkich <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> obiektów w drzewie chronometrażu.  
  
 Na poniższej ilustracji przedstawiono relacje między Menedżera czasu i <xref:System.Windows.Media.Animation.AnimationClock>i właściwości animowany zależności.  
  
 ![Czasy składników systemu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animowanie właściwości  
  
 Menedżer czasu znaczniki, aktualizuje czasie co <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> w aplikacji. Jeśli <xref:System.Windows.Media.Animation.Clock> jest <xref:System.Windows.Media.Animation.AnimationClock>, używa <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metody <xref:System.Windows.Media.Animation.AnimationTimeline> z którego został utworzony do obliczenia bieżącym wartość wyjściowa. <xref:System.Windows.Media.Animation.AnimationClock> Dostarcza <xref:System.Windows.Media.Animation.AnimationTimeline> z bieżącym czasem lokalnym, wartości wejściowej, która jest zazwyczaj podstawową wartość właściwości oraz domyślną wartość docelowego. Podczas pobierania wartości animowany za pomocą właściwości <xref:System.Windows.DependencyObject.GetValue%2A> metody lub jej akcesor CLR uzyskać dane wyjściowe jego <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Zegar grup  
 Poprzedniej sekcji opisano, jak są różnego rodzaju <xref:System.Windows.Media.Animation.Clock> obiektów dla różnych typów osi czasu. Na poniższej ilustracji przedstawiono relacje między Menedżera czasu <xref:System.Windows.Media.Animation.ClockGroup>, <xref:System.Windows.Media.Animation.AnimationClock>i właściwości animowany zależności. A <xref:System.Windows.Media.Animation.ClockGroup> jest tworzona dla osi czasu, takich jak grupy innych osi czasu, <xref:System.Windows.Media.Animation.Storyboard> klasy, która grupuje animacji i innych osi czasu.  
  
 ![Czasy składników systemu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>Kompozycja  
 Możliwe do skojarzenia wielu zarejestruje z jednej właściwości, w którym to przypadku każdy używa zegara wartość dane wyjściowe poprzedniego zegara jako jego wartość podstawową. Na poniższej ilustracji przedstawiono trzy <xref:System.Windows.Media.Animation.AnimationClock> obiektów zastosowanych do tej samej właściwości. Clock1 używa wartości podstawowej animowanej właściwości jako dane wejściowe i używa go do generowania danych wyjściowych. Clock2 pobiera dane wyjściowe z Clock1 jako dane wejściowe i używa go do generowania danych wyjściowych. Clock3 pobiera dane wyjściowe z Clock2 jako dane wejściowe i używa go do generowania danych wyjściowych. Wiele zegary wpływać na tę samą właściwość jednocześnie, są określane w łańcuchu kompozycji.  
  
 ![Czasy składników systemu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Łańcuch kompozycji  
  
 Należy pamiętać, że chociaż tworzona jest relacja między wejście i wyjście <xref:System.Windows.Media.Animation.AnimationClock> obiekty w łańcuchu kompozycji ich zachowania chronometrażu nie dotyczy; <xref:System.Windows.Media.Animation.Clock> obiekty (w tym <xref:System.Windows.Media.Animation.AnimationClock> obiektów) zależy od hierarchiczna macierzysty <xref:System.Windows.Media.Animation.Clock> obiektów.  
  
 Aby zastosować zegary wiele z tą samą właściwością, użyj <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> podczas stosowania <xref:System.Windows.Media.Animation.Storyboard>, animacji, lub <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="ticks-and-event-consolidation"></a>Znaczniki i zdarzenia konsolidacji  
 Oprócz obliczanie wartości danych wyjściowych, Menedżera czasu jest inne zadania za każdym razem, gdy go znaczniki: Określa stan każdego zegara i informuje o zdarzeniach, zależnie od potrzeb.  
  
 Gdy znaczniki występuje często, istnieje możliwość, że wiele różnych czynności między taktami. Na przykład <xref:System.Windows.Media.Animation.Clock> może zostać zatrzymana, uruchamiania i zatrzymywania ponownie, w którym to przypadku jego <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> wartości zostaną zmienione trzy razy. Teoretycznie <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzeń można uruchamiany wiele razy w jednym znaczników; jednak aparat chronometrażu konsoliduje zdarzenia, aby <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzenie można zgłaszane co najwyżej raz na osi. Dotyczy to wszystkich zdarzeń chronometrażu: co najwyżej jeden każdego typu zdarzenia dla danego <xref:System.Windows.Media.Animation.Clock> obiektu.  
  
 Gdy <xref:System.Windows.Media.Animation.Clock> zmienia Stany i powraca do stanu pierwotnego między taktami (np. zmiana z <xref:System.Windows.Media.Animation.ClockState.Active> do <xref:System.Windows.Media.Animation.ClockState.Stopped> i z powrotem do <xref:System.Windows.Media.Animation.ClockState.Active>), wystąpi skojarzonego zdarzenia.  
  
 Aby uzyskać więcej informacji na temat zdarzenia czasowe, zobacz [Przegląd zdarzeń chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>Bieżące wartości i wartości podstawowe właściwości  
 Można animować właściwości może mieć dwie wartości: wartość podstawową i bieżącą wartość. Podczas ustawiania właściwości przy użyciu jego akcesor CLR lub <xref:System.Windows.DependencyObject.SetValue%2A> metody, ustaw jej wartość podstawową. Właściwość nie jest animowany, jego podstawowej i bieżące wartości są takie same.  
  
 Gdy animować właściwości, <xref:System.Windows.Media.Animation.AnimationClock> ustawia właściwość *bieżącego* wartość. Podczas pobierania wartości właściwości za pośrednictwem jego akcesor CLR lub <xref:System.Windows.DependencyObject.GetValue%2A> metoda zwraca dane wyjściowe <xref:System.Windows.Media.Animation.AnimationClock> podczas <xref:System.Windows.Media.Animation.AnimationClock> jest <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling>. Podstawową wartość właściwości można pobrać za pomocą <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Zdarzenia chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [Zachowania chronometrażu — przegląd](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
