---
title: "Model obiektów odnajdywania WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68d6e156612ce707aa678b6589510b710b73e38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-discovery-object-model"></a>Model obiektów odnajdywania WCF
Odnajdywania WCF składa się z zestaw typów, które zapewniają ujednoliconego modelu programowania, który umożliwia pisanie usług, które są wykrywalny środowiska uruchomieniowego i klientów, którzy Znajdź i korzystania z tych usług.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Usługa wykrywalny i znajdowanie usługi  
 Aby usługa WCF wykrywalny, dodać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> do <xref:System.ServiceModel.Description.ServiceDescription> usługi hosta i Dodaj punkt końcowy odnajdowania. Jeśli usługa jest skonfigurowana do wysyłania wiadomości anonsu (przez dodanie <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) anonsu jest wysyłany, gdy host usługi jest otwarte i zamknięte.  
  
 Klient, który będzie nasłuchiwać komunikatów powiadomienia usługi obsługuje usługę anons i dodaje jeden lub więcej punktów końcowych anonsu. Usługa anonsu odbiera komunikaty anonsów i informuje o zdarzeniach anonsu.  
  
 Klient używa <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy do wyszukania dostępnych usług. Tworzy wystąpienie aplikacji klienckiej <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, przekazując odnajdowania punktu końcowego, który określa, gdzie można wysyłać wiadomości odnajdywania. Wywołania klienta <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodę, która wysyła `Probe` żądania. Nasłuchiwanie na odbieranie komunikatów odnajdywania, to usługi `Probe` żądania. Jeśli usługa jest zgodna z kryteriami `Probe`, wysyła `ProbeMatch` wiadomość do klienta.  
  
## <a name="object-model"></a>Model obiektu  
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
  
-   <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> Klasa dostarcza metody synchroniczne i asynchroniczne do wysyłania wiadomości powiadomienia. Istnieją dwa typy komunikatów anonsu, Hello i Bye. Wiadomość Hello są wysyłane do wskazują, że usługa stały się dostępne, i jest wysyłany komunikat Bye, aby wskazać, że istniejąca usługa stała się niedostępna. Utworzenie przez dewelopera <xref:System.ServiceModel.Discovery.AnnouncementClient> wystąpienia, przekazanie wystąpienia <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> jako parametru konstruktora.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>reprezentuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Jest używany przez usługi lub klienta do wysyłania i odbierania wiadomości powiadomienia. Domyślnie <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> klasy jest skonfigurowany do używania protokołu w wersji WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService>jest dostarczane przez system implementacji usługi anonsu, która odbiera i przetwarza wiadomości powiadomienia. Po odebraniu wiadomości powitania lub Bye <xref:System.ServiceModel.Discovery.AnnouncementService> wystąpienia wymaga odpowiedniej metody wirtualnej <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> lub <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, który informuje o zdarzeniach anonsu.  
  
## <a name="discoveryclient"></a>Obiekt DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Klasa jest używana przez aplikację klienta do znajdowania i usuwania dostępnych usług. Zapewnia metody synchroniczne i asynchroniczne Znajdowanie i rozwiązywanie usług opartych na określonym <xref:System.ServiceModel.Discovery.FindCriteria> i <xref:System.ServiceModel.Discovery.ResolveCriteria> odpowiednio. Utworzenie przez dewelopera <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienia i udostępnia wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jako parametru konstruktora.  
  
 Aby znaleźć usługi, deweloper wywołuje synchroniczna lub asynchroniczna `Find` metodę, która zapewnia <!--zz <xref:System.ServiceModel.Discription.FindCriteria> --> `FindCriteria` wystąpienia, które zawiera kryteria wyszukiwania, aby użyć. <xref:System.ServiceModel.Discovery.DiscoveryClient> Tworzy `Probe` komunikat z odpowiednią nagłówki i wysyła żądanie Znajdź. Ponieważ może istnieć więcej niż jedna oczekujących `Find` żądania w dowolnym momencie klienta są powiązane z odebranej odpowiedzi i sprawdza poprawność odpowiedzi. Następnie dostarcza wyniki do wywołującego `Find` za pomocą operacji <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Aby rozwiązać znanej usługi, deweloper wywołuje synchroniczna lub asynchroniczna `Resolve` metodę, która udostępnia wystąpienie <!--zz <xref:System.ServiceModel.ResolveCriteria>--> `ResolveCriteria` zawierający <xref:System.ServiceModel.EndpointAddress> znane usługi. <xref:System.ServiceModel.Discovery.DiscoveryClient> Tworzy `Resolve` komunikat z odpowiednią nagłówki i wysyła żądanie do rozpoznania. Odebrano odpowiedź jest skorelowany do rozpoznania oczekujących żądań i wynik jest dostarczane do funkcji wywołującej `Resolve` za pomocą operacji <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Jeśli serwer proxy odnajdywania znajduje się w sieci i <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` wysyła żądanie odnajdywania w sposób multiemisji serwera proxy odnajdywania może odpowiadać, podając wiadomość Hello pominięciu multiemisji. <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` Zgłasza `ProxyAvailable` zdarzeń po otrzymaniu wiadomości powitania w odpowiedzi na oczekujących `Find` lub `Resolve` żądań. `ProxyAvailable` Zdarzenie zawiera <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> dotyczące serwera proxy odnajdywania. Jest to deweloperom dzięki tym informacjom można przełączyć się z Ad hoc do zarządzany tryb.  
  
## <a name="discoveryendpoint"></a>Obiektu DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>reprezentuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Jest używany przez usługi lub klienta do wysyłania i odbierania wiadomości odnajdywania. Domyślnie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jest skonfigurowany do używania <!--zz <xref:System.ServiceModel.Discovery.DiscoveryMode.Managed>--> `Managed` tryb i wersji WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>Służy do generowania <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> podczas odnajdywania lub anonsu komunikatów wysyła usługi.  
  
## <a name="discoveryservice"></a>Obiekt DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> Klasy abstrakcyjnej zapewnia platformę do odbierania i przetwarzania `Probe` i `Resolve` wiadomości. Gdy `Probe` wiadomość zostanie odebrana, <xref:System.ServiceModel.Discovery.DiscoveryService> tworzy wystąpienie <xref:System.ServiceModel.Discovery.FindRequestContext> na podstawie przychodzącego komunikatu i wywołuje <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metoda wirtualna. Gdy `Resolve` wiadomość zostanie odebrana, <xref:System.ServiceModel.Discovery.DiscoveryService> wywołuje <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> metoda wirtualna. Ta klasa do niestandardowych implementacji usługi odnajdywania może dziedziczyć.  
  
## <a name="discoveryproxy"></a>Obiektu DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> Klasy abstrakcyjnej zapewnia platformę dla otrzymywanie i przetwarzanie komunikatów odnajdywania i anonsu. Pochodne względem tej klasy i podczas wdrażania serwera proxy odnajdywania niestandardowych. Gdy `Probe` komunikat jest odbierany przez funkcję multiemisji, <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasy wywołania `BeginShouldRedirectFind` metody wirtualnej, aby określić, czy komunikat o pominięciu multiemisji powinny być przesyłane. Jeśli Deweloper decyduje nie wysłać komunikat o pominięciu multiemisji lub `Probe` wiadomość została odebrana w emisji pojedynczej, tworzy wystąpienie <xref:System.ServiceModel.Discovery.FindRequestContext> klasy oparte na komunikat przychodzący i wywołuje `OnBeginFind` metoda wirtualna. Gdy `Resolve` komunikat jest odbierany przez funkcję multiemisji, <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasy wywołania `ShouldRedirectResolve` metody wirtualnej, aby określić, czy komunikat o pominięciu multiemisji powinny być przesyłane. Jeśli Deweloper decyduje nie wysłać komunikat o pominięciu multiemisji lub `Resolve` wiadomość została odebrana w emisji pojedynczej, tworzy wystąpienie <xref:System.ServiceModel.Discovery.ResolveCriteria> klasy oparte na komunikat przychodzący i wywołuje `OnBeginResolve` metoda wirtualna. Po odebraniu wiadomości powitania lub Bye <xref:System.ServiceModel.Discovery.DiscoveryProxy> wywołuje metodę wirtualną odpowiednie (`OnBeginOnlineAnnouncement` lub `OnBeingOfflineAnnouncement`), który informuje o zdarzeniach anonsu.  
  
## <a name="discoveryversion"></a>discoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> Klasa reprezentuje tę wersję protokołu odnajdowania.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Klasa jest używana do sterowania możliwość odnajdowania punktu końcowego, określ nazwy typów kontraktu dodatkowe rozszerzenia. i zakresy skojarzone z tym punktem końcowym. To zachowanie jest dodawany do punktu końcowego aplikacji, aby skonfigurować jego <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Gdy <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> jest dodawany do hosta usługi, wszystkie punkty końcowe aplikacji hostowanych przez hosta usługi domyślnie stają się wykrywalny. Deweloper można wyłączyć, ustawiając odnajdywania dla określonego punktu końcowego <!--zz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enable%2A>--> `Enable` właściwości `false`.  
  
## <a name="endpointdiscoverymetadata"></a>Obiektu EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Klasa udostępnia reprezentacja niezależnej od wersji punkt końcowy publikowane przez usługę. Zawiera adresy punktów końcowych, nasłuchiwania URI, nazwy typów kontraktu, zakresy, wersja metadanych i rozszerzeń określonych przez dewelopera usługi. <xref:System.ServiceModel.Discovery.FindCriteria> Wysłane przez klienta podczas `Probe` operacji jest dopasowywana <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Jeśli spełnia kryteria, a następnie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> jest zwracana do klienta. Adres punktu końcowego w <xref:System.ServiceModel.Discovery.ResolveCriteria> jest dopasowywana adres punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Jeśli spełnia kryteria, a następnie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> jest zwracana do klienta.  
  
## <a name="findcriteria"></a>Kryteria znajdowania  
 <xref:System.ServiceModel.Discovery.FindCriteria> Klasa jest klasą niezależny od wersji, można określić kryteria używane podczas znajdowania usługi. Obsługuje pełni określonych odnajdowania WS kryteriów dopasowania usług. Ma również rozszerzeń, które deweloperzy mogą używać do określenia wartości niestandardowych, które mogą być używane podczas dopasowywania procesów. Deweloper może zapewnić kryteria zakończenia `Find` operację, określając <!--zz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResult%2A>--> `MaxResult`, który określa liczbę usług szuka dewelopera lub który określa <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, który jest wartość, która określa, jak długo klient czeka na odpowiedzi.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> Utworzyć wystąpienia klasy przez usługę odnajdywania na podstawie `Probe` komunikat odbierze, gdy klient inicjuje `Find` operacji. Zawiera wystąpienie <xref:System.ServiceModel.Discovery.FindCriteria> podany przez klienta.  
  
## <a name="findresponse"></a>Obiektu FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> Klasy jest zwracana do wywołującego <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> odpowiedzi z `Find` operacji. Znajduje się również <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Zawiera kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, czyli kolekcji wykrytych punktów końcowych i słownika <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> i <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> Klasa jest klasą niezależny od wersji, można określić kryteria używane podczas rozpoznawania usługi już znany. Zawiera adres punktu końcowego usługi znane. Deweloper zapewniają kryteria zakończenia dla operacji rozpoznawania, określając <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, który określa, jak długo klient czeka na odpowiedzi.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> Jest zwracana do wywołującego <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody za pomocą odpowiedzi `Resolve` operacji. Znajduje się również <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Zawiera wystąpienie <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, czyli wykrytych punktów końcowych i wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>Obiekt ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Klasa umożliwia deweloperowi Dodaj funkcję odnajdywania do usługi. Dodaj ten problem i <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Klasy przechodzi przez punkty końcowe aplikacji dodane do usługi hosta i tworzy kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> z wykrywalny punktów końcowych. Wszystkie punkty końcowe są wykrywalny domyślnie. Możliwość odnajdowania punktu końcowego, w szczególności mogą być kontrolowane przez dodanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> do tego punktu końcowego. Jeśli punktów końcowych powiadomienia są dodawane do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> , a następnie anons wszystkie punkty końcowe wykrywalny jest wysyłany przez każdego z punktów końcowych powiadomienia, gdy host usługi jest otwarty lub zamknięty.  
  
## <a name="servicediscoveryextension"></a>ServiceDiscoveryExtension  
 <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension` Klasa jest tworzona przez <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> klasy. Punkty końcowe, które zostały wprowadzone wykrywalny można uzyskać z <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`. Ta klasa jest używana również w celu określenia implementacji usługi odnajdywania niestandardowych.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Klasa jest standardowe anonsu punktu końcowego, który jest wstępnie skonfigurowana do anonsowania za pośrednictwem protokołu UDP powiązanie multiemisji. Domyślnie <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jest skonfigurowany do używania wersji WSApril2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Klasa jest odnajdywania standardowego punktu końcowego, który jest wstępnie skonfigurowana do odnajdowania za pośrednictwem protokołu UDP powiązanie multiemisji. Domyślnie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jest skonfigurowany do używania wersji WSDiscovery11 WS-Discovery i <!--zz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.Adhoc>--> `Adhoc` tryb.
