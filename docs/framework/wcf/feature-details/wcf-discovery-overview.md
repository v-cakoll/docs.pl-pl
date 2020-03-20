---
title: Omówienie odnajdywania WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 449d54e0dd1948885a7298fb4da46067de3eb9d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184211"
---
# <a name="wcf-discovery-overview"></a>Omówienie odnajdywania WCF
Interfejsy API odnajdywania zapewniają ujednolicony model programowania dla dynamicznej publikacji i odnajdowania usług sieci Web przy użyciu protokołu WS-Discovery. Te interfejsy API umożliwiają usługom publikowanie siebie i klientów w celu znalezienia opublikowanych usług. Gdy usługa jest wykrywalna, usługa ma możliwość wysyłania komunikatów anonsu, a także nasłuchiwania i odpowiadania na żądania odnajdywania. Wykrywalne usługi mogą wysyłać wiadomości Hello, aby ogłosić ich przybycie do sieci i wiadomości Bye, aby ogłosić ich odejście z sieci. Aby znaleźć usługę, klienci `Probe` wysyłają żądanie, które zawiera określone kryteria, takie jak typ umowy serwisowej, słowa kluczowe i zakres w sieci. Usługi otrzymują `Probe` żądanie i określają, czy są zgodne z kryteriami. Jeśli usługa jest zgodna, odpowiada, `ProbeMatch` wysyłając wiadomość z powrotem do klienta z informacjami niezbędnymi do skontaktowania się z usługą. Klienci mogą `Resolve` również wysyłać żądania, które umożliwiają im znajdowanie usług, które mogły zmienić ich adres punktu końcowego. Pasujące usługi `Resolve` odpowiadają na `ResolveMatch` żądania, wysyłając wiadomość z powrotem do klienta.  
  
## <a name="ad-hoc-and-managed-modes"></a>Tryby ad-hoc i zarządzane  
 Interfejs API odnajdywania obsługuje dwa różne tryby: zarządzany i ad-hoc. W trybie zarządzanym istnieje scentralizowany serwer o nazwie serwer proxy odnajdowania, który przechowuje informacje o dostępnych usługach. Serwer proxy odnajdywania może być wypełniany informacjami o usługach na różne sposoby. Na przykład usługi mogą wysyłać komunikaty anonsów podczas uruchamiania do serwera proxy odnajdowania lub serwer proxy może odczytywać dane z bazy danych lub pliku konfiguracji, aby określić, jakie usługi są dostępne. Sposób wypełniania serwera proxy odnajdywania zależy całkowicie od dewelopera. Klienci używają serwera proxy odnajdowania do pobierania informacji o dostępnych usługach. Gdy klient wyszukuje usługę `Probe` wysyła wiadomość do serwera proxy odnajdywania, a serwer proxy określa, czy którakolwiek z usług, które zna o dopasowaniu usługi, którą klient szuka. Jeśli są zgodne serwera proxy `ProbeMatch` odnajdywania wysyła odpowiedź z powrotem do klienta. Klient może następnie skontaktować się z usługą bezpośrednio przy użyciu informacji o usłudze zwróconych z serwera proxy. Kluczową zasadą trybu zarządzanego jest to, że żądania odnajdywania są wysyłane w sposób emisji pojedynczej do jednego urzędu, serwera proxy odnajdywania. .NET Framework zawiera kluczowe składniki, które umożliwiają tworzenie własnego serwera proxy. Klienci i usługi mogą zlokalizować serwer proxy za pomocą wielu metod:  
  
- Serwer proxy może odpowiadać na wiadomości ad hoc.  
  
- Serwer proxy może wysłać komunikat anonsu podczas uruchamiania.  
  
- Klienci i usługi mogą być zapisywane w celu wyszukywana określonego dobrze znanego punktu końcowego.  
  
 W trybie Ad-Hoc nie ma scentralizowanego serwera. Wszystkie komunikaty odnajdywania, takie jak anonse usług i żądania klientów są wysyłane w sposób multiemisji. Domyślnie program .NET Framework zawiera obsługę odnajdowania ad-hoc za pomocą protokołu UDP. Na przykład jeśli usługa jest skonfigurowana do wysyłania hello anonsu podczas uruchamiania, wysyła go za pośrednictwem dobrze znanego adresu multiemisji przy użyciu protokołu UDP. Klienci muszą aktywnie słuchać tych ogłoszeń i odpowiednio je przetwarzać. Gdy klient wysyła `Probe` wiadomość dla usługi, jest on wysyłany przez sieć przy użyciu protokołu multiemisji. Każda usługa, która odbiera żądanie określa, czy `Probe` spełnia kryteria w wiadomości i `ProbeMatch` odpowiada bezpośrednio do klienta z `Probe` komunikatem, jeśli usługa spełnia kryteria określone w komunikacie.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Korzyści z korzystania z WCF Discovery  
 Ponieważ WCF Discovery jest zaimplementowana przy użyciu protokołu WS-Discovery jest interoperacyjne z innymi klientami, usługami i serwerami proxy, które implementują WS-Discovery, jak również. Odnajdowanie WCF jest zbudowany na istniejących interfejsów API WCF, co ułatwia dodawanie funkcji odnajdywania do istniejących usług i klientów. Wykrywalność usługi można łatwo dodać za pomocą ustawień konfiguracji aplikacji. Ponadto WCF Discovery obsługuje również przy użyciu protokołu odnajdywania za pośrednictwem innych transportów, takich jak sieć równorzędna, nakładka nazewnictwa i HTTP. Odnajdowanie WCF zapewnia obsługę zarządzanego trybu działania, w którym używany jest serwer proxy odnajdywania. Może to zmniejszyć ruch sieciowy, ponieważ wiadomości są wysyłane bezpośrednio do serwera proxy odnajdywania zamiast wysyłać wiadomości multiemisji do całej sieci. WCF Discovery pozwala również na większą elastyczność podczas pracy z usługami sieci Web. Na przykład można zmienić adres usługi bez konieczności ponownego konfigurowania klienta lub usługi. Gdy klient musi uzyskać dostęp do `Probe` usługi, `Find` może wydać komunikat za pośrednictwem żądania i oczekiwać, że usługa odpowie za pomocą bieżącego adresu. Odnajdywanie WCF umożliwia klientowi wyszukiwanie usługi na podstawie różnych kryteriów, w tym typów umów, elementów wiązania, przestrzeni nazw, zakresu i słów kluczowych lub numerów wersji. WCF Discovery umożliwia odnajdowanie czasu wykonywania i projektowania. Dodawanie odnajdowania do aplikacji może służyć do włączania innych scenariuszy, takich jak odporność na uszkodzenia i konfiguracji automatycznej.  
  
## <a name="service-publication"></a>Publikacja usługi  
 Aby usługa można było <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> odnajdować, należy dodać do hosta usługi, a punkt końcowy odnajdywania musi zostać dodany, aby określić, gdzie nasłuchiwać komunikaty odnajdywania. Poniższy przykład kodu pokazuje, jak usługa hostowana samodzielnie może być modyfikowana, aby była wykrywalna.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

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
  
 Wystąpienie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musi zostać dodane do opisu usługi, aby usługa była wykrywalna. Wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> musi zostać dodane do hosta usługi, aby poinformować usługę, gdzie można nasłuchiwać żądań odnajdywania. W tym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (który pochodzi <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>od ) jest dodawany, aby określić, że usługa powinna nasłuchiwać żądań odnajdywania za sprawą transportu multiemisji UDP. Jest <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> używany do odnajdowania ad-hoc, ponieważ wszystkie wiadomości są wysyłane w sposób multiemisji.  
  
## <a name="announcement"></a>Ogłoszenie  
 Domyślnie publikacja usługi nie wysyła komunikatów anonsu. Usługa musi być skonfigurowana do wysyłania komunikatów anonsu. Zapewnia to dodatkową elastyczność dla modułów zapisu usług, ponieważ mogą one ogłosić usługi oddzielnie od nasłuchiwania komunikatów odnajdywania. Anons usługi może być również używany jako mechanizm rejestrowania usług za pomocą serwera proxy odnajdywania lub innych rejestrów usług. Poniższy kod pokazuje, jak skonfigurować usługę do wysyłania komunikatów anonsu za sprawą powiązania UDP.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

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
  
## <a name="service-discovery"></a>Odnajdywanie usług  
 Aplikacja kliencka <xref:System.ServiceModel.Discovery.DiscoveryClient> może używać klasy do znajdowania usług. Deweloper tworzy wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, która przekazuje w punkcie końcowym odnajdywania, który określa, gdzie wysłać `Probe` lub `Resolve` wiadomości. Następnie klient <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> wywołuje, który określa <xref:System.ServiceModel.Discovery.FindCriteria> kryteria wyszukiwania w wystąpieniu. Jeśli zostaną znalezione <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> pasujące usługi, zwraca kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Poniższy kod pokazuje, `Find` jak wywołać metodę, a następnie połączyć się z odnalezioną usługą.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Zabezpieczenia odnajdowania i poziomu wiadomości  
 Podczas korzystania z zabezpieczeń na poziomie <xref:System.ServiceModel.EndpointIdentity> wiadomości jest konieczne, aby <xref:System.ServiceModel.EndpointIdentity> określić punkt końcowy odnajdywania usługi i dopasowania w punkcie końcowym odnajdywania klienta. Aby uzyskać więcej informacji na temat zabezpieczeń na poziomie wiadomości, zobacz [Zabezpieczenia wiadomości](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Odnajdowanie i usługi hostowane w sieci Web  
 Aby usługi WCF być wykrywalne muszą być uruchomione. Usługi WCF hostowane w usługach IIS lub WAS nie są uruchamiane, dopóki usługi IIS/WAS nie otrzymają wiadomości powiązanej z usługą, więc domyślnie nie można ich odnaleźć.  Istnieją dwie opcje, dzięki czemu usługi hostowane w sieci Web są wykrywalne:  
  
1. Korzystanie z funkcji Automatycznego uruchamiania aplikacji systemu Windows Server  
  
2. Używanie serwera proxy odnajdywania do komunikowania się w imieniu usługi  
  
 System Windows Server AppFabric ma funkcję automatycznego uruchamiania, która umożliwia uruchomienie usługi przed odebraniem jakichkolwiek wiadomości. Za pomocą tego zestawu autostart można skonfigurować usługę hosta IIS/WAS do wykrywania. Aby uzyskać więcej informacji na temat funkcji Automatycznego uruchamiania, zobacz [Funkcja automatycznego uruchamiania aplikacji systemu Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677260(v=azure.10)). Wraz z włączeniem funkcji Auto-Start należy skonfigurować usługę do odnajdowania. Aby uzyskać więcej informacji, zobacz [Jak: Programowo dodawanie wykrywalności do usługi WCF i](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[odnajdowanie konfiguracji klienta w pliku konfiguracyjnym](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Serwer proxy odnajdywania może służyć do komunikowania się w imieniu usługi WCF, gdy usługa nie jest uruchomiona. Serwer proxy może nasłuchiwać sondy lub rozpoznawania wiadomości i odpowiadać na klienta. Klient może następnie wysyłać wiadomości bezpośrednio do usługi. Gdy klient wyśle wiadomość do usługi, zostanie on smówiąc się, aby odpowiedzieć na wiadomość. Aby uzyskać więcej informacji na temat implementowania serwera proxy [odnajdywania, zobacz Implementowanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> Aby odnajdywanie WCF działało poprawnie, wszystkie karty sieciowe (kontroler interfejsu sieciowego) powinny mieć tylko 1 adres IP.
