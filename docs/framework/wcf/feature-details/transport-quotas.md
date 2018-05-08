---
title: Przydziały dla transportu
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: b6322bada88c6aef65b609f43fe92dda8dbab206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transport-quotas"></a>Przydziały dla transportu
Przydziały dla transportu są mechanizm zasad dotyczących decydowania, kiedy korzysta z połączenia nadmiernego zasobów. Limit przydziału jest stały limit, który uniemożliwia użycie dodatkowych zasobów, po przekroczeniu przydziału wartości. Przydziały dla transportu zapobiec złośliwe lub przypadkowe "odmowa usługi".  
  
 Transporty Windows Communication Foundation (WCF) ma domyślne wartości przydziałów, które są oparte na zachowawcze alokacji zasobów. Te wartości domyślne są odpowiednie dla środowisk projektowych oraz instalacji małe scenariusze. Administratorzy usługi przejrzeć przydziały dla transportu i dostrajania poszczególne wartości przydziału, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.  
  
## <a name="types-of-transport-quotas"></a>Typy przydziały dla transportu  
 Transportu WCF są trzy typy przydziałów:  
  
-   *Limity czasu* ograniczyć ataki, które opierają się na zajmowania zasobów przez dłuższy czas.  
  
-   *Limity przydziału pamięci* zapobiec pojedynczego połączenia z wyczerpaniem pamięci systemowej i odmawianie usługę dla innych połączeń.  
  
-   *Limity rozmiaru kolekcji* powiązany zużycie zasobów, które pośrednio przydzielić pamięci lub w ograniczonych zasobach.  
  
## <a name="transport-quota-descriptions"></a>Opisy przydziału transportu  
 W tej sekcji opisano dostępne dla standardowych transportu WCF przydziały dla transportu: HTTP (S), TCP/IP i nazwanych potoków. Transporty niestandardowe mogą uwidaczniać własne można konfigurować przydziały nie ma na tej liście. Zajrzyj do dokumentacji dla niestandardowych transportu dowiedzieć się o jego przydziałów.  
  
 Każde ustawienie limitu przydziału ma typ, wartość minimalna i wartość domyślną. Maksymalna wartość limit przydziału jest ograniczona przez jego typu. Ze względu na ograniczenia maszyny nie zawsze jest możliwe ustawić limit przydziału maksymalnej wartości.  
  
|Nazwa|Typ|Min.<br /><br /> value|Domyślny<br /><br /> value|Opis|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|Zakres czasu|1 znaczników|5 s|Maksymalny czas oczekiwania na połączenie do wysłania preambuły podczas wstępnej Odczyt. Odebrano te dane przed uwierzytelnianie odbywa się. To ustawienie jest zwykle znacznie mniejszy niż `ReceiveTimeout` wartość przydziału.|  
|`CloseTimeout`|Zakres czasu|0|1 min|Maksymalny czas oczekiwania na połączenie zamknąć przed transportu zgłasza wyjątek.|  
|`ConnectionBufferSize`|Liczba całkowita|1|8 KB|Rozmiar w bajtach, wysyłania i odbierania buforów transportu źródłowego. Zwiększanie rozmiaru buforu może zwiększyć przepustowość podczas wysyłania dużych wiadomości.|  
|`IdleTimeout`|Zakres czasu|0|2 minuty|Maksymalny czas połączenia z puli może być bezczynna, zanim zostanie zamknięty.<br /><br /> To ustawienie dotyczy tylko puli połączeń.|  
|`LeaseTimeout`|Zakres czasu|0|5 minut|Maksymalny okres istnienia aktywnego połączenia z puli. Po upływie określonego czasu, gdy bieżące żądanie zostanie obsłużone powoduje zamknięcie połączenia.<br /><br /> To ustawienie dotyczy tylko puli połączeń.|  
|`ListenBacklog`|Liczba całkowita|1|10|Odmówiono maksymalną liczbę połączeń, które mogą mieć unserviced odbiornika przed dodatkowych połączeń do określonego punktu końcowego.|  
|`MaxBufferPoolSize`|długa|0|512 KB|Maksymalna ilość pamięci, w bajtach, które devotes transportu do puli buforów komunikatów wielokrotnego użytku. Gdy puli nie może dostarczyć bufor komunikatów, bufor nowego jest przydzielane tymczasowych.<br /><br /> Urządzenia, które utworzyć wiele fabryk kanałów i odbiorników można przydzielić duże ilości pamięci dla puli bufora. Zmniejsza to rozmiar buforu może znacznie zmniejszyć użycie pamięci w tym scenariuszu.|  
|`MaxBufferSize`|Liczba całkowita|1|64 KB|Maksymalny rozmiar w bajtach buforu, używane do strumieniowego przesyłania danych. Jeśli ten przydział transportu nie jest ustawiona, lub transport nie korzysta z przesyłania strumieniowego, a następnie wartość przydziału jest taka sama jak mniejszy z `MaxReceivedMessageSize` wartość przydziału i <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Liczba całkowita|1|10|Maksymalna liczba połączeń wychodzących, które mogą być powiązane z określonym punktem końcowym.<br /><br /> To ustawienie dotyczy tylko puli połączeń.|  
|`MaxOutputDelay`|Zakres czasu|0|200 ms|Maksymalny czas oczekiwania, po operacji wysyłania dla przetwarzania wsadowego dodatkowych komunikatów w ramach jednej operacji. Komunikaty są wysyłane wcześniej, jeśli bufor transportu źródłowego zostaje zapełniony. Wysyłanie dodatkowych komunikatów nie powoduje resetowania opóźnienie.|  
|`MaxPendingAccepts`|Liczba całkowita|1|1|Maksymalna liczba akceptuje kanałów, że odbiornik może mieć oczekiwania.<br /><br /> Brak odstęp czasu między Kończenie akceptacji i uruchomienie nowej accept. Zwiększanie rozmiaru tej kolekcji może uniemożliwić klienci łączący się w danym przedziale czasu z usuwane.|  
|`MaxPendingConnections`|Liczba całkowita|1|10|Maksymalna liczba połączeń odbiornika może mieć oczekuje na zatwierdzenie przez aplikację. Po przekroczeniu tej wartości limitu przydziału nowych połączeń przychodzących są usuwane, a nie oczekuje na zatwierdzenie.<br /><br /> Połączenie funkcji, takich jak zabezpieczenia wiadomości może spowodować klienta otworzyć więcej niż jedno połączenie. Administratorzy usługi należy uwzględnić te dodatkowe połączenia podczas ustawiania tej wartości limitu przydziału.|  
|`MaxReceivedMessageSize`|długa|1|64 KB|Maksymalny rozmiar w bajtach odebranej wiadomości, włącznie z nagłówkami, zanim transportu zgłasza wyjątek.|  
|`OpenTimeout`|Zakres czasu|0|1 min|Maksymalny czas oczekiwania na połączenie, należy ustanowić przed transportu zgłasza wyjątek.|  
|`ReceiveTimeout`|Zakres czasu|0|10 minut|Maksymalny czas oczekiwania na ukończenie transportu zgłasza wyjątek operacji odczytu.|  
|`SendTimeout`|Zakres czasu|0|1 min|Maksymalny czas oczekiwania na ukończenie transportu zgłasza wyjątek operacji zapisu.|  
  
 Przydziały dla transportu `MaxPendingConnections` i `MaxOutboundConnectionsPerEndpoint` są łączone w pojedynczy transportu przydziału o nazwie `MaxConnections` po ustawieniu za pośrednictwem powiązania lub konfiguracji. Element powiązania umożliwia ustawienie wartości tych zasobów pojedynczo. `MaxConnections` Przydziału transportu ma takie same wartości minimalna i domyślne.  
  
## <a name="setting-transport-quotas"></a>Przydziały dla transportu ustawienie  
 Przydziały dla transportu są ustawiane przez element powiązania transportu powiązania transportu, konfiguracji aplikacji lub zasad hosta. Ten dokument nie obejmuje ustawienia transportu za pośrednictwem zasad hosta. Zajrzyj do dokumentacji dla transportu źródłowego do wykrywania ustawień przydziały zasad hosta. [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) temacie opisano ustawienia limitu przydziału dla sterownika Http.sys. Wyszukiwanie Microsoft Knowledge Base, aby uzyskać więcej informacji o konfigurowaniu limitów systemu Windows na HTTP, TCP/IP i połączenia nazwanego potoku.  
  
 Inne typy przydziałów pośrednio dotyczą transportów. Kodera wiadomości, który używa transportu do przekształcenia wiadomości w bajtach może mieć własne ustawienia limitu przydziału. Jednak te przydziały są niezależne od typu używanego transportu.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Kontrolowanie przydziały dla transportu z elementu powiązania  
 Ustawianie przydziałów transportu za pośrednictwem elementu powiązania zapewnia największą elastyczność w kontrolowanie zachowania transportu. Domyślne limity czasu dla zamknięty, Otwórz, Receive i wysyłać operacje są pobierane z powiązania po utworzeniu kanału.  
  
|Nazwa|HTTP|TCP/IP|Nazwany potok|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||X|X|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||X|X|  
|`IdleTimeout`||X|X|  
|`LeaseTimeout`||X||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|X|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||X|X|  
|`MaxOutputDelay`||X|X|  
|`MaxPendingAccepts`||X|X|  
|`MaxPendingConnections`||X|X|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Kontrolowanie przydziały dla transportu z wiązania  
 Ustawianie przydziałów transportu za pośrednictwem powiązania oferuje uproszczony zestaw przydziałów, które można wybierać podczas nadal zapewniające dostęp do najbardziej typowych wartości limitu przydziału.  
  
|Nazwa|HTTP|TCP/IP|Nazwany potok|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1.  `MaxBufferSize` Przydziału transportu jest dostępna tylko na `BasicHttp` powiązania. `WSHttp` Powiązania znajdują się w scenariuszach, które nie obsługują przesyłanej strumieniowo transportu.  
  
2.  Przydziały dla transportu `MaxPendingConnections` i `MaxOutboundConnectionsPerEndpoint` są łączone w pojedynczy transportu przydziału o nazwie `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Kontrolowanie przydziały dla transportu z konfiguracji  
 Konfiguracja aplikacji można ustawić tej samej przydziały dla transportu jako bezpośredni dostęp do właściwości dla wiązania. W plikach konfiguracji nazwę przydziału transportu zawsze rozpoczyna się od małej litery. Na przykład `CloseTimeout` odpowiada właściwości powiązania `closeTimeout` ustawieniu konfiguracji i `MaxConnections` odpowiada właściwości powiązania `maxConnections` ustawieniu konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
