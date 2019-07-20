---
title: Opis zmian stanu
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: 549620ee5317e68735b392ce35b73c92f2474eab
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363941"
---
# <a name="understanding-state-changes"></a>Opis zmian stanu
W tym temacie omówiono Stany i przejścia, które są dostępne dla kanałów, typy używane do struktury Stanów kanałów oraz sposób ich implementacji.  
  
## <a name="state-machines-and-channels"></a>Automaty stanów i kanały  
 Obiekty, które zajmują się komunikacją, na przykład Sockets zwykle stanowią komputer stanu, którego zmiany stanu odnoszą się do alokowania zasobów sieciowych, tworzenia lub akceptowania połączeń, zamykania połączeń i kończenia komunikacji. Komputer stanu kanału zapewnia jednolity model stanów obiektu komunikacyjnego, który stanowi abstrakcyjną podstawową implementację tego obiektu. <xref:System.ServiceModel.ICommunicationObject> Interfejs zawiera zestaw Stanów, metody przechodzenia stanu i zdarzenia przejścia stanu. Wszystkie kanały, fabryki kanałów i odbiorniki kanałów implementują komputer stanu kanału.  
  
 Zdarzenia zamknięte, zamykające, błędne, otwarte i otwierające sygnalizujący zewnętrzny obserwator po wystąpieniu przejścia stanu.  
  
 Metody przerywają, zamykają i otwierają (wraz z ich odpowiednikami asynchronicznymi) powodują przejścia stanu.  
  
 Właściwość State zwraca bieżący stan zdefiniowany przez <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Interfejs ICommunicationObject, CommunicationObject i Stany i zmiana stanu  
 <xref:System.ServiceModel.ICommunicationObject> Rozpoczęcie w stanie utworzonym, w którym można skonfigurować różne właściwości. W stanie otwartym obiekt jest używany do wysyłania i otrzymywania komunikatów, ale jego właściwości są uważane za niezmienne. Po zamknięciu obiekt nie może już przetwarzać nowych żądań wysłania lub odebrania, ale istniejące żądania mają szansę ukończenia do momentu osiągnięcia limitu czasu zamknięcia.  Jeśli wystąpi nieodwracalny błąd, obiekt przechodzi do stanu błędu, który można sprawdzić w celu uzyskania informacji o błędzie i ostatecznie zamknięty. Gdy stan jest zamknięty, obiekt zasadniczo osiągnął koniec automatu Stanów. Gdy obiekt przechodzi z jednego stanu do następnego, nie przechodzi do poprzedniego stanu.  
  
 Na poniższym diagramie przedstawiono <xref:System.ServiceModel.ICommunicationObject> Stany i przejścia stanu. Przejścia stanu mogą być spowodowane wywoływaniem jednej z trzech metod: Przerwij, Otwórz lub Zamknij. Mogą być również spowodowane wywoływaniem innych metod specyficznych dla implementacji. Przejście do stanu błędu może wystąpić w wyniku błędów podczas otwierania lub po otwarciu obiektu komunikacyjnego.  
  
 Każde <xref:System.ServiceModel.ICommunicationObject> zaczyna się w stanie created. W tym stanie aplikacja może skonfigurować obiekt przez ustawienie jego właściwości. Gdy obiekt jest w stanie innym niż utworzony, jest traktowany jako niezmienny.  
  
 ![Przejście stanu kanału](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Rysunek 1. Maszyna stanu Interfejs ICommunicationObject.  
  
 Windows Communication Foundation (WCF) zawiera abstrakcyjną klasę bazową <xref:System.ServiceModel.Channels.CommunicationObject> o nazwie <xref:System.ServiceModel.ICommunicationObject> implementującą i maszyną stanu kanału. Poniższa ilustracja przedstawia zmodyfikowany Diagram stanu, który jest specyficzny <xref:System.ServiceModel.Channels.CommunicationObject>dla. Oprócz <xref:System.ServiceModel.ICommunicationObject> komputera stanu pokazuje on czas, gdy są wywoływane dodatkowe <xref:System.ServiceModel.Channels.CommunicationObject> metody.  
  
 ![Zmiany stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Rysunek 2. Implementacja Communicationsobject automatu stanu Interfejs ICommunicationObject, w tym wywołania zdarzeń i metod chronionych.  
  
### <a name="icommunicationobject-events"></a>Zdarzenia Interfejs ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject>uwidacznia pięć zdarzeń zdefiniowanych przez <xref:System.ServiceModel.ICommunicationObject>. Te zdarzenia są przeznaczone do obsługi kodu przy użyciu obiektu komunikacyjnego do powiadamiania o zmianach stanu. Jak pokazano na rysunku 2 powyżej, każde zdarzenie jest uruchamiane jeden raz po przejścia stanu obiektu do stanu o nazwie zdarzenia. Wszystkie pięć zdarzeń są typu, `EventHandler` który jest zdefiniowany jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 W implementacji nadawca jest <xref:System.ServiceModel.Channels.CommunicationObject> sama lub dowolnie przesłany <xref:System.ServiceModel.Channels.CommunicationObject> jako nadawca do konstruktora (jeśli zostało użyte przeciążenie konstruktora). <xref:System.ServiceModel.Channels.CommunicationObject> Parametr EventArgs, `e`,, jest zawsze `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Wywołania zwrotne obiektu pochodnego  
 Oprócz pięciu zdarzeń <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje osiem chronionych metod wirtualnych zaprojektowanych tak, aby umożliwić wywoływanie obiektu pochodnego przed przejściami stanu i po nim.  
  
 Metody i mają trzy takie wywołania zwrotne, <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> które są skojarzone z każdym z nich. <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> Na przykład odpowiada <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>i. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> Skojarzone z <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>to metody <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, i<xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> .  
  
 Podobnie Metoda ma odpowiednie <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType>  
  
 Podczas <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>gdy <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, i<xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> nie ma implementacji domyślnej, inne wywołania zwrotne mają implementację domyślną, która jest niezbędna do poprawności komputera stanu. Jeśli zastąpisz te metody, należy wywołać implementację podstawową lub ją poprawnie zastąpić.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType><xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> Wygeneruj<xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> odpowiednie <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>zdarzenia .<xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> Ustaw stan obiektu na otwarty i zamknięty, a następnie Wygeneruj odpowiednie <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> zdarzenia <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> i.  
  
### <a name="state-transition-methods"></a>Metody przejściowe stanu  
 <xref:System.ServiceModel.Channels.CommunicationObject>zawiera implementacje Abort, Zamknij i Otwórz. Zapewnia również metodę błędu, która powoduje przejście stanu do stanu błędu. Rysunek 2 przedstawia <xref:System.ServiceModel.ICommunicationObject> komputer stanu z każdym przejściem oznaczonym przez metodę, która powoduje, że (przejścia nieoznaczone jako są wykonywane wewnątrz implementacji metody, która spowodowała ostatnie przejście z etykietą).  
  
> [!NOTE]
>  Wszystkie <xref:System.ServiceModel.Channels.CommunicationObject> implementacje stanu komunikacji pobiera/zestawy są zsynchronizowane z wątkiem.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>zawiera trzy konstruktory, z których wszystkie opuszczają obiekt w stanie created. Konstruktory są zdefiniowane jako:  
  
 Pierwszy Konstruktor jest konstruktorem bez parametrów, który jest delegatem do przeciążenia konstruktora, który przyjmuje obiekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, który pobiera obiekt używa tego parametru jako obiektu, który ma być zablokowany podczas synchronizowania dostępu do stanu obiektu komunikacji:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Na koniec trzeci Konstruktor przyjmuje dodatkowy parametr, który jest używany jako argument nadawcy w przypadku <xref:System.ServiceModel.ICommunicationObject> uruchomienia zdarzeń.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Dwa poprzednie konstruktory ustawiają nadawcę.  
  
 Open — Metoda  
  
 Warunek wstępny Stan został utworzony.  
  
 Warunek po: Stan jest otwarty lub wystąpił błąd. Może zgłosić wyjątek.  
  
 Metoda Open () podejmie próbę otwarcia obiektu komunikacyjnego i ustawienia stanu na otwarty. Jeśli wystąpi błąd, ustawi stan na błąd.  
  
 Metoda najpierw sprawdza, czy bieżący stan został utworzony. Jeśli bieżący stan jest otwierany lub otwarty, zgłasza <xref:System.InvalidOperationException>. Jeśli bieżący stan jest zamykany lub zamknięty, zgłasza <xref:System.ServiceModel.CommunicationObjectAbortedException> , że obiekt został zakończony i <xref:System.ObjectDisposedException> w inny sposób. Jeśli bieżący stan jest błędny, zgłasza <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Następnie ustawia stan na otwieranie i wywoływanie metody OnOpening () (która wywołuje zdarzenie otwarcia), OnOpen () i OnOpened () w tej kolejności. OnOpened () ustawia stan na otwarty i wywołuje otwarte zdarzenie. Jeśli którykolwiek z tych zgłasza wyjątek, Open () wywołuje błąd () i umożliwia wyszukanie wyjątku. Na poniższym diagramie przedstawiono proces otwierania w bardziej szczegółowy sposób.  
  
 ![Zmiany stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Zastąp metodę OnOpen, aby zaimplementować niestandardową, otwartą logikę, taką jak otwieranie wewnętrznego obiektu komunikacyjnego.  
  
 Close — Metoda  
  
 Warunek wstępny Brak.  
  
 Warunek po: Stan jest zamknięty. Może zgłosić wyjątek.  
  
 Metodę Close () można wywołać w dowolnym stanie. Próbuje ona zamknąć obiekt w normalny sposób. Jeśli wystąpi błąd, kończy obiekt. Metoda nie wykonuje żadnych operacji, jeśli bieżący stan jest zamykany lub zamknięty. W przeciwnym razie ustawia stan do zamknięcia. Jeśli oryginalny stan został utworzony, otwarcie lub błąd, wywołuje metodę Abort () (zobacz poniższy diagram). Jeśli pierwotny stan został otwarty, wywołuje metodę OnClose () (która wywołuje zdarzenie zamknięcia), w tej kolejności. Jeśli którykolwiek z tych zgłasza wyjątek, zamknięcia () wywołuje metodę Abort () i umożliwia wyszukanie wyjątku. OnClosed () ustawia stan na zamknięty i wywołuje zamknięte zdarzenie. Na poniższym diagramie przedstawiono proces zamykania bardziej szczegółowo.  
  
 ![Zmiany stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO — CloseFlowChartc")  
Zastąp metodę OnClose, aby zaimplementować niestandardową logikę zamykającą, na przykład zamykającą wewnętrzny obiekt komunikacyjny. Wszelka dyskretna logika, która może być blokowana przez długi czas (na przykład oczekiwanie na odpowiedź drugiej strony) powinna zostać zaimplementowana w trybie OnClose (), ponieważ przyjmuje parametr timeout i ponieważ nie jest wywoływana jako część przerwania ().  
  
 Przerwij  
  
 Warunek wstępny Brak.  
Warunek po: Stan jest zamknięty. Może zgłosić wyjątek.  
  
 Metoda Abort () nie wykonuje żadnych operacji, jeśli bieżący stan jest zamknięty lub jeśli obiekt został zakończony przed (na przykład może to być operacja Abort () wykonywana w innym wątku). W przeciwnym razie ustawia stan na zamykające i wywołuje metodę OnClose () (która wywołuje zdarzenie zamknięcia), OnAbort () i OnClosed () w tej kolejności (nie wywołuje metody onzamykającej, ponieważ obiekt jest przerywany, nie zamknięty). OnClosed () ustawia stan na zamknięty i wywołuje zamknięte zdarzenie. Jeśli którykolwiek z tych zgłasza wyjątek, zostanie ponownie zgłoszony wywołujący przerwanie. Implementacje onzamykając (), OnClosed () i OnAbort () nie powinny blokować (na przykład na wejściu/wyjściu). Na poniższym diagramie przedstawiono proces przerwania w bardziej szczegółowy sposób.  
  
 ![Zmiany stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO — AbortFlowChartc")  
Zastąp metodę OnAbort, aby zaimplementować niestandardową logikę zakończenia, taką jak kończenie wewnętrznego obiektu komunikacyjnego.  
  
 Powodu  
  
 Metoda Fault jest specyficzna dla <xref:System.ServiceModel.Channels.CommunicationObject> i nie jest częścią <xref:System.ServiceModel.ICommunicationObject> interfejsu. Jest ona tutaj dostępna do kompletności.  
  
 Warunek wstępny Brak.  
  
 Warunek po: Stan jest błędny. Może zgłosić wyjątek.  
  
 Metoda Fault () nie wykonuje żadnych operacji, jeśli bieżący stan jest błędny lub zamknięty. W przeciwnym razie ustawia stan na błąd i wywołanie onfaultd (), które wywołuje zdarzenie błędu. Jeśli onfaulting zgłosi wyjątek, zostanie ponownie zgłoszony.  
  
### <a name="throwifxxx-methods"></a>Metody ThrowIfXxx  
 Metoda CommunicationObject ma trzy metody chronione, których można użyć do zgłaszania wyjątków, jeśli obiekt jest w określonym stanie.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A>zgłasza wyjątek, jeśli stan jest zamykany, zamknięty lub błędny.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A>zgłasza wyjątek, jeśli stan nie został utworzony.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A>zgłasza wyjątek, jeśli stan nie jest otwarty.  
  
 Zgłoszone wyjątki zależą od stanu. W poniższej tabeli przedstawiono różne Stany i odpowiedni typ wyjątku zgłoszone przez wywołanie elementu ThrowIfXxx, który zgłasza ten stan.  
  
|Stan|Czy wywołano przerwanie?|Wyjątek|  
|-----------|----------------------------|---------------|  
|Utworzono|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otwierania|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otworzyć|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Zamykanie|Tak|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Zamykanie|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Zamknięte|Yes|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>w przypadku, gdy obiekt został zamknięty przez poprzednie i jawne wywołanie przerwania. W przypadku wywołania metody Close na obiekcie zostanie zgłoszony <xref:System.ObjectDisposedException?displayProperty=nameWithType> element.|  
|Zamknięte|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Faulted|Brak|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Limity czasu  
 Kilka metod omówionych przez nas parametrów limitu czasu. Są to zamknięcia, otwarte (Niektóre przeciążenia i wersje asynchroniczne), OnClose i OnOpen. Te metody zostały zaprojektowane w taki sposób, aby zezwalały na długotrwałe operacje (na przykład blokowanie danych wejściowych/wyjściowych i bezpieczne zamykanie połączenia), więc parametr timeout wskazuje, jak długo operacje mogą zostać wprowadzone przed przerwaniem. Implementacje dowolnej z tych metod powinny używać podanej wartości limitu czasu, aby upewnić się, że powraca do obiektu wywołującego w ramach tego limitu czasu. Implementacje innych metod, które nie przyjmują limitu czasu, nie są przeznaczone dla operacji długotrwałych i nie powinny blokować wejścia/wyjścia.  
  
 Wyjątkiem są przeciążenia Open () i Close (), które nie mają limitu czasu. Używają one domyślnej wartości limitu czasu dostarczonej przez klasę pochodną. <xref:System.ServiceModel.Channels.CommunicationObject>uwidacznia dwie chronione właściwości abstrakcyjne <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> o <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> nazwie i zdefiniowane jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Klasa pochodna implementuje te właściwości w celu zapewnienia domyślnego limitu czasu dla przeciążenia Open () i Close (), które nie przyjmują wartości limitu czasu. Następnie do przeciążenia są przekazywane implementacje typu open () i Close (), które zajmują limit czasu podczas przekazywania go do domyślnej wartości limitu czasu, na przykład:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Ten interfejs ma cztery właściwości tylko do odczytu, które zapewniają domyślne wartości limitu czasu dla operacji Otwórz, Wyślij, Odbierz i Zamknij. Każda implementacja jest odpowiedzialna za uzyskanie wartości domyślnych w dowolny sposób. Jako wygoda <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase> domyślne te wartości na 1 minutę każdego.
