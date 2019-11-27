---
title: Opis zmian stanu
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: f6ce9875a4ebecf11f1f8d08d681841773d9f841
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447473"
---
# <a name="understanding-state-changes"></a>Opis zmian stanu
W tym temacie omówiono Stany i przejścia, które są dostępne dla kanałów, typy używane do struktury Stanów kanałów oraz sposób ich implementacji.  
  
## <a name="state-machines-and-channels"></a>Automaty stanów i kanały  
 Obiekty, które zajmują się komunikacją, na przykład Sockets zwykle stanowią komputer stanu, którego zmiany stanu odnoszą się do alokowania zasobów sieciowych, tworzenia lub akceptowania połączeń, zamykania połączeń i kończenia komunikacji. Komputer stanu kanału zapewnia jednolity model stanów obiektu komunikacyjnego, który stanowi abstrakcyjną podstawową implementację tego obiektu. Interfejs <xref:System.ServiceModel.ICommunicationObject> udostępnia zestaw Stanów, metody przechodzenia stanu i zdarzenia przejścia stanu. Wszystkie kanały, fabryki kanałów i odbiorniki kanałów implementują komputer stanu kanału.  
  
 Zdarzenia zamknięte, zamykające, błędne, otwarte i otwierające sygnalizujący zewnętrzny obserwator po wystąpieniu przejścia stanu.  
  
 Metody przerywają, zamykają i otwierają (wraz z ich odpowiednikami asynchronicznymi) powodują przejścia stanu.  
  
 Właściwość State zwraca bieżący stan zdefiniowany przez <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Interfejs ICommunicationObject, CommunicationObject i Stany i zmiana stanu  
 <xref:System.ServiceModel.ICommunicationObject> zaczyna się w stanie utworzonym, w którym można skonfigurować różne właściwości. W stanie otwartym obiekt jest używany do wysyłania i otrzymywania komunikatów, ale jego właściwości są uważane za niezmienne. Po zamknięciu obiekt nie może już przetwarzać nowych żądań wysłania lub odebrania, ale istniejące żądania mają szansę ukończenia do momentu osiągnięcia limitu czasu zamknięcia.  Jeśli wystąpi nieodwracalny błąd, obiekt przechodzi do stanu błędu, który można sprawdzić w celu uzyskania informacji o błędzie i ostatecznie zamknięty. Gdy stan jest zamknięty, obiekt zasadniczo osiągnął koniec automatu Stanów. Gdy obiekt przechodzi z jednego stanu do następnego, nie przechodzi do poprzedniego stanu.  
  
 Na poniższym diagramie przedstawiono Stany <xref:System.ServiceModel.ICommunicationObject> i przejścia stanu. Przejścia stanu mogą być spowodowane wywoływaniem jednej z trzech metod: Przerwij, Otwórz lub Zamknij. Mogą być również spowodowane wywoływaniem innych metod specyficznych dla implementacji. Przejście do stanu błędu może wystąpić w wyniku błędów podczas otwierania lub po otwarciu obiektu komunikacyjnego.  
  
 Każdy <xref:System.ServiceModel.ICommunicationObject> zaczyna się w stanie created. W tym stanie aplikacja może skonfigurować obiekt przez ustawienie jego właściwości. Gdy obiekt jest w stanie innym niż utworzony, jest traktowany jako niezmienny.  
  
 ![Diagram przepływu danych przejścia stanu kanału.](./media/understanding-state-changes/channel-state-transitions.gif)  
Rysunek 1. Maszyna stanu Interfejs ICommunicationObject.  
  
 Windows Communication Foundation (WCF) zapewnia abstrakcyjną klasę bazową o nazwie <xref:System.ServiceModel.Channels.CommunicationObject> implementującą <xref:System.ServiceModel.ICommunicationObject> i komputer stanu kanału. Poniższa ilustracja przedstawia zmodyfikowany Diagram stanu, który jest specyficzny dla <xref:System.ServiceModel.Channels.CommunicationObject>. Oprócz automatu Stanów <xref:System.ServiceModel.ICommunicationObject> pokazuje czas, w którym są wywoływane dodatkowe metody <xref:System.ServiceModel.Channels.CommunicationObject>.  
  
 ![Diagram przepływu danychy zmian stanu implementacji programu CommunicationObject.](./media/understanding-state-changes/communicationobject-implementation-state-machine.gif)
Rysunek 2. Implementacja Communicationsobject automatu stanu Interfejs ICommunicationObject, w tym wywołania zdarzeń i metod chronionych.  
  
### <a name="icommunicationobject-events"></a>Zdarzenia Interfejs ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject> uwidacznia pięć zdarzeń zdefiniowanych przez <xref:System.ServiceModel.ICommunicationObject>. Te zdarzenia są przeznaczone do obsługi kodu przy użyciu obiektu komunikacyjnego do powiadamiania o zmianach stanu. Jak pokazano na rysunku 2 powyżej, każde zdarzenie jest uruchamiane jeden raz po przejścia stanu obiektu do stanu o nazwie zdarzenia. Wszystkie pięć zdarzeń są typu `EventHandler`, który jest zdefiniowany jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 W implementacji <xref:System.ServiceModel.Channels.CommunicationObject> nadawca jest albo sam <xref:System.ServiceModel.Channels.CommunicationObject> lub, który został przesłany jako nadawca do konstruktora <xref:System.ServiceModel.Channels.CommunicationObject> (jeśli zostało użyte przeciążenie konstruktora). Parametr EventArgs, `e`, jest zawsze `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Wywołania zwrotne obiektu pochodnego  
 Oprócz pięciu zdarzeń <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje osiem chronionych metod wirtualnych zaprojektowanych tak, aby umożliwić wywoływanie obiektu pochodnego przed przejściami stanu i po nim.  
  
 Metody <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> mają trzy takie wywołania zwrotne, które są skojarzone z każdym z nich. Na przykład odpowiada <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>i <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Skojarzone z <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> są metodami <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType>.  
  
 Podobnie Metoda <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> ma odpowiednie <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Chociaż <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>i <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> nie mają domyślnej implementacji, inne wywołania zwrotne mają domyślną implementację, która jest niezbędna do poprawności komputera stanu. Jeśli zastąpisz te metody, należy wywołać implementację podstawową lub ją poprawnie zastąpić.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> pożaru odpowiednich zdarzeń <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> ustawić stan obiektu na otwarty i zamknięty, a następnie uruchomić odpowiednie zdarzenia <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType>.  
  
### <a name="state-transition-methods"></a>Metody przejściowe stanu  
 <xref:System.ServiceModel.Channels.CommunicationObject> udostępnia implementacje Abort, Zamknij i Otwórz. Zapewnia również metodę błędu, która powoduje przejście stanu do stanu błędu. Rysunek 2 przedstawia automat <xref:System.ServiceModel.ICommunicationObject> stanu z każdym przechodzeniem oznaczonym przez metodę, która powoduje, że (przejścia nieoznaczone jako są wykonywane wewnątrz implementacji metody, która spowodowała ostatnie przejście z etykietą).  
  
> [!NOTE]
> Wszystkie <xref:System.ServiceModel.Channels.CommunicationObject> implementacje stanu komunikacji pobiera/ustawiają synchronizację wątków.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> zawiera trzy konstruktory, a wszystkie obiekty, które opuszczają obiekt w stanie created. Konstruktory są zdefiniowane jako:  
  
 Pierwszy Konstruktor jest konstruktorem bez parametrów, który jest delegatem do przeciążenia konstruktora, który przyjmuje obiekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, który pobiera obiekt używa tego parametru jako obiektu, który ma być zablokowany podczas synchronizowania dostępu do stanu obiektu komunikacji:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Na koniec trzeci Konstruktor przyjmuje dodatkowy parametr, który jest używany jako argument nadawcy w przypadku uruchomienia zdarzeń <xref:System.ServiceModel.ICommunicationObject>.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Dwa poprzednie konstruktory ustawiają nadawcę.  
  
 Open — Metoda  
  
 Warunek wstępny: stan jest tworzony.  
  
 Warunek post: stan jest otwarty lub wystąpił błąd. Może zgłosić wyjątek.  
  
 Metoda Open () podejmie próbę otwarcia obiektu komunikacyjnego i ustawienia stanu na otwarty. Jeśli wystąpi błąd, ustawi stan na błąd.  
  
 Metoda najpierw sprawdza, czy bieżący stan został utworzony. Jeśli bieżący stan jest otwierany lub otwarty, zgłasza <xref:System.InvalidOperationException>. Jeśli bieżący stan jest zamykany lub zamknięty, zgłasza <xref:System.ServiceModel.CommunicationObjectAbortedException>, jeśli obiekt został zakończony i <xref:System.ObjectDisposedException> w inny sposób. Jeśli bieżący stan jest błędny, zgłasza <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Następnie ustawia stan na otwieranie i wywoływanie metody OnOpening () (która wywołuje zdarzenie otwarcia), OnOpen () i OnOpened () w tej kolejności. OnOpened () ustawia stan na otwarty i wywołuje otwarte zdarzenie. Jeśli którykolwiek z tych zgłasza wyjątek, Open () wywołuje błąd () i umożliwia wyszukanie wyjątku. Na poniższym diagramie przedstawiono proces otwierania w bardziej szczegółowy sposób.  
  
 ![Diagram przepływu danychy zmian stanu Interfejs ICommunicationObject. Open.](./media/understanding-state-changes/ico-open-process-override-onopen.gif)  
Zastąp metodę OnOpen, aby zaimplementować niestandardową, otwartą logikę, taką jak otwieranie wewnętrznego obiektu komunikacyjnego.  
  
 Close — Metoda  
  
 Warunek wstępny: Brak.  
  
 Warunek post: stan jest zamknięty. Może zgłosić wyjątek.  
  
 Metodę Close () można wywołać w dowolnym stanie. Próbuje ona zamknąć obiekt w normalny sposób. Jeśli wystąpi błąd, kończy obiekt. Metoda nie wykonuje żadnych operacji, jeśli bieżący stan jest zamykany lub zamknięty. W przeciwnym razie ustawia stan do zamknięcia. Jeśli oryginalny stan został utworzony, otwarcie lub błąd, wywołuje metodę Abort () (zobacz poniższy diagram). Jeśli pierwotny stan został otwarty, wywołuje metodę OnClose () (która wywołuje zdarzenie zamknięcia), w tej kolejności. Jeśli którykolwiek z tych zgłasza wyjątek, zamknięcia () wywołuje metodę Abort () i umożliwia wyszukanie wyjątku. OnClosed () ustawia stan na zamknięty i wywołuje zamknięte zdarzenie. Na poniższym diagramie przedstawiono proces zamykania bardziej szczegółowo.  
  
 ![Diagram przepływu danychy zmian stanu Interfejs ICommunicationObject. Close.](./media/understanding-state-changes/ico-close-process-override-onclose.gif)  
Zastąp metodę OnClose, aby zaimplementować niestandardową logikę zamykającą, na przykład zamykającą wewnętrzny obiekt komunikacyjny. Wszelka dyskretna logika, która może być blokowana przez długi czas (na przykład oczekiwanie na odpowiedź drugiej strony) powinna zostać zaimplementowana w trybie OnClose (), ponieważ przyjmuje parametr timeout i ponieważ nie jest wywoływana jako część przerwania ().  
  
 Przerwij  
  
 Warunek wstępny: Brak.  
Warunek post: stan jest zamknięty. Może zgłosić wyjątek.  
  
 Metoda Abort () nie wykonuje żadnych operacji, jeśli bieżący stan jest zamknięty lub jeśli obiekt został zakończony przed (na przykład może to być operacja Abort () wykonywana w innym wątku). W przeciwnym razie ustawia stan na zamykające i wywołuje metodę OnClose () (która wywołuje zdarzenie zamknięcia), OnAbort () i OnClosed () w tej kolejności (nie wywołuje metody onzamykającej, ponieważ obiekt jest przerywany, nie zamknięty). OnClosed () ustawia stan na zamknięty i wywołuje zamknięte zdarzenie. Jeśli którykolwiek z tych zgłasza wyjątek, zostanie ponownie zgłoszony wywołujący przerwanie. Implementacje onzamykając (), OnClosed () i OnAbort () nie powinny blokować (na przykład na wejściu/wyjściu). Na poniższym diagramie przedstawiono proces przerwania w bardziej szczegółowy sposób.  
  
 ![Diagram przepływu danychy zmian stanu Interfejs ICommunicationObject. Abort.](./media/understanding-state-changes/ico-abort-process-override-onabort.gif)  
Zastąp metodę OnAbort, aby zaimplementować niestandardową logikę zakończenia, taką jak kończenie wewnętrznego obiektu komunikacyjnego.  
  
 Powodu  
  
 Metoda Fault jest specyficzna dla <xref:System.ServiceModel.Channels.CommunicationObject> i nie jest częścią interfejsu <xref:System.ServiceModel.ICommunicationObject>. Jest ona tutaj dostępna do kompletności.  
  
 Warunek wstępny: Brak.  
  
 Po warunku: stan jest błędny. Może zgłosić wyjątek.  
  
 Metoda Fault () nie wykonuje żadnych operacji, jeśli bieżący stan jest błędny lub zamknięty. W przeciwnym razie ustawia stan na błąd i wywołanie onfaultd (), które wywołuje zdarzenie błędu. Jeśli onfaulting zgłosi wyjątek, zostanie ponownie zgłoszony.  
  
### <a name="throwifxxx-methods"></a>Metody ThrowIfXxx  
 Metoda CommunicationObject ma trzy metody chronione, których można użyć do zgłaszania wyjątków, jeśli obiekt jest w określonym stanie.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> zgłasza wyjątek, jeśli stan jest zamykany, zamknięty lub błędny.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> zgłasza wyjątek, jeśli stan nie zostanie utworzony.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> zgłasza wyjątek, jeśli stan nie jest otwarty.  
  
 Zgłoszone wyjątki zależą od stanu. W poniższej tabeli przedstawiono różne Stany i odpowiedni typ wyjątku zgłoszone przez wywołanie elementu ThrowIfXxx, który zgłasza ten stan.  
  
|Stan|Czy wywołano przerwanie?|Wyjątek|  
|-----------|----------------------------|---------------|  
|Utworzono|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otwierania|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otworzyć|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Zamykanie|Tak|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Zamykanie|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Zamknięte|Tak|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> w przypadku, gdy obiekt został zamknięty przez poprzednie i jawne wywołanie przerwania. W przypadku wywołania Close na obiekcie zostanie zgłoszony <xref:System.ObjectDisposedException?displayProperty=nameWithType>.|  
|Zamknięte|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Faulted|Brak|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Limity czasu  
 Kilka metod omówionych przez nas parametrów limitu czasu. Są to zamknięcia, otwarte (Niektóre przeciążenia i wersje asynchroniczne), OnClose i OnOpen. Te metody zostały zaprojektowane w taki sposób, aby zezwalały na długotrwałe operacje (na przykład blokowanie danych wejściowych/wyjściowych i bezpieczne zamykanie połączenia), więc parametr timeout wskazuje, jak długo operacje mogą zostać wprowadzone przed przerwaniem. Implementacje dowolnej z tych metod powinny używać podanej wartości limitu czasu, aby upewnić się, że powraca do obiektu wywołującego w ramach tego limitu czasu. Implementacje innych metod, które nie przyjmują limitu czasu, nie są przeznaczone dla operacji długotrwałych i nie powinny blokować wejścia/wyjścia.  
  
 Wyjątkiem są przeciążenia Open () i Close (), które nie mają limitu czasu. Używają one domyślnej wartości limitu czasu dostarczonej przez klasę pochodną. <xref:System.ServiceModel.Channels.CommunicationObject> uwidacznia dwie chronione właściwości abstrakcyjne o nazwie <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> i <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> zdefiniowane jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Klasa pochodna implementuje te właściwości w celu zapewnienia domyślnego limitu czasu dla przeciążenia Open () i Close (), które nie przyjmują wartości limitu czasu. Następnie do przeciążenia są przekazywane implementacje typu open () i Close (), które zajmują limit czasu podczas przekazywania go do domyślnej wartości limitu czasu, na przykład:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Ten interfejs ma cztery właściwości tylko do odczytu, które zapewniają domyślne wartości limitu czasu dla operacji Otwórz, Wyślij, Odbierz i Zamknij. Każda implementacja jest odpowiedzialna za uzyskanie wartości domyślnych w dowolny sposób. Jako wygoda <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase> domyślne te wartości do 1 minuty każdego.
