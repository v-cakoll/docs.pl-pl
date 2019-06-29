---
title: Opis zmian stanu
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: 858da2a88c17920910c05966bb3b211d754fb278
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424776"
---
# <a name="understanding-state-changes"></a>Opis zmian stanu
W tym temacie omówiono Stany i przejścia, które mają kanały, typy używane do struktury stany kanału i sposobie ich implementacji.  
  
## <a name="state-machines-and-channels"></a>Stan maszyn i kanałów  
 Obiekty, które zajmują się komunikacji, na przykład gniazd, zwykle przedstawiają automatu stanów, w których stanami odnoszą się do przydzielania zasobów sieciowych, dzięki czemu lub może odbierać połączeń, zamykając połączenia i przerywa komunikacji. Automatu stanów kanału zapewnia jednolity model stanów obiektu komunikacyjnego, zapewniający abstrakcję podstawowej implementacji tego obiektu. <xref:System.ServiceModel.ICommunicationObject> Interfejs zapewnia zestaw stanów, stan przejścia metod i zdarzeń przejście stanu. Wszystkie kanały, fabryki kanałów i odbiorników kanału możesz zaimplementować maszynę stanu kanału.  
  
 Zdarzenia zamknięte, zamykanie, Faulted, otwartego i otwieranie sygnał obserwatora zewnętrznych, po wystąpieniu zmiany stanu.  
  
 Metody przerwania, zamknij i Otwórz (i ich odpowiedniki asynchroniczne) powodują stanami.  
  
 Właściwość stanu zwraca bieżący stan, zgodnie z definicją <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>ICommunicationObject, CommunicationObject i Stany i przejścia stanu  
 <xref:System.ServiceModel.ICommunicationObject> Rozpoczyna się w stanie Created, gdzie można skonfigurować jej różne właściwości. Jeden raz w stanie Opened obiektu są wykorzystywane do wysyłania i odbierania wiadomości, ale jego właściwości są traktowane jako niezmienialny. Gdy w stanie zamknięcia obiektu można nie jest już przetwarzać nowych wysyłania lub odbierania żądań, ale istniejącymi żądaniami ma szansę zakończyć aż do osiągnięcia limit czasu zamknięcia.  Jeśli wystąpi błąd nieodwracalny, obiekt przechodzi do stanu Faulted, gdzie może być sprawdzane pod kątem informacji o błędzie i ostatecznie zamknięte. Gdy w stanie zamkniętym obiekt zasadniczo osiągnął koniec automatu stanów. Raz obiektu przejścia z jednego stanu do drugiego, go nie wróć do poprzedniego stanu.  
  
 Na poniższym diagramie przedstawiono <xref:System.ServiceModel.ICommunicationObject> Stany i przejścia stanu. Stan przejścia może być spowodowana przez wywołanie jednej z trzech metod: Przerwij otwieranie, lub Zamknij. One może również być spowodowane wywołaniem innych metod specyficzne dla implementacji. Przejście do stanu Faulted może występować w wyniku błędy podczas otwierania lub po masz otwarty obiekt komunikacyjny.  
  
 Każdy <xref:System.ServiceModel.ICommunicationObject> rozpoczyna się w stanie Created. W tym stanie aplikacji można skonfigurować obiekt przez ustawienie jego właściwości. Gdy obiekt jest w stanie innym niż utworzony, jest uważany za niezmienialny.  
  
 ![Przejście stanu kanału](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Rysunek 1. Automatu stanów ICommunicationObject.  
  
 Windows Communication Foundation (WCF) zapewnia abstrakcyjna klasa bazowa o nazwie <xref:System.ServiceModel.Channels.CommunicationObject> implementującej <xref:System.ServiceModel.ICommunicationObject> i automatu stanów kanału. Poniższa ilustracja jest diagram stanu modyfikacji, które są specyficzne dla <xref:System.ServiceModel.Channels.CommunicationObject>. Oprócz <xref:System.ServiceModel.ICommunicationObject> automatu stanów pokazuje przybliżonego dodatkowe <xref:System.ServiceModel.Channels.CommunicationObject> metody są wywoływane.  
  
 ![Zmianie stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Rysunek 2. Implementacja CommunicationObject ICommunicationObject automatu stanów, łącznie z wywołania zdarzenia i metody chronionej.  
  
### <a name="icommunicationobject-events"></a>Zdarzenia ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject> przedstawia pięć zdarzenia, zdefiniowany przez <xref:System.ServiceModel.ICommunicationObject>. Zdarzenia te zostały zaprojektowane dla kodu za pomocą obiektu komunikacyjnego, aby otrzymywać powiadomienia o zmianie stanu. Jak pokazano na rysunku 2 powyżej, każde zdarzenie jest uruchamiany raz, po stan obiektu przechodzi w stan, o nazwie określonej przez zdarzenie. Wszystkie zdarzenia pięciu są `EventHandler` typu, który jest zdefiniowany jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 W <xref:System.ServiceModel.Channels.CommunicationObject> implementacji nadawcy jest <xref:System.ServiceModel.Channels.CommunicationObject> autonomiczną usługą Intune a niezależnie od rodzaju została przekazana jako nadawcy <xref:System.ServiceModel.Channels.CommunicationObject> konstruktora (jeśli został użyty tego przeciążenia konstruktora). Parametr EventArgs `e`, jest zawsze `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Wywołania zwrotne pochodnego obiektu  
 Oprócz pięciu zdarzenia <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje ośmiu chronione metod wirtualnych, które pozwalają na pochodnej obiekt ma zostać wywołany przed i po zmianie stanu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> metody mają trzy takie wywołania zwrotne związany z każdą z nich. Na przykład, odpowiadający <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ma <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Skojarzone z <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> są <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> metody.  
  
 Podobnie <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> metoda ma odpowiadające mu <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Gdy <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> nie mają domyślnej implementacji, inne wywołania zwrotne mają domyślną implementację, co jest niezbędne pod kątem poprawności maszyny stanu. Jeśli zastąpisz tych metod należy wywoływać implementację podstawową lub poprawnie go zastąpić.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> fire odpowiednich <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> zdarzenia. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> odpowiednio ustawić stan obiektu Opened i zamknięte, a następnie fire odpowiednich <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> zdarzenia.  
  
### <a name="state-transition-methods"></a>Metody przejścia stanu  
 <xref:System.ServiceModel.Channels.CommunicationObject> zawiera implementacje przerwania, zamknij i Otwórz. Zapewnia także metody błędów, co powoduje przejście do stanu Faulted. Na rysunku 2 przedstawiono <xref:System.ServiceModel.ICommunicationObject> automatu stanów z każdym przejściem oznaczone przez metodę, która powoduje, że (bez etykiety przejścia możliwe wewnątrz implementacji metody, która spowodowała ostatnie przejście etykietami).  
  
> [!NOTE]
>  Wszystkie <xref:System.ServiceModel.Channels.CommunicationObject> implementacje komunikacji stanu pobiera/ustawia są synchronizowane wątku.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> zapewnia trzy konstruktory, które należy pozostawić obiekt w stanie Created. Konstruktory są definiowane jako:  
  
 Pierwszy Konstruktor jest konstruktorem domyślnym, który delegował do przeciążenia konstruktora, który przyjmuje obiekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, który pobiera obiekt używa tego parametru jako obiektu zostanie zablokowane podczas synchronizowania dostępu do stanu obiektu komunikacji:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Na koniec trzeci Konstruktor zajmuje dodatkowy parametr, który jest używany jako argument nadawcy podczas <xref:System.ServiceModel.ICommunicationObject> zdarzenia są uruchamiane.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Poprzednie dwa konstruktory to ustawić nadawcy.  
  
 Open — metoda  
  
 Warunek wstępny: Stan jest tworzony.  
  
 Warunek po: Stan to Opened lub Faulted. Może zgłaszać wyjątek.  
  
 Metody Open() podejmie próbę otwarcia obiektu komunikacji i ustawić stan na Opened. Jeśli napotka błąd, zostanie ustawiony stan do Faulted.  
  
 Metoda najpierw sprawdza, czy bieżący stan został utworzony. Jeśli bieżący stan jest otwierania lub otwarciem zgłasza <xref:System.InvalidOperationException>. W przypadku zamknięcia i zamknięte bieżący stan wyniku weryfikacji zgłasza wyjątek <xref:System.ServiceModel.CommunicationObjectAbortedException> Jeśli obiekt został zakończony i <xref:System.ObjectDisposedException> inaczej. Jeśli bieżący stan jest błędne, zgłasza <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Następnie ustawia stan do otwierania i wywołuje OnOpening() (który wywołuje zdarzenie otwierania) i OnOpen() OnOpened() w tej kolejności. OnOpened() ustawia stan Opened i zgłasza zdarzenie Opened. Jeśli dowolny z tych zgłasza wyjątek (Otwórz) wywołuje Fault() i umożliwia bąbelków wyjątek w. Na poniższym diagramie przedstawiono procesu otwierania bardziej szczegółowo.  
  
 ![Zmianie stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Zastąp metodę zdarzenia do zaimplementowania niestandardowej logiki open, takich jak otwieranie obiekt wewnętrzny komunikacji.  
  
 Close — Metoda  
  
 Warunek wstępny: Brak.  
  
 Warunek po: Stan jest zamknięty. Może zgłaszać wyjątek.  
  
 Można wywołać metody Close() w każdym stanie. Próbuje zamykających obiekt w zwykły sposób. W przypadku napotkania błędu kończy obiektu. Metoda ma wartość nothing, jeśli bieżący stan jest zamykany lub zamknięte. W przeciwnym razie ustawia stan zamknięcia. Jeśli pierwotnego stanu została utworzona, otwieranie lub Faulted, wywołuje metodę Abort() (patrz poniższy diagram). Jeśli oryginalny stan został otwarty, wywołuje metodę OnClosing() (który wywołuje zdarzenie zamknięcia) i OnClose() OnClosed() w tej kolejności. Jeśli dowolny z tych zgłasza wyjątek (Zamknij) wywołuje metodę Abort() i umożliwia bąbelków wyjątek. OnClosed() ustawia stan na zamknięte i zgłasza zdarzenie zamknięte. Na poniższym diagramie przedstawiono zamknięciu przetwarzania bardziej szczegółowo.  
  
 ![Zmianie stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Zastąp metodę OnClose — Aby zaimplementować logikę niestandardową Zamknij, np. zamknięcie obiekt wewnętrzny komunikacji. Wszystkie łagodne zamykanie logikę, która może blokować długo (np. Trwa oczekiwanie na drugiej stronie odpowiadać) powinny być zrealizowane w OnClose(), ponieważ pobiera on parametr limitu czasu i ponieważ nie jest wywoływana jako część metodę Abort().  
  
 Przerwij  
  
 Warunek wstępny: Brak.  
Warunek po: Stan jest zamknięty. Może zgłaszać wyjątek.  
  
 Metoda metodę Abort() nie działają, jeśli bieżącym stanem nie jest zamknięty lub jeśli obiekt został zakończony przed (na przykład prawdopodobnie przez metodę Abort() wykonywania w innym wątku). W przeciwnym razie ustawia stan do zamknięcia i wywołuje OnClosing() (który wywołuje zdarzenie zamknięcia), OnAbort() i OnClosed() w tej kolejności (nie wywołuje OnClose — ponieważ obiekt zostanie przerwany, nie jest zamknięty). OnClosed() ustawia stan na zamknięte i zgłasza zdarzenie zamknięte. Jeśli któregoś z powyższych zgłosić wyjątek, jest ponownie zgłoszony do obiektu wywołującego przerwania. Implementacje OnClosing(), OnClosed() i OnAbort() nie powinny blokować (na przykład na We/Wy). Na poniższym diagramie przedstawiono proces przerwania bardziej szczegółowo.  
  
 ![Zmianie stanu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Zastąpienie metody OnAbort implementacji niestandardowych Zakończ logiki, takie jak przerywanie obiekt wewnętrzny komunikacji.  
  
 Błędów  
  
 Metoda błędów zależy od <xref:System.ServiceModel.Channels.CommunicationObject> i nie jest częścią <xref:System.ServiceModel.ICommunicationObject> interfejsu. Została ona tutaj uwzględniona aby informacje były kompletne.  
  
 Warunek wstępny: Brak.  
  
 Warunek po: Stan jest błędne. Może zgłaszać wyjątek.  
  
 Metoda Fault() nie działa w przypadku bieżącego stanu Faulted lub zamknięte. W przeciwnym razie ustawia stan Faulted, a następnie wywołać OnFaulted(), który wywołuje zdarzenie Faulted. Jeśli OnFaulted zgłasza wyjątek jest ponownie zgłoszony.  
  
### <a name="throwifxxx-methods"></a>Metody ThrowIfXxx  
 CommunicationObject ma trzy metody chronionych, których można użyć zgłaszają wyjątki, jeśli obiekt jest w określonym stanie.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> zgłasza wyjątek, jeśli stan jest zamknięcia, zamknięte lub Faulted.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> zgłasza wyjątek, jeśli stan nie został utworzony.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> zgłasza wyjątek, jeśli stan nie jest otwarty.  
  
 Wyjątki generowane są zależne od stanu. W poniższej tabeli przedstawiono różne stany i odpowiedni typ wyjątek zgłoszony przez wywołanie metody ThrowIfXxx, która zgłasza w tym stanie.  
  
|Stan|Została wywołana przerwania?|Wyjątek|  
|-----------|----------------------------|---------------|  
|Utworzono|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otwieranie|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otwarte|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Zamykanie|Yes|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Zamykanie|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Zamknięte|Tak|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> w przypadku, że obiekt został zamknięty przez poprzednie i jawne wywołanie przerwania. Jeśli możesz wywołać operację Close dla obiektu, a następnie <xref:System.ObjectDisposedException?displayProperty=nameWithType> zgłaszany.|  
|Zamknięte|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Wystąpił błąd|Brak|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Limity czasu  
 Kilka metod, które Omówiliśmy przyjmują parametry limitu czasu. Są to zamknij i Otwórz (niektóre przeciążenia i asynchronicznych wersji), OnClose zdarzenia. Te metody są zaprojektowane z myślą długotrwałej operacji (np. blokowania na We/Wy podczas bezpiecznie zamknąć połączenie), parametr limitu czasu wskazuje, ile takich operacji może zająć przed są przerwane. Implementacje dowolnej z tych metod powinny używać wartości podany limit czasu, aby upewnić się, że powraca do obiektu wywołującego w ramach tego limitu czasu. Implementacje innych metod, które nie przyjmują przekroczenie limitu czasu nie są przeznaczone dla długotrwałej operacji i nie powinny blokować na dane wejściowe i wyjściowe.  
  
 Wyjątkiem są Open() i Close() przeciążenia, które nie przyjmują przekroczenie limitu czasu. Te Użyj domyślnej wartości limitu czasu pochodzącego z klasy pochodnej. <xref:System.ServiceModel.Channels.CommunicationObject> udostępnia dwa chronione właściwości abstrakcyjnych, o nazwie <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> i <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> zdefiniowany jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Klasa pochodna implementuje te właściwości, aby podać domyślny limit czasu dla Open() i Close() przeciążeń, które nie przyjmują wartość limitu czasu. Następnie implementacji metody Open() i Close() delegować do przeciążenia, które przyjmuje przekazanie do niej domyślnej wartości limitu czasu, na przykład limit czasu:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Ten interfejs ma cztery właściwości tylko do odczytu do prezentowania domyślne wartości limitów czasu dla otwierania, wysyłanie, odbieranie i zamykania. Każda implementacja jest odpowiedzialny za uzyskanie wartości domyślne w jakikolwiek sposób, które są odpowiednie. Dla wygody <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase> domyślne te wartości na 1 minutę.
