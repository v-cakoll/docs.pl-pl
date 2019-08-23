---
title: Omówienie odnajdywania WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: fce16038b4c9ab65047125be1881be4b86976aee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931854"
---
# <a name="wcf-discovery-overview"></a>Omówienie odnajdywania WCF
Interfejsy API odnajdywania zapewniają ujednolicony model programowania dla publikacji dynamicznej i odnajdywania usług sieci Web przy użyciu protokołu WS-Discovery. Te interfejsy API umożliwiają usługom publikowanie samych opublikowanych usług i klientów. Po przeprowadzeniu odnajdywania usługi Usługa może wysyłać komunikaty dotyczące anonsów, a także nasłuchiwać żądań odnajdywania i odpowiadać na nie. Odnajdywane usługi mogą wysyłać wiadomości Hello w celu ogłoszenia ich przybycia do sieci i bye komunikaty, aby ogłosić wychodzące z sieci. Aby znaleźć usługę, klienci wysyłają `Probe` żądanie zawierające określone kryteria, takie jak typ kontraktu usługi, słowa kluczowe i zakres w sieci. Usługi odbierają `Probe` żądanie i określają, czy pasują do kryteriów. Jeśli usługa jest zgodna, reaguje, wysyłając `ProbeMatch` wiadomość z powrotem do klienta przy użyciu informacji niezbędnych do skontaktowania się z usługą. Klienci mogą również wysyłać `Resolve` żądania, które umożliwiają znalezienie usług, które mogły zmienić adres punktu końcowego. Zgodne usługi odpowiadają `Resolve` na żądania przez `ResolveMatch` wysłanie komunikatu z powrotem do klienta.  
  
## <a name="ad-hoc-and-managed-modes"></a>Tryby ad hoc i zarządzane  
 Interfejs API odnajdowania obsługuje dwa różne tryby: Zarządzane i ad hoc. W trybie zarządzanym istnieje scentralizowany serwer o nazwie serwer proxy odnajdywania, który przechowuje informacje o dostępnych usługach. Serwer proxy odnajdywania można wypełnić informacjami o usługach na różne sposoby. Na przykład usługi mogą wysyłać komunikaty anonsu podczas uruchamiania do serwera proxy odnajdywania lub serwer proxy może odczytywać dane z bazy danych lub pliku konfiguracji, aby określić, które usługi są dostępne. Sposób wypełnienia serwera proxy odnajdywania jest całkowicie do dewelopera. Klienci używają serwera proxy odnajdywania do pobierania informacji o dostępnych usługach. Gdy klient wyszukuje usługę, wysyła `Probe` komunikat do serwera proxy odnajdywania, a serwer proxy określa, czy dowolna z usług, których zna, jest zgodna z usługą wyszukiwaną przez klienta. Jeśli jest zgodny z serwerem proxy odnajdywania, `ProbeMatch` wysyła odpowiedź z powrotem do klienta. Klient może następnie skontaktować się bezpośrednio z usługą przy użyciu informacji o usłudze zwróconych z serwera proxy. Kluczową zasadami związanymi z trybem zarządzanym jest to, że żądania odnajdowania są wysyłane do jednego urzędu, a serwer proxy odnajdywania. .NET Framework zawiera kluczowe składniki, które umożliwiają tworzenie własnego serwera proxy. Klienci i usługi mogą lokalizować serwer proxy przez wiele metod:  
  
- Serwer proxy może odpowiadać na komunikaty ad hoc.  
  
- Serwer proxy może wysłać komunikat anonsu podczas uruchamiania.  
  
- Klienci i usługi mogą być napisanie, aby szukać określonego dobrze znanego punktu końcowego.  
  
 W trybie ad hoc nie istnieje scentralizowany serwer. Wszystkie komunikaty odnajdowania, takie jak anonsy usług i żądania klientów, są wysyłane w sposób multiemisyjny. Domyślnie .NET Framework zawiera obsługę odnajdywania ad hoc za pośrednictwem protokołu UDP. Na przykład jeśli usługa jest skonfigurowana do wysyłania powiadomienia o powitaniu podczas uruchamiania, wysyła je za pośrednictwem dobrze znanego adresu multiemisji przy użyciu protokołu UDP. Klienci muszą aktywnie słuchać tych anonsów i przetwarzać je odpowiednio. Gdy klient wysyła `Probe` komunikat dla usługi, jest wysyłany przez sieć przy użyciu protokołu multiemisji. Każda usługa, która odbiera żądanie, określa, czy pasuje do kryteriów w `Probe` komunikacie i reaguje bezpośrednio na klienta `ProbeMatch` z komunikatem, jeśli usługa jest zgodna z kryteriami określonymi `Probe` w komunikacie.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Zalety korzystania z funkcji odnajdywania WCF  
 Ponieważ Odnajdywanie WCF jest implementowane za pomocą protokołu WS-Discovery, może współdziałać z innymi klientami, usługami i serwerami proxy, które również implementują usługę WS-Discovery. Funkcja odnajdywania WCF została utworzona na podstawie istniejących interfejsów API WCF, co ułatwia dodawanie funkcji odnajdywania do istniejących usług i klientów. Możliwość odnajdowania usług może być łatwo dodawana za pomocą ustawień konfiguracji aplikacji. Ponadto funkcja odnajdywania w programie WCF obsługuje również korzystanie z protokołu odnajdywania w różnych transportach, takich jak peer, nadawanie nazw i HTTP. Funkcja odnajdywania WCF zapewnia obsługę zarządzanego trybu działania, w którym jest używany serwer proxy odnajdywania. Może to zmniejszyć obciążenie sieci, ponieważ komunikaty są wysyłane bezpośrednio do serwera proxy odnajdywania zamiast wysyłania komunikatów multiemisji do całej sieci. Funkcja odnajdywania WCF umożliwia również większą elastyczność pracy z usługami sieci Web. Można na przykład zmienić adres usługi bez konieczności ponownego konfigurowania klienta lub usługi. Gdy klient musi uzyskać dostęp do usługi, może wydać `Probe` komunikat `Find` przez żądanie i oczekiwać, że usługa odpowie z bieżącym adresem. Funkcja odnajdywania WCF umożliwia klientowi wyszukanie usługi na podstawie różnych kryteriów, takich jak typy kontraktów, elementy powiązania, przestrzeń nazw, zakres i słowa kluczowe lub numery wersji. Funkcja odnajdywania WCF umożliwia wykrywanie środowiska uruchomieniowego i czasu projektowania. Dodawanie odnajdywania do aplikacji może służyć do włączania innych scenariuszy, takich jak odporność na uszkodzenia i konfiguracja samoobsługi.  
  
## <a name="service-publication"></a>Publikacja usługi  
 Aby umożliwić odnajdywanie usługi, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> należy dodać do hosta usługi, a punkt końcowy odnajdywania musi zostać dodany w celu określenia miejsca, w którym mają być nasłuchiwani komunikaty odnajdowania. Poniższy przykład kodu pokazuje, jak można zmodyfikować usługę samoobsługową, aby umożliwić jej odnajdowanie.  
  
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
  
 Aby można było odnaleźć usługę, należy dodać wystąpieniedoopisuusługi.<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Należy <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> dodać wystąpienie do hosta usługi, aby poinformować usługę, gdzie ma być nasłuchiwanie żądań odnajdywania. W tym przykładzie zostanie dodany <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (pochodzący z <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>), aby określić, że usługa powinna nasłuchiwać żądań odnajdywania za pośrednictwem transportu multiemisji UDP. Służy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do odnajdywania ad hoc, ponieważ wszystkie komunikaty są wysyłane w sposób multiemisyjny.  
  
## <a name="announcement"></a>Instruktaż  
 Domyślnie publikacja usługi nie wysyła komunikatów anonsu. Usługa musi być skonfigurowana do wysyłania komunikatów anonsu. Zapewnia to dodatkową elastyczność dla modułów zapisujących usługi, ponieważ mogą one ogłosić usługę niezależnie od nasłuchiwania komunikatów odnajdywania. Anons usługi może również służyć jako mechanizm rejestrowania usług przy użyciu serwera proxy odnajdywania lub innych rejestrów usług. Poniższy kod przedstawia sposób konfigurowania usługi do wysyłania komunikatów anonsów za pośrednictwem powiązania UDP.  
  
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
  
## <a name="service-discovery"></a>Odnajdowanie usług  
 Aplikacja kliencka może używać <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy do znajdowania usług. Deweloper tworzy wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, która przekazuje w punkcie końcowym odnajdywania, który określa, gdzie należy `Probe` wysyłać `Resolve` lub wiadomości. Klient następnie wywołuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , aby określić kryteria wyszukiwania <xref:System.ServiceModel.Discovery.FindCriteria> w ramach wystąpienia. W przypadku znalezienia <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> pasujących usług zwraca <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>kolekcję. Poniższy kod pokazuje, `Find` jak wywołać metodę, a następnie nawiązać połączenie z odnalezioną usługą.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Odnajdywanie i zabezpieczenia na poziomie komunikatów  
 <xref:System.ServiceModel.EndpointIdentity> W przypadku korzystania z zabezpieczeń na poziomie komunikatów należy określić punkt końcowy odnajdowania usług i dopasowanie <xref:System.ServiceModel.EndpointIdentity> do punktu końcowego odnajdywania klienta. Aby uzyskać więcej informacji na temat zabezpieczeń na poziomie komunikatów, zobacz [zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Odnajdywanie i usługi hostowane w sieci Web  
 Aby można było odnajdować usługi WCF, muszą one być uruchomione. Usługi WCF hostowane w usługach IIS lub nie zostały uruchomione do momentu otrzymania przez program IIS/odebrania komunikatu powiązanego z usługą, więc nie można ich odnaleźć domyślnie.  Dostępne są dwie opcje umożliwiające odnajdywanie usług hostowanych w sieci Web:  
  
1. Korzystanie z funkcji Autostart systemu Windows Server AppFabric  
  
2. Korzystanie z serwera proxy odnajdywania w celu komunikowania się w imieniu usługi  
  
 System Windows Server AppFabric zawiera funkcję Autostart, która umożliwi uruchomienie usługi przed odebraniem jakichkolwiek komunikatów. Dzięki temu zestawowi automatycznego uruchamiania można skonfigurować usługę hostowaną w usługach IIS/WAS. Aby uzyskać więcej informacji na temat funkcji Autostart, zobacz [Funkcja Autostart systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=205545). Wraz z włączeniem funkcji Autostart należy skonfigurować usługę do odnajdowania. Aby uzyskać więcej informacji, zobacz [jak: Programowe Dodawanie możliwości odnajdywania do usługi WCF i](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)klienta[Konfigurowanie odnajdywania w pliku konfiguracji](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Serwer proxy odnajdywania może być używany do komunikowania się w imieniu usługi WCF, gdy usługa nie jest uruchomiona. Serwer proxy może nasłuchiwać sondy lub rozwiązywać komunikaty i odpowiadać na klienta. Klient może następnie wysyłać wiadomości bezpośrednio do usługi. Gdy klient wysyła komunikat do usługi, zostanie ona utworzona w celu odpowiedzi na wiadomość. Aby uzyskać więcej informacji na temat implementowania serwera proxy odnajdywania, zobacz [Wdrażanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> Aby Odnajdywanie WCF działało prawidłowo, wszystkie karty sieciowe (kontroler interfejsu sieciowego) powinny mieć tylko 1 adres IP.
