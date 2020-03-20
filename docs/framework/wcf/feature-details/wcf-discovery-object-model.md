---
title: Model obiektów odnajdywania WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: debcb08802894a34e16d9aa65bbbb1b0282794f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184224"
---
# <a name="wcf-discovery-object-model"></a>Model obiektów odnajdywania WCF
Odnajdowanie WCF składa się z zestawu typów, które zapewniają ujednolicony model programowania, który umożliwia pisanie usług, które są wykrywalne w czasie wykonywania i klientów, którzy znajdują i korzystają z tych usług.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Tworzenie usług wykrywalnych i znajdowania usług  
 Aby usługa WCF wykrywalne, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> dodać <xref:System.ServiceModel.Description.ServiceDescription> do hosta usługi i dodać punkt końcowy odnajdywania. Jeśli usługa jest skonfigurowana do wysyłania <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>komunikatów anonsu (przez dodanie) anons jest wysyłany po otwarciu i zamknięciu hosta usługi.  
  
 Klient, który chce nasłuchiwać komunikatów anonsu usługi hostuje usługę anonsowania i dodaje jeden lub więcej punktów końcowych anonsu. Usługa anonsu odbiera komunikaty anonsu i wywołuje zdarzenia anonsu.  
  
 Klient używa klasy <xref:System.ServiceModel.Discovery.DiscoveryClient> do wyszukiwania dostępnych usług. Aplikacja kliencka wystąpienia <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, przekazywanie w punkcie końcowym odnajdywania, który określa, gdzie wysłać komunikaty odnajdywania. Klient wywołuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodę, która `Probe` wysyła żądanie. Usługi nasłuchiwania `Probe` komunikatów odnajdywania odbierają to żądanie. Jeśli usługa spełnia kryteria określone `Probe`w , `ProbeMatch` wysyła komunikat z powrotem do klienta.  
  
## <a name="object-model"></a>Model obiektu  
 Interfejs API odnajdywania WCF definiuje następujące klasy:  
  
- <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
- <xref:System.ServiceModel.Discovery.FindCriteria>  
  
- <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
- <xref:System.ServiceModel.Discovery.FindResponse>  
  
- <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
- <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>Announcementclient  
 Klasa <xref:System.ServiceModel.Discovery.AnnouncementClient> zapewnia synchroniczne i asynchroniczne metody wysyłania komunikatów anonsu. Istnieją dwa typy komunikatów anonsowych, Hello i Bye. Komunikat Hello jest wysyłany w celu wskazania, że usługa stała się dostępna i bye komunikat jest wysyłany, aby wskazać, że istniejąca usługa stała się niedostępna. Deweloper tworzy <xref:System.ServiceModel.Discovery.AnnouncementClient> wystąpienie, przekazując <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> wystąpienie jako parametr konstruktora.  
  
## <a name="announcementendpoint"></a>Announcementendpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>reprezentuje standardowy punkt końcowy z umową o stałej anonsie. Jest on używany przez usługę lub klienta do wysyłania i odbierania komunikatów anonsowych. Domyślnie klasa <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> jest ustawiona na użycie WS_Discovery wersji protokołu 11.  
  
## <a name="announcementservice"></a>Announcementservice  
 <xref:System.ServiceModel.Discovery.AnnouncementService>to implementacja usługi anonsu świadczona przez system, która odbiera i przetwarza komunikaty anonsów. Po odebraniu komunikatu Hello <xref:System.ServiceModel.Discovery.AnnouncementService> lub Bye wystąpienie wywołuje odpowiednią metodę wirtualną <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> lub <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, która wywołuje zdarzenia anonsu.  
  
## <a name="discoveryclient"></a>Discoveryclient  
 Klasa <xref:System.ServiceModel.Discovery.DiscoveryClient> jest używana przez aplikację kliencką do znajdowania i rozpoznawania dostępnych usług. Zapewnia synchroniczne i asynchroniczne metody znajdowania i rozwiązywania usług na podstawie określonych <xref:System.ServiceModel.Discovery.FindCriteria> i <xref:System.ServiceModel.Discovery.ResolveCriteria> odpowiednio. Deweloper tworzy <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienie i zapewnia <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienie jako parametr konstruktora.  
  
 Aby znaleźć usługę, deweloper wywołuje metodę synchroniową lub `Find` asynchroniką, która zapewnia <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, które zawiera kryteria wyszukiwania do użycia. Tworzy <xref:System.ServiceModel.Discovery.DiscoveryClient> `Probe` komunikat z odpowiednimi nagłówkami i wysyła żądanie znalezienia. Ponieważ może istnieć więcej `Find` niż jedno zaległe żądanie w dowolnym momencie, klient koreluje odebrane odpowiedzi i sprawdza poprawność odpowiedzi. Następnie dostarcza wyniki do wywołującego `Find` operacji za <xref:System.ServiceModel.Discovery.FindResponse>pomocą .  
  
 Aby rozwiązać znaną usługę, deweloper wywołuje metodę synchroniową `Resolve` lub asynchroniką, która zapewnia wystąpienie, <xref:System.ServiceModel.Discovery.ResolveCriteria> które zawiera <xref:System.ServiceModel.EndpointAddress> znaną usługę. Tworzy <xref:System.ServiceModel.Discovery.DiscoveryClient> `Resolve` komunikat z odpowiednimi nagłówkami i wysyła żądanie rozwiązania. Odebrana odpowiedź jest skorelowana z żądaniami rozwiązania nierozstrzygnięte, a wynik jest dostarczany do wywołującego `Resolve` operacji przy użyciu <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Jeśli serwer proxy odnajdywania jest obecny w sieci, a żądanie <xref:System.ServiceModel.Discovery.DiscoveryClient> odnajdywania w sposób multiemisji, serwer proxy odnajdywania może odpowiedzieć komunikatem hello tłumienia multiemisji. Wywołuje <xref:System.ServiceModel.Discovery.DiscoveryClient> zdarzenie, `ProxyAvailable` gdy odbiera Hello wiadomości w `Find` `Resolve` odpowiedzi na nierozstrzygnięte lub żądania. Zdarzenie `ProxyAvailable` zawiera <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> informacje o serwerze proxy odnajdywania. To do dewelopera, aby użyć tych informacji, aby przełączyć się z trybu ad hoc do trybu zarządzanego.  
  
## <a name="discoveryendpoint"></a>Discoveryendpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>reprezentuje standardowy punkt końcowy ze umową odnajdywania stałego. Jest on używany przez usługę lub klienta do wysyłania lub odbierania komunikatów odnajdywania. Domyślnie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jest ustawiona <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> na tryb użycia i wersja WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>Discoverymessagesequencegenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>służy do generowania, <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> gdy usługa wysyła komunikaty odnajdywania lub anonsu.  
  
## <a name="discoveryservice"></a>Discoveryservice  
 Klasa <xref:System.ServiceModel.Discovery.DiscoveryService> abstrakcyjna zapewnia platformę do `Probe` `Resolve` odbierania i przetwarzania i wiadomości. Po `Probe` odebraniu <xref:System.ServiceModel.Discovery.DiscoveryService> wiadomości tworzy <xref:System.ServiceModel.Discovery.FindRequestContext> wystąpienie oparte na wiadomości <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> przychodzącej i wywołuje metodę wirtualną. Po `Resolve` odebraniu <xref:System.ServiceModel.Discovery.DiscoveryService> wiadomości wywołuje <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> metodę wirtualną. Można dziedziczyć z tej klasy, aby zapewnić implementację usługi odnajdywania niestandardowe.  
  
## <a name="discoveryproxy"></a>Discoveryproxy  
 Klasa <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstrakcyjna zapewnia platformę do odbierania i przetwarzania komunikatów odnajdywania i anonsów. Dziedziczysz z tej klasy podczas implementowania niestandardowego serwera proxy odnajdywania. Gdy `Probe` wiadomość jest odbierana za <xref:System.ServiceModel.Discovery.DiscoveryProxy> daniem `BeginShouldRedirectFind` multiemisji, klasa wywołuje metodę wirtualną, aby ustalić, czy komunikat tłumienia multiemisji powinien zostać wysłany. Jeśli deweloper zdecyduje się nie wysyłać komunikat tłumienia multiemisji lub jeśli `Probe` wiadomość została <xref:System.ServiceModel.Discovery.FindRequestContext> odebrana za ą emisję pojedynczą, tworzy wystąpienie klasy na podstawie wiadomości przychodzącej i wywołuje metodę wirtualną. `OnBeginFind` Gdy `Resolve` wiadomość jest odbierana za <xref:System.ServiceModel.Discovery.DiscoveryProxy> ć `ShouldRedirectResolve` multiemisji, Klasa wywołuje metodę wirtualną, aby ustalić, czy komunikat tłumienia multiemisji powinny być wysyłane. Jeśli deweloper zdecyduje się nie wysyłać komunikat tłumienia multiemisji lub jeśli `Resolve` wiadomość została <xref:System.ServiceModel.Discovery.ResolveCriteria> odebrana za ą emisję pojedynczą, tworzy wystąpienie klasy na podstawie wiadomości przychodzącej i wywołuje metodę wirtualną. `OnBeginResolve` Po odebraniu komunikatu Hello <xref:System.ServiceModel.Discovery.DiscoveryProxy> lub Bye`OnBeginOnlineAnnouncement` wywołuje `OnBeingOfflineAnnouncement`odpowiednią metodę wirtualną ( lub ), która wywołuje zdarzenia anonsu.  
  
## <a name="discoveryversion"></a>Discoveryversion  
 Klasa <xref:System.ServiceModel.Discovery.DiscoveryVersion> reprezentuje wersję protokołu odnajdywania do użycia.  
  
## <a name="endpointdiscoverybehavior"></a>Endpointdiscoverybehavior  
 Klasa <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> służy do kontrolowania wykrywalności punktu końcowego, określić rozszerzenia, dodatkowe nazwy typów umowy. i zakresów skojarzonych z tym punktem końcowym. To zachowanie jest dodawane do punktu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>końcowego aplikacji, aby skonfigurować jego . Po <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> dodaniu do hosta usługi wszystkie punkty końcowe aplikacji hostowane przez hosta usługi domyślnie stają się wykrywalne. Deweloper może wyłączyć odnajdowanie dla <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> określonego `false`punktu końcowego, ustawiając właściwość na .  
  
## <a name="endpointdiscoverymetadata"></a>Endpointdiscoverymetadata  
 Klasa <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> zapewnia niezależną od wersji reprezentację punktu końcowego opublikowanego przez usługę. Zawiera adresy punktów końcowych, identyfikatory URI nasłuchiwania, nazwy typów kontraktów, zakresy, wersję metadanych i rozszerzenia określone przez dewelopera usługi. Wysyłane <xref:System.ServiceModel.Discovery.FindCriteria> przez klienta podczas `Probe` operacji jest dopasowywały się do <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Jeśli kryteria są zgodne, a <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> następnie jest zwracany do klienta. Adres punktu końcowego w <xref:System.ServiceModel.Discovery.ResolveCriteria> jest dopasowywał się do adresu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Jeśli kryteria są zgodne, a <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> następnie jest zwracany do klienta.  
  
## <a name="findcriteria"></a>Findcriteria  
 Klasa <xref:System.ServiceModel.Discovery.FindCriteria> jest klasą niezależną od wersji, używaną do określania kryteriów używanych podczas znajdowania usługi. W pełni obsługuje zdefiniowane w u programu WS-Discovery kryteria dopasowywania usług. Ma również rozszerzenia, których deweloperzy mogą używać do określania wartości niestandardowych, które mogą być używane podczas procesu dopasowywania. Deweloper może podać kryteria zakończenia `Find` operacji, określając <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, który określa całkowitą liczbę usług, których deweloper szuka <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>lub który określa , która jest wartością, która określa, jak długo klient czeka na odpowiedzi.  
  
## <a name="findrequestcontext"></a>Kontekst FindRequestContext  
 Klasa <xref:System.ServiceModel.Discovery.FindRequestContext> jest tworzone przez usługę odnajdywania na podstawie komunikatu, `Probe` który otrzymuje, gdy klient inicjuje `Find` operację. Zawiera wystąpienie, <xref:System.ServiceModel.Discovery.FindCriteria> które zostało określone przez klienta.  
  
## <a name="findresponse"></a>ZnajdźOdpowiedzialność  
 Klasa <xref:System.ServiceModel.Discovery.FindResponse> jest zwracana do <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> wywołującego z odpowiedziami `Find` operacji. Jest również obecny <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>w . Zawiera zbiór <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, który jest zbiorem odkrytych punktów końcowych i <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>słownika i .  
  
## <a name="resolvecriteria"></a>Resolvecriteria  
 Klasa <xref:System.ServiceModel.Discovery.ResolveCriteria> jest klasą niezależną od wersji, używaną do określania kryteriów używanych podczas rozpoznawania już znanej usługi. Zawiera adres punktu końcowego znanej usługi. Deweloper może podać kryteria zakończenia dla operacji rozpoznawania, określając <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, który określa, jak długo klient czeka na odpowiedzi.  
  
## <a name="resolveresponse"></a>Rozwiązanie Rozpoznawania  
 Jest <xref:System.ServiceModel.Discovery.ResolveResponse> zwracany do wywołującego <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody z odpowiedzią operacji. `Resolve` Jest również obecny <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>w . Zawiera wystąpienie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, który jest odnalezionych punktów <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>końcowych i wystąpienie .  
  
## <a name="servicediscoverybehavior"></a>Servicediscoverybehavior  
 Klasa <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umożliwia deweloperowi dodać funkcję odnajdywania do usługi. To zachowanie można <xref:System.ServiceModel.ServiceHost>dodać do pliku . Klasa <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> iteruje za punktami końcowymi aplikacji dodane do hosta usługi i tworzy kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> z odnajdowalnych punktów końcowych. Wszystkie punkty końcowe są domyślnie wykrywalne. Wykrywalność określonego punktu końcowego można kontrolować, dodając <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> do tego określonego punktu końcowego. Jeśli punkty końcowe anonsu są dodawane do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> następnie anons wszystkich odnajdowalnych punktów końcowych jest wysyłany za każdy z punktów końcowych anonsu, gdy host usługi jest otwarty lub zamknięty.  
  
## <a name="udpannouncementendpoint"></a>Udpannouncementendpoint  
 Klasa <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jest standardowym punktem końcowym anonsu, który jest wstępnie skonfigurowany do ogłaszania za pociągnięte do wiązania multiemisji UDP. Domyślnie <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jest ustawiona na użycie wersji WS_Discovery WSApril2005.  
  
## <a name="udpdiscoveryendpoint"></a>Udpdiscoveryendpoint  
 Klasa <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> jest standardowym punktem końcowym odnajdywania, który jest wstępnie skonfigurowany do odnajdowania za poczęsknienia multiemisji UDP. Domyślnie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jest ustawiona na używanie wersji i <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> trybu WSDiscovery111 WS-Discovery.
