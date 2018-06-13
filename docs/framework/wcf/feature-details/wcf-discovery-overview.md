---
title: Omówienie odnajdywania WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: c01ded15b3284058d7c5678409936e51fce1ea5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505904"
---
# <a name="wcf-discovery-overview"></a>Omówienie odnajdywania WCF
Interfejsy API wykrywania zapewnienia ujednoliconego modelu programowania dynamiczne publikacji i odnajdywania usług sieci Web za pomocą protokołu WS-Discovery. Te interfejsy API umożliwiają usług do publikowania się i klientom znalezienie usług opublikowanych. Gdy usługa następuje wykrywalny, usługa ma możliwość wysyłać powiadomienia, a także nasłuchiwania i odpowiadać na żądania odnajdywania. Wykrywalny usług można wysyłać wiadomości powitania ogłaszamy przybyciu w sieci i komunikaty Bye poinformować ich wyjścia z sieci. Aby znaleźć usługi, klienci wysyłają `Probe` żądania, która zawiera określone kryteria, takie jak typ kontraktu usługi, słowa kluczowe i zakresem w sieci. Odbieranie usług `Probe` żądania i ustalić, czy odpowiadają one kryteriom. Usługa zgodna, odpowiadały wysyłając `ProbeMatch` wiadomość do klienta informacje niezbędne do kontaktu z usługą. Klienci mogą również wysyłać `Resolve` żądania, dzięki czemu można znaleźć usługi, które mogą zmienić swój adres punktu końcowego. Usługi pasującego odpowiadanie na `Resolve` żądań wysyłając `ResolveMatch` wiadomość do klienta.  
  
## <a name="ad-hoc-and-managed-modes"></a>Tryby zarządzanych i Ad Hoc  
 Interfejs API Discovery obsługuje dwa różne tryby: zarządzane i Ad Hoc. Zarządzany tryb jest centralny serwer o nazwie serwera proxy odnajdywania, która zawiera informacje o dostępnych usług. Serwera proxy odnajdywania można wypełniać za pomocą informacji o usługach na różne sposoby. Na przykład usługi może wysyłać komunikaty anonsów podczas uruchamiania serwera proxy odnajdywania lub serwer proxy może odczytywać dane z bazy danych lub plik konfiguracji w celu ustalenia, jakie usługi są dostępne. Jak jest wypełniana serwera proxy odnajdywania zależy całkowicie dewelopera. Klienci używają serwera proxy odnajdywania można pobrać informacji o dostępnych usług. Gdy klient szuka usługi go wysyła `Probe` wiadomość do serwera proxy odnajdywania i serwer proxy Określa, czy którakolwiek z nich bez informacji o zgodne Usługa klienta jest wyszukiwanie. Jeśli ma dopasowania wysyła serwera proxy odnajdywania `ProbeMatch` odpowiedź z powrotem do klienta. Klient może następnie skontaktować się z usługą, bezpośrednio za pomocą usługi informacje zwrócone z serwera proxy. Zasada klucza za zarządzany tryb jest, że żądania odnajdywania są wysyłane w sposób emisji pojedynczej do jednego urzędu certyfikacji, serwera proxy odnajdywania. .NET Framework zawiera najważniejsze składniki, które pozwalają na tworzenie własnego serwera proxy. Klienci i usługi można zlokalizować serwera proxy przez wiele metod:  
  
-   Serwer proxy może odpowiadać na komunikaty ad hoc.  
  
-   Serwer proxy można Wyślij anonse podczas uruchamiania.  
  
-   Aby wyszukać określonego dobrze znanego punktu końcowego można pisać klientów i usług.  
  
 W trybie Ad-Hoc serwer nie jest scentralizowane. Wszystkie komunikaty odnajdywania, takie jak Anonse usługi i żądania klientów są wysyłane w sposób multiemisji. Domyślnie programu .NET Framework obsługuje odnajdywania Ad Hoc za pośrednictwem protokołu UDP. Na przykład jeśli usługa jest skonfigurowana do wysłania powiadomienia Hello przy uruchamianiu, wysyła on za pośrednictwem adresu dobrze znane, multiemisji przy użyciu protokołu UDP. Klienci muszą aktywnie nasłuchiwania ogłoszenia i odpowiednio je przetworzyć. Gdy klient wyśle `Probe` komunikatu dla usługi są wysyłane za pośrednictwem sieci przy użyciu multiemisji protokołu. Każda usługa, która odbiera żądanie określa, czy spełnia on kryteria `Probe` wiadomości i odpowiada bezpośrednio do klienta z `ProbeMatch` komunikatów, jeśli usługa jest zgodna z kryteriami `Probe` wiadomości.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Zalety używania odnajdywania WCF  
 Ponieważ odnajdywania WCF jest implementowane za pomocą protokołu WS-Discovery jest współpraca z innymi klientami, usług i serwerów proxy, które również implementują WS-Discovery. Odnajdywania WCF jest oparty na istniejących API WCF, która ułatwia dodawanie funkcji odnajdywania do istniejących usług i klientów. Odnajdowanie usługi można łatwo dodać za pomocą ustawienia konfiguracji aplikacji. Ponadto odnajdywania WCF obsługuje również, przy użyciu protokołu odnajdowania za pośrednictwem innych transportów, takie jak sieci równorzędnej, nazewnictwa nakładce i HTTP. Odnajdywania WCF zapewnia obsługę zarządzany tryb działania, w których jest używany serwer proxy odnajdywania. To zmniejszenie ruchu w sieci, ponieważ komunikaty są wysyłane bezpośrednio do serwera proxy odnajdywania zamiast wysyłać komunikatów multiemisji do całej sieci. Odnajdywania WCF umożliwia również większą elastyczność podczas pracy z usługami sieci Web. Na przykład można zmienić adres usługi bez konieczności ponownej konfiguracji klienta lub usługi. Gdy klient musi uzyskać dostęp do usługi, pozwala na wydawanie `Probe` komunikatu za pośrednictwem `Find` żądania i oczekują usługi z bieżącego adresu. Odnajdywania WCF umożliwia klientowi wyszukiwania na podstawie różnych kryteriów, takich jak typy kontraktu, elementy powiązania, przestrzeni nazw, zakresu oraz słowa kluczowe i numery wersji usługi. Odnajdywania WCF umożliwia odnajdywanie czasu środowiska uruchomieniowego i projektu. Dodawanie odnajdywania aplikacji można włączyć inne scenariusze, takie jak odporność na uszkodzenia i konfiguracji automatycznej.  
  
## <a name="service-publication"></a>Usługa publikacji  
 Aby usługa wykrywalny, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musi zostać dodany do hosta usługi i odnajdywanie punktu końcowego musi zostać dodany do określ, gdzie nasłuchiwać komunikatów odnajdywania. Poniższy przykład kodu pokazuje, jak samodzielnie hostowana usługa może być modyfikowany w taki sposób, aby był wykrywalny.  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie musi zostać dodany do opisu usługi do być wykrywalny przez usługę. A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienie musi zostać dodany do na informują usługa skąd do nasłuchiwania żądań odnajdywania usługi hosta. W tym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (która jest pochodną <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) jest dodawany do określenia, czy usługa powinna nasłuchiwać żądań odnajdywania za pośrednictwem protokołu UDP multiemisji transportu. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Służy do odnajdowania Ad-Hoc, ponieważ wszystkie komunikaty są wysyłane w sposób multiemisji.  
  
## <a name="announcement"></a>Anonsu  
 Domyślnie usługi publikacji nie wysyła wiadomości powiadomienia. Usługa musi być skonfigurowana do wysyłania wiadomości powiadomienia. Zapewnia to większą elastyczność moduły zapisujące usługi ponieważ one ogłaszamy usługi niezależnie od nasłuchiwanie komunikatów odnajdywania. Powiadomienia usługi również może służyć jako mechanizm rejestrowania usług za pomocą serwera proxy odnajdywania lub innych rejestrów usługi. Poniższy kod przedstawia sposób konfigurowania usługi do wysłania komunikatów Anons powiązania protokołu UDP.  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>Odnajdowanie usługi  
 Można użyć aplikacji klienckiej <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy można znaleźć usługi. Deweloper tworzy wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, która przekazuje w odnajdowania punktu końcowego, który określa, który ma zostać wysłana `Probe` lub `Resolve` wiadomości. Klient następnie wywołuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , który określa kryteria wyszukiwania w <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia. W przypadku znalezienia pasujących usług <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> zwraca kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Poniższy kod przedstawia sposób wywołania `Find` metody, a następnie połączyć się z usługą odnalezione.  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>Odnajdywanie i zabezpieczeń na poziomie komunikatu  
 Korzystając z zabezpieczeniami na poziomie wiadomości jest niezbędne do określenia <xref:System.ServiceModel.EndpointIdentity> na punkt końcowy odnajdowania usługi i odpowiadający mu <xref:System.ServiceModel.EndpointIdentity> odnajdywania klienta w punkcie końcowym. Aby uzyskać więcej informacji dotyczących zabezpieczeń na poziomie komunikatu, zobacz [zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Odnajdywanie i sieci Web usług hostowanych  
 Aby usługi WCF być wykrywalny musi być uruchomiona. Usługi WCF hostowanej przez usługi IIS lub WAS nie uruchamiaj do usług IIS / WAS odbiera komunikat przeznaczony dla usługi, dlatego nie może być wykrywalny domyślnie.  Dostępne są dwie opcje do wprowadzania wykrywalny usług hostowanych w sieci Web:  
  
1.  Funkcja Auto-Start systemu Windows Server AppFabric  
  
2.  Użyj serwera proxy odnajdywania do komunikacji w imieniu usługi  
  
 Windows Server AppFabric ma funkcję automatycznego uruchamiania, która umożliwi usługa ma zostać uruchomiony przed otrzymaniem komunikaty. Auto-Start ustawiona, usługi IIS / WAS hostowanej usługi można skonfigurować w celu być wykrywalny. Aby uzyskać więcej informacji na temat automatycznego uruchamiania funkcji, zobacz [systemu Windows Server AppFabric automatycznego uruchamiania funkcji](http://go.microsoft.com/fwlink/?LinkId=205545). Wraz z włączenie funkcji automatycznego uruchamiania, należy skonfigurować usługę odnajdywania. Aby uzyskać więcej informacji, zobacz [porady: programowane Dodawanie odnajdywania usługi WCF i klienta](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Konfigurowanie odnajdywania w pliku konfiguracyjnym](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Serwer proxy odnajdywania może służyć do komunikacji imieniu usług WCF, gdy usługa nie jest uruchomiona. Serwer proxy można nasłuchiwać sondy lub rozwiązać wiadomości i odpowiedzi do klienta. Klient następnie może wysyłać komunikaty bezpośrednio do usługi. Gdy klient wysyła komunikat do usługi będzie można wdrożyć odpowiedzieć na wiadomość. Aby uzyskać więcej informacji o implementacji odnajdywania serwera proxy, zobacz temat [Implementowanie serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  Do odnajdywania WCF działał prawidłowo wszystkie karty sieciowe (kontrolera interfejsu sieciowego) powinien mieć tylko 1 adres IP.
