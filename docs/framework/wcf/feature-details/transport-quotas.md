---
title: Przydziały dla transportu
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: fca5fbeffb560f848edda6421301785f02547d2c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585704"
---
# <a name="transport-quotas"></a>Przydziały dla transportu
Przydziały transportu to mechanizm zasad służący do decydowania, kiedy połączenie zużywa nadmierne zasoby. Przydział jest stałym limitem, który uniemożliwia korzystanie z dodatkowych zasobów po przekroczeniu wartości limitu przydziału. Przydziały transportowe uniemożliwiają złośliwe lub przypadkowe ataki typu "odmowa usługi".  
  
 Windows Communication Foundation (WCF) transporty mają domyślne wartości przydziału, które opierają się na rozdysponowaniu zasobów. Te wartości domyślne są odpowiednie dla środowisk deweloperskich i małych scenariuszy instalacji. Administratorzy usługi powinni przejrzeć przydziały transportu i dostosować poszczególne wartości przydziału w przypadku braku zasobów w ramach instalacji lub jeśli ograniczenia są ograniczone, pomimo dostępności dodatkowych zasobów.  
  
## <a name="types-of-transport-quotas"></a>Typy przydziałów transportu  
 Transporty WCF mają trzy typy przydziałów:  
  
- *Limity czasu* zmniejszają ryzyko ataków typu "odmowa usługi", które opierają się na zasobach przez dłuższy czas.  
  
- *Limity alokacji pamięci* uniemożliwiają pojedyncze połączenie z wyczerpania pamięci systemowej i odmowa usługi do innych połączeń.  
  
- *Limity rozmiaru kolekcji* odnoszą się do użycia zasobów, które bezpośrednio przydzielą pamięć lub są ograniczone.  
  
## <a name="transport-quota-descriptions"></a>Opisy przydziału transportowego  
 W tej sekcji opisano przydziały transportu dostępne dla standardowych transportów WCF: HTTP (S), TCP/IP i nazwane potoki. Niestandardowe transporty mogą uwidaczniać własne konfigurowalne przydziały, które nie znajdują się na tej liście. Zapoznaj się z dokumentacją dotyczącą niestandardowego transportu, aby dowiedzieć się więcej o jego przydziałach.  
  
 Każde ustawienie przydziału ma typ, wartość minimalną i wartość domyślną. Maksymalna wartość limitu przydziału jest ograniczona przez jego typ. Ze względu na ograniczenia komputera nie zawsze jest możliwe ustawienie limitu przydziału na wartość maksymalną.  
  
|Nazwa|Typ|Długości.<br /><br /> value|Domyślne<br /><br /> value|Opis|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|przedział_czasu|1 takt|5 sekund|Maksymalny czas oczekiwania na połączenie w celu wysłania preambuły podczas początkowego odczytu. Te dane są odbierane przed zauwierzytelnianiem. To ustawienie jest zwykle znacznie mniejsze niż `ReceiveTimeout` wartość limitu przydziału.|  
|`CloseTimeout`|przedział_czasu|0|1 min|Maksymalny czas oczekiwania na połączenie, zanim transport zgłosi wyjątek.|  
|`ConnectionBufferSize`|Integer|1|8 KB|Rozmiar (w bajtach) buforów przesyłania i odbioru źródłowego transportu. Zwiększenie rozmiaru buforu może zwiększyć przepływność podczas wysyłania dużych komunikatów.|  
|`IdleTimeout`|przedział_czasu|0|2 min|Maksymalny czas, przez jaki połączenie w puli może pozostawać bezczynne przed zamknięciem.<br /><br /> To ustawienie dotyczy tylko połączeń obsługiwanych przez pule.|  
|`LeaseTimeout`|przedział_czasu|0|5 min|Maksymalny okres istnienia aktywnego połączenia w puli. Po upływie określonego czasu połączenie zostanie zamknięte, gdy bieżące żądanie zostanie serwisowane.<br /><br /> To ustawienie dotyczy tylko połączeń obsługiwanych przez pule.|  
|`ListenBacklog`|Integer|1|10|Maksymalna liczba połączeń, które odbiornik może być nieserwisowany przed odmową dodatkowych połączeń z tym punktem końcowym.|  
|`MaxBufferPoolSize`|Długo|0|512 KB|Maksymalna pamięć (w bajtach), przez którą transportuje buforowanie buforów komunikatów wielokrotnego użytku. Gdy pula nie może dostarczyć buforu komunikatów, nowy bufor jest przypisywany do tymczasowego użytku.<br /><br /> Instalacje tworzące wiele fabryk kanałów lub odbiorników mogą przydzielić duże ilości pamięci dla pul buforów. Zmniejszenie rozmiaru buforu może znacznie zmniejszyć użycie pamięci w tym scenariuszu.|  
|`MaxBufferSize`|Integer|1|64 KB|Maksymalny rozmiar buforu używany do przesyłania strumieniowego w bajtach. Jeśli ten przydział transportu nie jest ustawiony lub transport nie używa przesyłania strumieniowego, wartość przydziału jest taka sama jak mniejsza `MaxReceivedMessageSize` wartość przydziału i <xref:System.Int32.MaxValue> .|  
|`MaxOutboundConnectionsPerEndpoint`|Integer|1|10|Maksymalna liczba połączeń wychodzących, które mogą być skojarzone z określonym punktem końcowym.<br /><br /> To ustawienie dotyczy tylko połączeń obsługiwanych przez pule.|  
|`MaxOutputDelay`|przedział_czasu|0|200 MS|Maksymalny czas oczekiwania po wykonaniu operacji wysyłania wsadowych dodatkowych komunikatów w ramach jednej operacji. Komunikaty są wysyłane wcześniej, jeśli bufor podstawowego transportu zostanie zapełniony. Wysyłanie dodatkowych komunikatów nie powoduje zresetowania okresu opóźnienia.|  
|`MaxPendingAccepts`|Integer|1|1|Maksymalna liczba zaakceptowanych kanałów, które odbiornik może oczekiwać.<br /><br /> Istnieje odstęp czasu między ukończeniem zaakceptowania a rozpoczęciem nowego akceptacji. Zwiększenie rozmiaru kolekcji może uniemożliwić porzucenie klientów łączących się w tym interwale.|  
|`MaxPendingConnections`|Integer|1|10|Maksymalna liczba połączeń, które odbiornik może oczekiwać na akceptację przez aplikację. Po przekroczeniu tej wartości przydziału nowe połączenia przychodzące są usuwane, a nie czekają na ich zaakceptowanie.<br /><br /> Funkcje połączeń, takie jak zabezpieczenia komunikatów, mogą spowodować otwarcie więcej niż jednego połączenia przez klienta. Administratorzy usługi powinni uwzględnić te dodatkowe połączenia podczas ustawiania wartości tego przydziału.|  
|`MaxReceivedMessageSize`|Długo|1|64 KB|Maksymalny rozmiar (w bajtach) odebranej wiadomości, łącznie z nagłówkami, zanim transport zgłosi wyjątek.|  
|`OpenTimeout`|przedział_czasu|0|1 min|Maksymalny czas oczekiwania na połączenie, zanim transport zgłosi wyjątek.|  
|`ReceiveTimeout`|przedział_czasu|0|10 min|Maksymalny czas oczekiwania na zakończenie operacji odczytu, zanim transport zgłosi wyjątek.|  
|`SendTimeout`|Zakres czasu|0|1 min|Maksymalny czas oczekiwania na zakończenie operacji zapisu, zanim transport zgłosi wyjątek.|  
  
 Przydziały transportu `MaxPendingConnections` i `MaxOutboundConnectionsPerEndpoint` są łączone w jeden przydział transportu wywoływany w `MaxConnections` przypadku ustawienia przez powiązanie lub konfigurację. Tylko element Binding służy do ustawiania tych wartości przydziału osobno. `MaxConnections`Przydział transportu ma takie same wartości minimalne i domyślne.  
  
## <a name="setting-transport-quotas"></a>Ustawianie przydziałów transportu  
 Przydziały transportu są ustawiane za pomocą elementu powiązania transportu, powiązania transportowego, konfiguracji aplikacji lub zasad hosta. Ten dokument nie obejmuje ustawiania transportów za poorednictwem zasad hosta. Zapoznaj się z dokumentacją podstawowego transportu, aby odnaleźć ustawienia przydziałów zasad hosta. W temacie [Konfigurowanie protokołu HTTP i https](configuring-http-and-https.md) opisano ustawienia przydziału dla sterownika HTTP. sys. Aby uzyskać więcej informacji o konfigurowaniu limitów systemu Windows dla połączeń HTTP, TCP/IP i nazwanych potoków, Wyszukaj w bazie wiedzy Microsoft Knowledge Base.  
  
 Inne typy przydziałów stosuje się pośrednio do transportów. Koder komunikatów, którego używa transport do przekształcania wiadomości na bajty, może mieć własne ustawienia przydziału. Jednak te przydziały są niezależne od używanego typu transportu.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Kontrolowanie przydziałów transportu z elementu powiązania  
 Ustawienie przydziałów transportu za pomocą elementu powiązania zapewnia największą elastyczność kontroli nad zachowaniem transportu. Domyślne limity czasu dla operacji zamykania, otwierania, odbierania i wysyłania są pobierane z powiązania w przypadku skompilowania kanału.  
  
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
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Kontrolowanie przydziałów transportu z powiązania  
 Ustawienie przydziałów transportu za pośrednictwem powiązania oferuje uproszczony zestaw przydziałów do wyboru, pozostawiając jednocześnie dostęp do najbardziej typowych wartości przydziału.  
  
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
  
1. `MaxBufferSize`Przydział transportu jest dostępny tylko dla `BasicHttp` powiązania. `WSHttp`Powiązania są przeznaczone dla scenariuszy, które nie obsługują trybów transportowych przesyłanych strumieniowo.  
  
2. Przydziały transportu `MaxPendingConnections` i `MaxOutboundConnectionsPerEndpoint` są łączone w pojedynczy przydział transportu o nazwie `MaxConnections` .  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Kontrolowanie przydziałów transportu z konfiguracji  
 Konfiguracja aplikacji może ustawiać te same przydziały transportu co bezpośredni dostęp do właściwości w powiązaniu. W obszarze pliki konfiguracji nazwa przydziału transportu zawsze zaczyna się od małej litery. Na przykład `CloseTimeout` właściwość powiązania odpowiada `closeTimeout` ustawieniu w obszarze Konfiguracja i `MaxConnections` właściwość powiązania odpowiada `maxConnections` ustawieniu w obszarze Konfiguracja.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
