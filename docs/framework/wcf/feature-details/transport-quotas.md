---
title: Przydziały dla transportu
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: 44bda0838689fcf8096017060be970f2291a86e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174632"
---
# <a name="transport-quotas"></a>Przydziały dla transportu
Przydziały dla transportu to mechanizm zasad dotyczących decydowania, gdy połączenie jest korzystanie z zasobów. Przydział to stały limit, który uniemożliwia korzystanie z dodatkowych zasobów, po przekroczeniu wartości limitu przydziału. Przydziały dla transportu uniemożliwia złośliwym lub przypadkowe atakom typu odmowa usługi.  
  
 Transporty Windows Communication Foundation (WCF) mają limit przydziału przypisane wartości domyślne, które są oparte na zachowawcze alokacji zasobów. Te wartości domyślne są odpowiednie dla środowisk projektowych oraz instalacji małe scenariusze. Administratorzy usług należy przejrzeć przydziały dla transportu i dostosowywanie wartości poszczególnych zasobów, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.  
  
## <a name="types-of-transport-quotas"></a>Typy przydziały dla transportu  
 Transporty WCF są trzy typy przydziałów:  
  
-   *Limity czasu* eliminowanie atakom typu odmowa usługi, które zależą od zajmowania zasobów przez dłuższy czas.  
  
-   *Limity przydziału pamięci* zapobiec jednego połączenia z wyczerpaniem pamięci systemowej i odmawianie usługi do innych połączeń.  
  
-   *Limity rozmiaru kolekcji* powiązany zużycie zasobów, które pośrednio przydzielić pamięci lub w ograniczoną.  
  
## <a name="transport-quota-descriptions"></a>Opisy przydziału transportu  
 W tej sekcji opisano przydziały dla transportu dostępnych dla standardowego transportu WCF: HTTP (S), protokół TCP/IP i nazwanych potoków. Transporty niestandardowe mogą uwidocznić swoje własne konfigurowalne przydziały nie są uwzględnione na tej liście. Zapoznaj się z dokumentacją dla niestandardowych transportu dowiedzieć się o swoje limity przydziału.  
  
 Każde ustawienie limitu przydziału ma typ, wartość minimalna i wartość domyślną. Maksymalna wartość przydziału jest ograniczona przez jego typu. Ze względu na ograniczenia maszyny nie zawsze jest możliwość ustawiania przydziału do jego wartości maksymalnej.  
  
|Nazwa|Typ|Min.<br /><br /> value|Domyślny<br /><br /> value|Opis|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 znaczników|5 s|Maksymalny czas oczekiwania na połączenie do wysłania Preambuła podczas początkowego Odczyt. Odebrano te dane przed uwierzytelnianie odbywa się. To ustawienie jest zwykle znacznie mniejszy niż `ReceiveTimeout` wartości limitu przydziału.|  
|`CloseTimeout`|TimeSpan|0|1 min|Maksymalny czas oczekiwania na połączenie zamknąć przed transportu zgłasza wyjątek.|  
|`ConnectionBufferSize`|Liczba całkowita|1|8 KB|Rozmiar w bajtach, wysyłania i odbierania buforów transportu źródłowego. Zwiększenie rozmiaru buforu może zwiększyć przepływność, podczas wysyłania dużych komunikatów.|  
|`IdleTimeout`|TimeSpan|0|2 min|Maksymalny czas tego połączenie może pozostawać bezczynne, zanim zamykane.<br /><br /> To ustawienie dotyczy tylko puli połączeń.|  
|`LeaseTimeout`|TimeSpan|0|5 min|Maksymalny okres istnienia puli aktywne połączenie. Po upływie określonego czasu, połączenie zostaje zamknięte, gdy bieżące żądanie zostanie obsłużone.<br /><br /> To ustawienie dotyczy tylko puli połączeń.|  
|`ListenBacklog`|Liczba całkowita|1|10|Maksymalna liczba połączeń, które mogą mieć unserviced odbiornik przed dodatkowych połączeń do tego punktu końcowego są odrzucane.|  
|`MaxBufferPoolSize`|Długie|0|512 KB|Maksymalna ilość pamięci, w bajtach, które transportu devotes do puli buforów komunikatów wielokrotnego użytku. Gdy pula nie może dostarczyć buforu komunikatu, bufor nowego jest przydzielany do tymczasowego użytku.<br /><br /> Instalacje, utworzyć wiele fabryki kanałów i odbiorników, które można przydzielić dużej ilości pamięci dla puli buforów. Ograniczenie to rozmiar buforu może znacznie zmniejszyć użycie pamięci w tym scenariuszu.|  
|`MaxBufferSize`|Liczba całkowita|1|64 KB|Maksymalny rozmiar w bajtach bufora używany dla danych przesyłanych strumieniowo. Jeśli ten limit przydziału transportu nie jest ustawiona, lub transportu nie korzysta z przesyłania strumieniowego, a następnie wartość limitu przydziału jest taka sama jak mniejszego z `MaxReceivedMessageSize` wartości limitu przydziału i <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Liczba całkowita|1|10|Maksymalna liczba połączeń wychodzących, które mogą być powiązane z określonym punktem końcowym.<br /><br /> To ustawienie dotyczy tylko puli połączeń.|  
|`MaxOutputDelay`|TimeSpan|0|200 ms|Maksymalny czas oczekiwania po zakończeniu operacji wysyłania dla przetwarzania wsadowego dodatkowe komunikaty w ramach jednej operacji. Komunikaty są wysyłane wcześniej, jeśli bufor transportu źródłowego zostaje zapełniony. Wysyłanie dodatkowych komunikatów nie powoduje resetowania opóźnienie.|  
|`MaxPendingAccepts`|Liczba całkowita|1|1|Maksymalna liczba akceptuje kanałów, że odbiornik może mieć oczekiwania.<br /><br /> Brak interwału czasu między Kończenie Akceptuj i uruchamianie nowego accept. Zwiększenie rozmiaru tej kolekcji może uniemożliwić klientów łączących się w danym przedziale czasu z porzucana.|  
|`MaxPendingConnections`|Liczba całkowita|1|10|Maksymalna liczba połączeń, które mogą mieć odbiornika, oczekuje na zatwierdzenie przez aplikację. Po przekroczeniu tej wartości limitu przydziału na nowe połączenia przychodzące są odrzucane zamiast oczekuje na zatwierdzenie.<br /><br /> Połączenie funkcji, takich jak zabezpieczenia komunikatów może spowodować klienta otworzyć więcej niż jedno połączenie. Administratorzy usługi należy uwzględnić w przypadku tych dodatkowych połączeń, podczas ustawiania tej wartości limitu przydziału.|  
|`MaxReceivedMessageSize`|Długie|1|64 KB|Maksymalny rozmiar w bajtach odebranego komunikatu, włącznie z nagłówkami, zanim transportu zgłasza wyjątek.|  
|`OpenTimeout`|TimeSpan|0|1 min|Maksymalny czas oczekiwania na połączenie nawiązane przed transportu zgłasza wyjątek.|  
|`ReceiveTimeout`|TimeSpan|0|10 min|Maksymalny czas oczekiwania dla operacji odczytu, które należy wykonać przed transportu zgłasza wyjątek.|  
|`SendTimeout`|Przedział czasu|0|1 min|Maksymalny czas oczekiwania dla operacji zapisu, które należy wykonać przed transportu zgłasza wyjątek.|  
  
 Przydziały dla transportu `MaxPendingConnections` i `MaxOutboundConnectionsPerEndpoint` są łączone w pojedynczy transportu przydziału o nazwie `MaxConnections` po ustawieniu za pośrednictwem powiązania lub konfiguracji. Tylko element powiązania umożliwia ustawienie te wartości limitu przydziału oddzielnie. `MaxConnections` Transportu limit przydziału ma takie same wartości minimalnych i domyślnych.  
  
## <a name="setting-transport-quotas"></a>Ustawienie przydziały dla transportu  
 Przydziały dla transportu są ustawiane za pośrednictwem elementu powiązania transportu powiązania transportu, konfiguracji aplikacji lub zasad hosta. Ten dokument nie obejmuje ustawienia transportu za pomocą zasad hosta. Zapoznaj się z dokumentacją dla transportu źródłowego do wykrywania ustawień przydziałów zasad hosta. [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) temacie opisano ustawienia limitu przydziału dla sterownik Http.sys. Wyszukaj Microsoft Knowledge Base, aby uzyskać więcej informacji o konfigurowaniu limitów Windows dla protokołu HTTP, TCP/IP i połączenia nazwanego potoku.  
  
 Inne rodzaje przydziały dotyczą pośrednio transportów. Koder komunikatów, który używa transportu w celu przekształcenia wiadomości w bajtach może mieć własne ustawienia limitu przydziału. Jednak te przydziały dotyczą niezależna od typu transportu używane.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Kontrolowanie przydziały dla transportu z elementu powiązania  
 Ustawienie przydziały dla transportu za pomocą elementu powiązania oferuje największą elastyczność w kontrolowaniu zachowanie transportu. Limity czasu domyślnego dla Zamknij, Otwórz, Receive i wysłać operacje są pobierane z powiązania, po utworzeniu kanału.  
  
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
 Ustawienie przydziały dla transportu za pośrednictwem powiązania oferuje uproszczony zestaw przydziały mogą wybierać nadal zapewniając dostęp do najbardziej typowych wartości limitu przydziału.  
  
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
  
1.  `MaxBufferSize` Przydziału transportu jest dostępna tylko na `BasicHttp` powiązania. `WSHttp` Powiązania są dla scenariuszy, które nie obsługują przesyłane strumieniowo transportu.  
  
2.  Przydziały dla transportu `MaxPendingConnections` i `MaxOutboundConnectionsPerEndpoint` są łączone w pojedynczy transportu przydziału o nazwie `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Kontrolowanie przydziały dla transportu z konfiguracji  
 Konfiguracja aplikacji można ustawić tej samej przydziały dla transportu jako bezpośredni dostęp do właściwości w powiązaniu. W plikach konfiguracyjnych Nazwa przydziału transportu zawsze rozpoczyna się od małej litery. Na przykład `CloseTimeout` właściwość w powiązaniu odpowiada `closeTimeout` ustawieniu konfiguracji i `MaxConnections` właściwość w powiązaniu odpowiada `maxConnections` ustawieniu konfiguracji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
