---
title: Opis zmian stanu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 972b7e0ed9ffbc9f9ddecb2ab7afdd08626fde19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-state-changes"></a>Opis zmian stanu
W tym temacie omówiono Stany i przejść, które mają kanały, typy używane do stanów kanału struktury i sposobu ich wdrażania.  
  
## <a name="state-machines-and-channels"></a>Stan maszyny i kanały  
 Obiekty, które zajmują się komunikacji, na przykład gniazda, zwykle stanowi automatu stanów przejść stanu, którego odnoszą się do przydzielania zasobów sieciowych, przez co lub odbierać połączeń, zamykając połączenia i przerywa komunikacji. Komputer stanu kanału udostępnia model uniform stanów obiektu komunikacji abstracts ta implementacja tego obiektu. <xref:System.ServiceModel.ICommunicationObject> Interfejs zawiera zestaw stanów, metod przejścia stanu i zdarzeń przejścia stanu. Wszystkie kanały, fabryk kanałów i odbiorników kanału implementuje kanału komputera stanu.  
  
 Zdarzenia zamknięte, Zamknij, Faulted, Opened i otwarcia sygnał obserwatora zewnętrznych po wystąpieniu przejście stanu.  
  
 Metody Abort, zamknij i Otwórz (i ich odpowiedniki asynchroniczne) spowodować przejścia stanu.  
  
 Właściwość state zwraca bieżący stan, zgodnie z definicją w <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Interfejs ICommunicationObject, CommunicationObject i stanów i przejścia stanu  
 <xref:System.ServiceModel.ICommunicationObject> Rozpoczyna się w stanie Created, gdzie można skonfigurować różne właściwości. Raz w stanie otwartym obiektu jest gotowa do wysyłania i odbierania wiadomości, ale jego właściwości są traktowane jako niezmienialny. Gdy w stanie zamknięcia obiektu można już przetworzyć nowej wysyłania i odbierania żądań, ale istniejących żądań ma możliwość wykonania do osiągnięto limit czasu zamknięcia.  Jeśli wystąpi błąd nieodwracalny, obiekt przechodzi w stan końcowy: Faulted, gdzie można sprawdzane pod kątem informacji o błędzie, a ostatecznie jest zamknięty. Gdy w stanie zamkniętym obiektu zasadniczo osiągnął koniec automatu stanów. Raz przejść obiektu z jednego stanu do następnego go nie wróć do poprzedniego stanu.  
  
 Na poniższym diagramie przedstawiono <xref:System.ServiceModel.ICommunicationObject> tany i przejścia stanu. Stan przejścia może być spowodowana przez wywoływanie jednej z trzech metod: Abort, Otwórz, lub Zamknij. One może również być spowodowane wywołaniem innych metod konkretnej implementacji. Przejście w stan końcowy: Faulted może występować w wyniku błędy podczas otwierania lub po o otworzyć obiektu komunikacji.  
  
 Każdy <xref:System.ServiceModel.ICommunicationObject> rozpoczyna się w stanie Created. W tym stanie aplikacji można skonfigurować obiektu jego właściwości. Gdy obiekt jest w stanie innym niż utworzony, jest uważany za niezmienialny.  
  
 ![Kanał transitition stanu](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Rysunek 1. Komputer stanu interfejs ICommunicationObject.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]udostępnia abstrakcyjną klasę podstawową o nazwie <xref:System.ServiceModel.Channels.CommunicationObject> implementującej <xref:System.ServiceModel.ICommunicationObject> i kanał komputera stanu. Poniższa ilustracja jest diagram stanu modyfikacji, która jest specyficzna dla <xref:System.ServiceModel.Channels.CommunicationObject>. Oprócz <xref:System.ServiceModel.ICommunicationObject> komputera stanu przedstawia czas, gdy dodatkowe <xref:System.ServiceModel.Channels.CommunicationObject> metody są wywoływane.  
  
 ![Zmiany stanów](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Rysunek 2. Implementacja CommunicationObject automatu stanów interfejs ICommunicationObject tym wywołania zdarzenia i chronione metody.  
  
### <a name="icommunicationobject-events"></a>Interfejs ICommunicationObject zdarzeń  
 <xref:System.ServiceModel.Channels.CommunicationObject>Opisuje pięć zdarzenia, zdefiniowany przez <xref:System.ServiceModel.ICommunicationObject>. Zdarzenia te zostały zaprojektowane dla kodu za pomocą obiektu komunikacji ma być powiadamiany o przejścia stanu. Jak pokazano na rysunku 2 powyżej, każde zdarzenie jest uruchamiany raz po stan obiektu przechodzi do stanu o nazwie przez zdarzenie. Wszystkie zdarzenia pięć są `EventHandler` typu, który jest zdefiniowany jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 W <xref:System.ServiceModel.Channels.CommunicationObject> implementacji, nadawca jest albo <xref:System.ServiceModel.Channels.CommunicationObject> siebie lub niezależnie od przekazany jako nadawcy <xref:System.ServiceModel.Channels.CommunicationObject> — Konstruktor (jeśli użyto tego przeładowania konstruktora). Parametr EventArgs `e`, jest zawsze `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Wywołania zwrotne pochodnej obiektu  
 Oprócz pięciu zdarzeń <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje osiem chronione metody wirtualne pozwala pochodnego obiektu być wywołanie zwrotne przed i po zmianie stanu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> metody mieć trzy tych wywołań zwrotnych skojarzone z każdym z nich. Na przykład odpowiadający <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> jest <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Skojarzone z <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> są <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> metody.  
  
 Podobnie <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> metoda ma odpowiadające mu <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Gdy <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> mieć żadnej implementacji domyślnej, wywołania zwrotne domyślną implementację, które są niezbędne do stanu prawidłowości maszyny. Jeśli zastępować te metody należy wywoływać implementację podstawową lub nieprawidłowo go zastąpić.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> wyzwalać odpowiadającego <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> zdarzenia. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>i <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> odpowiednio ustaw stan obiektu Opened i zamknięte, a następnie uruchomienie odpowiadającego <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> zdarzenia.  
  
### <a name="state-transition-methods"></a>Metody przejścia stanu  
 <xref:System.ServiceModel.Channels.CommunicationObject>zawiera implementacje przerwania, zamknij i Otwórz. Umożliwia także metodę błędów, która powoduje przejście do stanu Faulted. Na rysunku 2 przedstawiono <xref:System.ServiceModel.ICommunicationObject> automatu stanów z każdego przejścia z etykietą przez metodę, która go (bez etykiety przejścia wystąpić wewnątrz implementacji metody, która spowodowała ostatniego przejścia etykietą).  
  
> [!NOTE]
>  Wszystkie <xref:System.ServiceModel.Channels.CommunicationObject> implementacje komunikacji stanu pobiera i ustawia są synchronizowane wątku.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>udostępnia trzy konstruktorów, które pozostawienie obiektu w stanie Created. Konstruktory są zdefiniowane jako:  
  
 Pierwszy Konstruktor jest domyślny konstruktor, który deleguje do przeładowania konstruktora, który pobiera obiekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, który pobiera obiekt używa parametru jako obiekt zablokowane podczas synchronizowania dostęp do stanu obiektu komunikacji:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Na koniec trzeci Konstruktor ma dodatkowy parametr, który jest używany jako argumentu sender podczas <xref:System.ServiceModel.ICommunicationObject> uruchomienia zdarzeń.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Poprzednie dwa konstruktory to ustawić nadawcy.  
  
 Open — metoda  
  
 Warunek wstępny: Stan jest tworzony.  
  
 Po warunek: Stan jest otwartym lub Faulted. Może zgłosić wyjątek.  
  
 Metoda metody Open() spróbuje otworzyć obiektu komunikacji i ustawić stan na Opened. W przypadku napotkania błędu go ustawi stan końcowy: Faulted.  
  
 Metoda najpierw sprawdza, czy bieżący stan to utworzony. Jeśli bieżący stan jest otwierania lub otworzył zgłasza <xref:System.InvalidOperationException>. W przypadku zamknięcia lub zamknięty bieżący stan zgłasza <xref:System.ServiceModel.CommunicationObjectAbortedException> Jeśli obiekt został zakończony i <xref:System.ObjectDisposedException> inaczej. Jeśli bieżący stan jest uszkodzona, zgłasza <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Następnie ustawia stan do otwierania i wywołuje OnOpening() (który wywołuje zdarzenie otwierający), OnOpen() i OnOpened() w podanej kolejności. OnOpened() ustawia stan do otwartego i zgłasza zdarzenie Opened. Jeśli dowolny z tych zgłasza wyjątek (Otwórz) wywołuje Fault() i umożliwia bąbelków wyjątek w. Na poniższym diagramie przedstawiono proces Otwórz bardziej szczegółowo.  
  
 ![Zmiany stanów](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Zastąp metodę zdarzenia w celu wykonania niestandardowej logiki otwarte, takie jak otwieranie obiektu komunikacji wewnętrznej.  
  
 Close — Metoda  
  
 Warunek wstępny: Brak.  
  
 Po warunek: Stan jest zamknięty. Może zgłosić wyjątek.  
  
 Na każdy stan można wywołać metody Close(). Próbuje Zamknij obiekt normalnie. Jeśli wystąpi błąd, zostaje zakończone obiektu. Metoda nie nic, jeśli bieżący stan jest zamykany lub zamknięty. W przeciwnym razie ustawia stan zamknięcia. Jeśli oryginalny stan został utworzony, otwieranie lub Faulted, wywołuje metodę Abort() (zobacz poniższy rysunek). Jeśli zostało otwarte pierwotnego stanu, wywołuje metodę OnClosing() (który wywołuje zdarzenie zamknięcia), OnClose() i OnClosed() w podanej kolejności. Jeśli dowolny z tych zgłasza wyjątek (Zamknij) wywołuje metodę Abort() i umożliwia bąbelków wyjątek w. OnClosed() ustawia stanu na zamknięty i zgłasza zdarzenie zamknięte. Na poniższym diagramie przedstawiono zamknięcia przetworzyć bardziej szczegółowo.  
  
 ![Zmiany stanów](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Zastąp metodę OnClose w celu wykonania niestandardowej logiki Zamknij, takich jak zamknięcia obiektu komunikacji wewnętrznej. Wszystkie łagodne zamykanie logiki, które mogą zablokować dla długo (np. oczekiwanie na drugiej stronie odpowiada) powinny być implementowane w OnClose(), ponieważ ma on parametr limitu czasu i dlatego nie jest wywoływany jako część Abort().  
  
 Przerwania  
  
 Warunek wstępny: Brak.  
Po warunek: Stan jest zamknięty. Może zgłosić wyjątek.  
  
 Metodę Abort() nie działają, jeśli bieżącym stanem nie jest zamknięty lub jeśli obiekt został zakończony przed (na przykład, prawdopodobnie przez metodę Abort() wykonywanych na inny wątek). W przeciwnym razie ustawia stan zamknięcia i wywołuje OnClosing() (który wywołuje zdarzenie zamknięcia), OnAbort() i OnClosed() w tej kolejności (nie wywołuje OnClose ponieważ obiekt jest przerywane, niezamknięte). OnClosed() ustawia stanu na zamknięty i zgłasza zdarzenie zamknięte. Jeśli dowolne z tych zgłosić wyjątek, jest ponownie zgłoszone do obiektu wywołującego przerwania. Implementacje OnClosing(), OnClosed() i OnAbort() nie powinny blokować (na przykład na We/Wy). Na poniższym diagramie przedstawiono proces przerwania bardziej szczegółowo.  
  
 ![Zmiany stanów](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Zastąpienie metody OnAbort do zaimplementowania niestandardowego przerwanie logiki, takich jak przerywanie obiektu komunikacji wewnętrznej.  
  
 Błąd  
  
 Metoda błędów jest specyficzne dla <xref:System.ServiceModel.Channels.CommunicationObject> i nie jest częścią <xref:System.ServiceModel.ICommunicationObject> interfejsu. Został uwzględniony w tym miejscu aby informacje były kompletne.  
  
 Warunek wstępny: Brak.  
  
 Po warunek: Stan jest uszkodzona. Może zgłosić wyjątek.  
  
 Metoda Fault() nie działają, jeśli bieżący stan końcowy: Faulted lub zamknięty. W przeciwnym razie ustawia stan końcowy: Faulted i wywołanie OnFaulted(), który wywołuje zdarzenie Faulted. Jeśli OnFaulted zgłasza wyjątek jest zgłoszony ponownie.  
  
### <a name="throwifxxx-methods"></a>Metody ThrowIfXxx  
 CommunicationObject ma trzy metody chronione, które mogą służyć do zgłaszają wyjątki, jeśli obiekt jest w określonym stanie.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A>zgłasza wyjątek, jeśli stan jest zamknięcia, zamknięte lub Faulted.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A>zgłasza wyjątek, jeśli stan nie został utworzony.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A>zgłasza wyjątek, jeśli stan nie jest otwarty.  
  
 Wyjątki generowane są zależne od stanu. W poniższej tabeli przedstawiono różne stany i odpowiedniego typu wyjątek zgłoszony przez wywołanie metody ThrowIfXxx, która zgłasza wyjątek w tym stanie.  
  
|Stan|Została wywołana przerwania?|Wyjątek|  
|-----------|----------------------------|---------------|  
|Utworzono|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otwieranie|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otwarte|Brak|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Zamykanie|Tak|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Zamykanie|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Zamknięte|Tak|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>w przypadku, że obiekt został zamknięty przez jawne i poprzednie wywołanie przerwania. Jeśli wywołać zamknięcia obiektu, a następnie <xref:System.ObjectDisposedException?displayProperty=nameWithType> jest generowany.|  
|Zamknięte|Nie|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Wystąpił błąd|Brak|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Limity czasu  
 Podjąć kilka metod, które Rozmawialiśmy parametry limitu czasu. Są to zamknij i Otwórz (niektórych przeciążenia i wersje asynchroniczne), OnClose zdarzenia. Te metody są zaprojektowane z myślą długich operacji (na przykład blokowania na wejścia/wyjścia podczas bezpiecznie zamknąć połączenie), parametr limitu czasu wskazuje, jak długo takich operacji może zająć przed zostanie przerwane. Implementacje dowolnej z tych metod należy używać wartość limitu czasu dostarczony do upewnij się, że zwraca do obiektu wywołującego w ramach tego limitu czasu. Implementacje innych metod, które nie przyjmują przekroczenie limitu czasu nie są przeznaczone dla operacji długie i nie powinny blokować na wejścia/wyjścia.  
  
 Wyjątkiem są przeciążenia metody Open() i Close(), które nie przyjmują przekroczenie limitu czasu. Te użyć domyślnej wartości limitu czasu dostarczonych przez klasy pochodnej. <xref:System.ServiceModel.Channels.CommunicationObject>udostępnia dwa chronione właściwości abstrakcyjne o nazwie <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> i <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> zdefiniowany jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Klasa pochodna implementuje te właściwości, aby podać domyślny limit czasu dla przeciążenia metody Open() i Close(), które nie przyjmują wartości limitu czasu. Następnie implementacje metody Open() i Close() delegować do przeciążenia, które przyjmuje przekazanie jej przez domyślną wartość limitu czasu, na przykład limit czasu:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Ten interfejs ma czterech właściwości tylko do odczytu do prezentowania domyślnej wartości limitu czasu dla otworzyć, wysyłania, odbierania i zamknij. Każda implementacja jest odpowiedzialny za uzyskiwanie wartości domyślne w jakikolwiek sposób odpowiednie. Dla wygody <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase> domyślne te wartości na 1 minutę.
