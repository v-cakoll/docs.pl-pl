---
title: Przegląd Animacja i system chronometrażu
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187708"
---
# <a name="animation-and-timing-system-overview"></a>Przegląd Animacja i system chronometrażu
W tym temacie opisano sposób, w <xref:System.Windows.Media.Animation.Timeline>jaki <xref:System.Windows.Media.Animation.Clock> system chronometrażu używa animacji, a klasy do animowania właściwości.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używać animacji do animowania właściwości, zgodnie z opisem w [przeglądzie animacji](animation-overview.md). Pomaga również zapoznać się z właściwości zależności; Aby uzyskać więcej informacji, zobacz [omówienie właściwości zależności](../advanced/dependency-properties-overview.md).  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>Osie czasu i zegary  
 [Omówienie animacji](animation-overview.md) opisano, jak <xref:System.Windows.Media.Animation.Timeline> reprezentuje segment czasu, a <xref:System.Windows.Media.Animation.Timeline> animacja jest typem, który tworzy wartości wyjściowe. Sam w <xref:System.Windows.Media.Animation.Timeline>sobie, nie robi nic innego niż tylko opisać segment czasu. Jest to <xref:System.Windows.Media.Animation.Clock> obiekt osi czasu, który wykonuje prawdziwą pracę. Podobnie animacja faktycznie nie animuje właściwości: klasa animacji opisuje sposób obliczania wartości <xref:System.Windows.Media.Animation.Clock> wyjściowych, ale jest to, który został utworzony dla animacji, która napędza dane wyjściowe animacji i stosuje je do właściwości.  
  
 A <xref:System.Windows.Media.Animation.Clock> jest specjalnym typem obiektu, który zachowuje stan czasu <xref:System.Windows.Media.Animation.Timeline>związany z czasem dla . Zawiera trzy bity informacji, które są niezbędne do <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A> <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>animacji <xref:System.Windows.Media.Animation.Clock.CurrentState%2A>i systemu pomiaru czasu: , , i . A <xref:System.Windows.Media.Animation.Clock> określa jego bieżący czas, postęp i stan przy użyciu <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.Duration%2A>zachowań chronometrażu opisanych przez jego : , <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>i tak dalej.  
  
 W większości przypadków <xref:System.Windows.Media.Animation.Clock> a jest tworzony automatycznie dla osi czasu. Podczas animowania przy <xref:System.Windows.Media.Animation.Storyboard> użyciu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> lub metody, zegary są tworzone automatycznie dla osi czasu i animacji i stosowane do ich właściwości docelowych. Można również utworzyć <xref:System.Windows.Media.Animation.Clock> jawnie przy <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> użyciu <xref:System.Windows.Media.Animation.Timeline>metody programu . Metoda <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType> tworzy zegar odpowiedniego typu dla <xref:System.Windows.Media.Animation.Timeline> którego jest wywoływana. Jeśli <xref:System.Windows.Media.Animation.Timeline> zawiera osi czasu podrzędnych, tworzy <xref:System.Windows.Media.Animation.Clock> obiekty dla nich, jak również. Wynikowe <xref:System.Windows.Media.Animation.Clock> obiekty są rozmieszczone w drzewach, <xref:System.Windows.Media.Animation.Timeline> które pasują do struktury drzewa obiektów, z którego są tworzone.  
  
 Istnieją różne typy zegarów dla różnych typów osi czasu. W poniższej <xref:System.Windows.Media.Animation.Clock> tabeli przedstawiono typy, które odpowiadają niektórym z różnych <xref:System.Windows.Media.Animation.Timeline> typów.  
  
|Typ osi czasu|Typ zegara|Cel zegara|  
|-------------------|----------------|-------------------|  
|Animacja (dziedziczy po <xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|Generuje wartości wyjściowe dla właściwości zależności.|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|Przetwarza plik multimedialny.|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupuje i <xref:System.Windows.Media.Animation.Clock> steruje obiektami podrzędnymi|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|Grupuje i <xref:System.Windows.Media.Animation.Clock> steruje obiektami podrzędnymi|  
  
 Wszystkie <xref:System.Windows.Media.Animation.AnimationClock> obiekty, które tworzysz, można zastosować do <xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A> zgodnych właściwości zależności przy użyciu metody.  
  
 W scenariuszach wymagających dużej wydajności, takich jak animowanie dużej <xref:System.Windows.Media.Animation.Clock> liczby podobnych obiektów, zarządzanie własnym użyciem może zapewnić korzyści z wydajności.  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>Zegary i Menedżer czasu  
 Animowanie obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie — menedżer czasu zarządza <xref:System.Windows.Media.MediaPlayer.Clock%2A> obiektami utworzonymi dla osi czasu. Menedżer czasu jest katalogiem głównym <xref:System.Windows.Media.MediaPlayer.Clock%2A> drzewa obiektów i kontroluje przepływ czasu w tym drzewie.  Menedżer czasu jest tworzony automatycznie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla każdej aplikacji i jest niewidoczny dla dewelopera aplikacji. Menedżer czasu "tyka" wiele razy na sekundę; rzeczywista liczba znaczników, które występują co sekundę różni się w zależności od dostępnych zasobów systemowych. Podczas każdego z tych znaczników menedżer czasu oblicza <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> stan wszystkich obiektów w drzewie chronometrażu.  
  
 Na poniższej ilustracji przedstawiono relację między menedżerem czasu i <xref:System.Windows.Media.Animation.AnimationClock>, a właściwością animowanej zależności.  
  
 ![Elementy systemu rozrządu](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
Animowanie właściwości  
  
 Gdy menedżer czasu zaznacza, aktualizuje <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.Clock> czas każdego w aplikacji. Jeśli <xref:System.Windows.Media.Animation.Clock> jest <xref:System.Windows.Media.Animation.AnimationClock>, używa <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metody, <xref:System.Windows.Media.Animation.AnimationTimeline> z której został utworzony do obliczania jego bieżącej wartości wyjściowej. Dostarcza <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> bieżącego czasu lokalnego, wartość wejściową, która jest zazwyczaj wartość bazową właściwości i domyślną wartość docelową. Po pobraniu wartości animowanego przez <xref:System.Windows.DependencyObject.GetValue%2A> właściwość przy użyciu metody lub jego akcesora CLR, można uzyskać dane wyjściowe jego <xref:System.Windows.Media.Animation.AnimationClock>.  
  
#### <a name="clock-groups"></a>Grupy zegarów  
 W poprzedniej sekcji opisano, jak istnieją <xref:System.Windows.Media.Animation.Clock> różne typy obiektów dla różnych typów osi czasu. Na poniższej ilustracji przedstawiono relację między menedżerem czasu, a <xref:System.Windows.Media.Animation.ClockGroup>, <xref:System.Windows.Media.Animation.AnimationClock>, i animowaną właściwością zależności. A <xref:System.Windows.Media.Animation.ClockGroup> jest tworzony dla osi czasu, które <xref:System.Windows.Media.Animation.Storyboard> grupuje inne osie czasu, takie jak klasa, która grupuje animacje i inne osie czasu.  
  
 ![Elementy systemu rozrządu](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
A ClockGroup  
  
#### <a name="composition"></a>Kompozycja  
 Jest możliwe skojarzenie wielu zegarów z pojedynczą właściwością, w którym to przypadku każdy zegar używa wartości wyjściowej poprzedniego zegara jako jego wartości podstawowej. Na poniższej <xref:System.Windows.Media.Animation.AnimationClock> ilustracji przedstawiono trzy obiekty zastosowane do tej samej właściwości. Clock1 używa wartości podstawowej animowanej właściwości jako jego danych wejściowych i używa go do generowania danych wyjściowych. Clock2 pobiera dane wyjściowe z Clock1 jako jego dane wejściowe i używa go do generowania danych wyjściowych. Clock3 pobiera dane wyjściowe z Clock2 jako jego dane wejściowe i używa go do generowania danych wyjściowych. Gdy wiele zegarów wpływa na tę samą właściwość jednocześnie, mówi się, że w łańcuchu kompozycji.  
  
 ![Elementy systemu rozrządu](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
Łańcuch kompozycji  
  
 Należy zauważyć, że chociaż relacja jest tworzona między danych wejściowych i wyjściowych <xref:System.Windows.Media.Animation.AnimationClock> obiektów w łańcuchu kompozycji, ich zachowania chronometrażu nie są zmieniane; <xref:System.Windows.Media.Animation.Clock> obiekty (w tym <xref:System.Windows.Media.Animation.AnimationClock> obiekty) mają hierarchiczną <xref:System.Windows.Media.Animation.Clock> zależność od ich obiektów nadrzędnych.  
  
 Aby zastosować wiele zegarów do tej <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior> samej <xref:System.Windows.Media.Animation.Storyboard>właściwości, użyj <xref:System.Windows.Media.Animation.AnimationClock>podczas stosowania animacji lub .  
  
#### <a name="ticks-and-event-consolidation"></a>Tyka i konsolidacja zdarzeń  
 Oprócz obliczania wartości wyjściowych menedżer czasu wykonuje inną pracę za każdym razem, gdy zaznacza: określa stan każdego zegara i w razie potrzeby wywołuje zdarzenia.  
  
 Podczas gdy kleszcze występują często, możliwe jest, że między kleszczami wiele rzeczy się wydarzy. Na przykład <xref:System.Windows.Media.Animation.Clock> może być zatrzymany, uruchomiony i zatrzymany ponownie, w którym to przypadku jego <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> wartość zmieni się trzy razy. Teoretycznie <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzenie może być podniesione wiele razy w jednym kleszczu; jednak aparat rozrządu konsoliduje <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> zdarzenia, dzięki czemu zdarzenie może być wywoływane co najwyżej raz na znacznik. Dotyczy to wszystkich zdarzeń chronometrażu: co najwyżej jedno <xref:System.Windows.Media.Animation.Clock> zdarzenie każdego typu jest wywoływane dla danego obiektu.  
  
 Gdy <xref:System.Windows.Media.Animation.Clock> stany przełącza i powraca do pierwotnego stanu między znacznikami <xref:System.Windows.Media.Animation.ClockState.Stopped> (takich <xref:System.Windows.Media.Animation.ClockState.Active>jak zmiana z <xref:System.Windows.Media.Animation.ClockState.Active> do i z powrotem do), skojarzone zdarzenie nadal występuje.  
  
 Aby uzyskać więcej informacji na temat zdarzeń chronometrażu, zobacz [Przegląd zdarzeń chronometrażu](timing-events-overview.md).  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>Bieżące wartości i wartości podstawowe właściwości  
 Animowana właściwość może mieć dwie wartości: wartość bazową i bieżącą wartość. Po ustawieniu właściwości przy użyciu jego <xref:System.Windows.DependencyObject.SetValue%2A> akcesor CLR lub metody, można ustawić jego wartość bazową. Gdy właściwość nie jest animowana, jej wartości podstawowe i bieżące są takie same.  
  
 Podczas animowania właściwości <xref:System.Windows.Media.Animation.AnimationClock> ustawia *bieżącą* wartość właściwości. Pobieranie wartości właściwości za pośrednictwem jego <xref:System.Windows.DependencyObject.GetValue%2A> akcesor CLR <xref:System.Windows.Media.Animation.AnimationClock> lub <xref:System.Windows.Media.Animation.AnimationClock> metoda <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Filling>zwraca dane wyjściowe, gdy jest lub . Wartość podstawową właściwości można pobrać za <xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A> pomocą metody.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](animation-overview.md)
- [Zdarzenia chronometrażu — przegląd](timing-events-overview.md)
- [Przegląd Zachowania chronometrażu](timing-behaviors-overview.md)
