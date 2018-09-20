---
title: Model obiektów odnajdywania WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: b337eda40fc70a6d0e7b3aeccfc125e6e6bacf8f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324130"
---
# <a name="wcf-discovery-object-model"></a>Model obiektów odnajdywania WCF
Odnajdywanie w programie WCF składa się zestaw typów, które udostępniają jednolity model programowania, który pozwala na zapis usług, które są wykrywalni środowiska uruchomieniowego i klienci, w których odnaleźć i korzystać z tych usług.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Usługa stała się wykrywalna i usługi wyszukiwania  
 Aby stał się wykrywalny usługi WCF, należy dodać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> do <xref:System.ServiceModel.Description.ServiceDescription> usługi hosta i Dodaj punkt końcowy odnajdywania. Jeśli usługa jest skonfigurowana do wysyłania komunikatów Anons (przez dodanie <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) etapem jest wysyłana, gdy host usług to otwarte i zamknięte.  
  
 Klient, który będzie nasłuchiwać komunikatów Anons usługi obsługuje usługi anonsu i dodaje co najmniej jeden anons punktów końcowych. Usługa ogłoszenie odbiera komunikaty anonsów i wywołuje zdarzenia anonsu.  
  
 Klient używa <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, aby wyszukać dostępne usługi. Tworzy wystąpienie aplikacji klienckiej <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, przekazując punkt końcowy odnajdywania, która określa, gdzie wysyłać komunikaty odnajdywania. Wywołania klienta <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody, która wysyła `Probe` żądania. Nasłuchiwanie do odbierania komunikatów odnajdywania, to usługi `Probe` żądania. Jeśli usługa spełnia kryteria określone we `Probe`, wysyła `ProbeMatch` wiadomość do klienta.  
  
## <a name="object-model"></a>Model obiektów  
 Interfejs API odnajdywania WCF definiuje następujące klasy:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
 
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> Klasa udostępnia synchroniczne i asynchroniczne metody do wysyłania wiadomości anonsów. Istnieją dwa typy komunikatów Anons, Hello i Bye. Wiadomości powitania są wysyłane do wskazywać, że usługa stała się dostępna i komunikat Bye jest wysyłany do wskazania, że istniejąca usługa stała się niedostępna. Deweloper tworzy <xref:System.ServiceModel.Discovery.AnnouncementClient> wypadku przekazanie wystąpienia <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> jako parametr konstruktora.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> reprezentuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Używane przez usługę lub klienta do wysyłania i odbierania wiadomości anonsów. Domyślnie <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> klasy jest skonfigurowany do używania protokołu w wersji WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> jest dostarczane przez system implementacji usługi anons, która odbiera i przetwarza komunikaty anonsów. Po odebraniu wiadomości powitania lub Bye <xref:System.ServiceModel.Discovery.AnnouncementService> wystąpienia, wywołuje odpowiednią metodę wirtualną <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> lub <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, która wywołuje zdarzenia anonsu.  
  
## <a name="discoveryclient"></a>Klasa DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Klasa jest używana przez aplikację kliencką do znajdowaniem i usuwaniem dostępne usługi. Udostępnia synchroniczne i asynchroniczne metody do znajdowania i rozwiązywania usług w oparciu o określonym <xref:System.ServiceModel.Discovery.FindCriteria> i <xref:System.ServiceModel.Discovery.ResolveCriteria> odpowiednio. Deweloper tworzy <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienia i udostępnia wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jako parametr konstruktora.  
  
 Aby znaleźć usługę, deweloper wywołuje synchroniczna lub asynchroniczna `Find` metody, która zapewnia <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia, które zawiera kryteria wyszukiwania, aby użyć. <xref:System.ServiceModel.Discovery.DiscoveryClient> Tworzy `Probe` wiadomości przy użyciu odpowiednich nagłówków i wysyła żądanie wyszukiwania. Ponieważ może istnieć więcej niż jeden oczekujących `Find` żądania w dowolnym momencie, klient jest skorelowane odebrano odpowiedzi i weryfikuje odpowiedzi. Następnie dostarcza wyniki do obiektu wywołującego `Find` przy użyciu operacji <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Aby rozwiązać znane usługi, deweloper wywołuje synchroniczna lub asynchroniczna `Resolve` metodę, która udostępnia wystąpienia <xref:System.ServiceModel.Discovery.ResolveCriteria> zawierający <xref:System.ServiceModel.EndpointAddress> znane usługi. <xref:System.ServiceModel.Discovery.DiscoveryClient> Tworzy `Resolve` wiadomości przy użyciu odpowiednich nagłówków i wysyła żądanie rozwiązania. Odebrano odpowiedź jest skorelowane żądania rozpoznania oczekujących, a wynik jest dostarczany do obiektu wywołującego `Resolve` przy użyciu operacji <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Jeśli serwera proxy odnajdywania znajduje się w sieci i <xref:System.ServiceModel.Discovery.DiscoveryClient> wysyła żądanie odnajdywania w sposób multiemisji serwera proxy odnajdywania mogą odpowiadać za pomocą multiemisji pomijanie wiadomości powitania. <xref:System.ServiceModel.Discovery.DiscoveryClient> Zgłasza `ProxyAvailable` zdarzeń po odebraniu wiadomości powitania w odpowiedzi na pozostałych `Find` lub `Resolve` żądań. `ProxyAvailable` Zdarzenie zawiera <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> dotyczące serwera proxy odnajdywania. Jest deweloperów dzięki tym informacjom można przejść z Ad hoc na zarządzany tryb.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> reprezentuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Używane przez usługę lub klienta do wysyłania i odbierania komunikatów odnajdywania. Domyślnie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jest skonfigurowany do używania <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> tryb i wersji WSDiscovery11 protokołu WS Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> Służy do generowania <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> podczas odnajdywania lub ogłoszenie komunikatów wysyła usługi.  
  
## <a name="discoveryservice"></a>Discoveryservice i  
 <xref:System.ServiceModel.Discovery.DiscoveryService> Klasę abstrakcyjną zapewnia platformę do odbierania i przetwarzania `Probe` i `Resolve` wiadomości. Gdy `Probe` wiadomość zostanie odebrana, <xref:System.ServiceModel.Discovery.DiscoveryService> tworzy wystąpienie <xref:System.ServiceModel.Discovery.FindRequestContext> na podstawie wiadomości przychodzących, a następnie wywołuje <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metodę wirtualną. Gdy `Resolve` wiadomość zostanie odebrana, <xref:System.ServiceModel.Discovery.DiscoveryService> wywołuje <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> metodę wirtualną. Możesz dziedziczyć od tej klasy w celu zapewnienia niestandardowych implementacji usługi odnajdywania.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> Klasę abstrakcyjną udostępnia strukturę, odbierania i przetwarzania wiadomości odnajdywania i anonsu. Pochodne względem tej klasy i podczas wdrażania serwera proxy odnajdywania niestandardowych. Gdy `Probe` wiadomość zostaje odebrana w ramach multiemisji, <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasy wywołania `BeginShouldRedirectFind` metodę wirtualną, aby ustalić, czy komunikat multiemisji pomijanie powinny być przesyłane. Jeśli Deweloper zdecyduje nie wysyłanie komunikatów multiemisji pomijanie lub `Probe` wiadomość została odebrana w emisji pojedynczej, tworzy wystąpienie <xref:System.ServiceModel.Discovery.FindRequestContext> klasy na podstawie przychodzącego komunikatu i wywołuje `OnBeginFind` metodę wirtualną. Gdy `Resolve` wiadomość zostaje odebrana w ramach multiemisji, <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasy wywołania `ShouldRedirectResolve` metodę wirtualną, aby ustalić, czy komunikat multiemisji pomijanie powinny być przesyłane. Jeśli Deweloper zdecyduje nie wysyłanie komunikatów multiemisji pomijanie lub `Resolve` wiadomość została odebrana w emisji pojedynczej, tworzy wystąpienie <xref:System.ServiceModel.Discovery.ResolveCriteria> klasy na podstawie przychodzącego komunikatu i wywołuje `OnBeginResolve` metodę wirtualną. Po odebraniu wiadomości powitania lub Bye <xref:System.ServiceModel.Discovery.DiscoveryProxy> wywołuje odpowiednią metodę wirtualną (`OnBeginOnlineAnnouncement` lub `OnBeingOfflineAnnouncement`), która wywołuje zdarzenia anonsu.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> Klasa reprezentuje wersję protokołu odnajdywania do użycia.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Klasa jest używana do sterowania odnajdywania punktu końcowego, określ rozszerzenia, nazwy typów kontraktu dodatkowe. oraz zakresy skojarzony z tym punktem końcowym. To zachowanie jest dodawany do punktu końcowego aplikacji, aby skonfigurować jego <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Gdy <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> jest dodawany host usługi wszystkie punkty końcowe aplikacji hostowanej przez hosta usługi domyślnie stają się wykrywalny. Deweloper można wyłączyć odnajdywanie określonego punktu końcowego, ustawiając <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> właściwość `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Klasy zawiera reprezentację niezależny od wersji punktu końcowego opublikowana przez usługę. Zawiera on adresy punktów końcowych, nasłuchiwania identyfikatory URI, nazwy typów kontraktu, zakresy, wersja metadanych i rozszerzeniami określonymi przez dewelopera usługi. <xref:System.ServiceModel.Discovery.FindCriteria> Wysłane przez klienta podczas `Probe` operacji jest dopasowywana <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Jeśli spełnia kryteria, a następnie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> jest zwracana do klienta. Adres punktu końcowego w <xref:System.ServiceModel.Discovery.ResolveCriteria> jest dopasowywana adres punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Jeśli spełnia kryteria, a następnie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> jest zwracana do klienta.  
  
## <a name="findcriteria"></a>Kryteria znajdowania  
 <xref:System.ServiceModel.Discovery.FindCriteria> Klasa jest klasą niezależny od wersji, można określić kryteria używane podczas znajdowania usługi. W pełni obsługuje kryteria zdefiniowane odnajdowania WS dla zgodnych usług. Ma również rozszerzeń, które deweloperzy mogą używać do określenia wartości niestandardowych, które mogą być używane podczas dopasowywania procesów. Deweloper opracowuje kryteriów zakończenia dla `Find` operację, określając <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, określający łączna liczba usług szuka dewelopera lub który określa <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, która jest wartością, Określa, jak długo klient czeka na odpowiedzi.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> Utworzyć wystąpienia klasy przez usługę odnajdywania na podstawie `Probe` wiadomości, które otrzymuje, gdy klient jest inicjowany `Find` operacji. Zawiera on wystąpienie <xref:System.ServiceModel.Discovery.FindCriteria> , która została określona przez klienta.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> Klasy jest zwracany do obiektu wywołującego <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> z odpowiedziami z `Find` operacji. Jest również obecny w <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Zawiera on zbiór <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, czyli kolekcji odnalezione punkty końcowe i słownika <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> i <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> Klasa jest klasą niezależny od wersji, można określić kryteria używane podczas rozpoznawania usługi już znany. Zawiera adres punktu końcowego usługi znane. Deweloper opracowuje kryteriów zakończenia operacji Rozwiąż, określając <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, która określa, jak długo klient czeka na odpowiedzi.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> Jest zwracany do obiektu wywołującego <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody z odpowiedzi `Resolve` operacji. Jest również obecny w <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Zawiera on wystąpienie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, czyli odnalezione punkty końcowe i wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Klasy umożliwia deweloperom Dodawanie funkcji odnajdywania do usługi. Dodaj ten problem i <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Klasy iteruje przez punkty końcowe aplikacji dodany host usługi i tworzy zbiór <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> z wykrywalny punktów końcowych. Wszystkie punkty końcowe są wykrywane przez domyślny. Odnajdowanie określonego punktu końcowego można kontrolować przez dodanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> do tego punktu końcowego. Jeśli punkty końcowe ogłoszenie zostaną dodane do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> , a następnie anons wszystkie punkty końcowe wykrywalny jest wysyłana za pośrednictwem wszystkich punktów końcowych anons, gdy otwarcie lub zamknięcie hosta usługi.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Klasa jest standardowa ogłoszenie punktu końcowego, który jest wstępnie konfigurowany dla anonsu za pośrednictwem protokołu UDP powiązania multiemisji. Domyślnie <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jest skonfigurowany do używania wersji WSApril2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Klasa jest odnajdywania standardowego punktu końcowego, który jest wstępnie konfigurowany dla odnajdywania za pośrednictwem protokołu UDP powiązania multiemisji. Domyślnie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jest skonfigurowany do używania wersji protokołu WS Discovery WSDiscovery11 i <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> trybu.
