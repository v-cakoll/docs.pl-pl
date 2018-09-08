---
title: Omówienie odnajdywania WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 24d758502e360a8368be25c506b8648b12a3eb20
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44173077"
---
# <a name="wcf-discovery-overview"></a>Omówienie odnajdywania WCF
API odnajdywania udostępniają jednolity model programowania do opublikowania dynamiczne i odnajdywania usług sieci Web przy użyciu protokołu WS Discovery. Te interfejsy API umożliwiają services, aby publikować z nimi i klientów w celu znalezienia opublikowanych usług. Gdy usługa jest wykrywalne, usługa ma możliwość wysyłania komunikatów Anons, a także nasłuchiwania i odpowiadania na żądania odnajdywania. Wykrywalny usług można wysłać wiadomości powitania poinformować ich przybycia w sieci i Bye komunikaty, aby poinformować o ich wyjścia z sieci. Aby znaleźć usługi, klienci wysyłają `Probe` żądanie, które zawiera określone kryteria, takich jak typ kontraktu usługi, słowa kluczowe i zakresu w sieci. Usługi odbierać `Probe` żądania i określić, czy spełniają kryteria. Jeśli usługa jest zgodny, odpowie, wysyłając `ProbeMatch` wiadomość do klienta przy użyciu informacji niezbędnych do kontaktu z usługą. Klienci mogą również wysyłać `Resolve` żądań, które pozwalają znaleźć usług, które uległy zmianie adresu punktu końcowego. Zgodnych usług odpowiadanie na `Resolve` żądań, wysyłając `ResolveMatch` wiadomość do klienta.  
  
## <a name="ad-hoc-and-managed-modes"></a>Tryby zarządzanych i Ad-Hoc  
 Interfejs API Discovery obsługuje dwa różne tryby: zarządzanych i Ad-Hoc. Zarządzany tryb ma centralny serwer o nazwie serwera proxy odnajdywania, która przechowuje informacje o dostępnych usługach. Serwera proxy odnajdywania można wypełnić przy użyciu informacji o usługach różne sposoby. Na przykład services wysłać komunikaty anonsów podczas uruchamiania serwera proxy odnajdywania lub serwer proxy może odczytywać dane z bazy danych lub plik konfiguracji, aby ustalić, jakie usługi są dostępne. Jak jest wypełniana serwera proxy odnajdywania zależy wyłącznie od dewelopera. Klienci używają serwera proxy odnajdywania można pobrać informacji o dostępnych usługach. Gdy klient wyszukuje usługa go wysyła `Probe` wiadomość do serwera proxy odnajdywania i serwer proxy Określa, czy spełniają dowolnej usługi bez informacji o usługa korzysta z klienta. W przypadku dopasowania wysyła serwera proxy odnajdywania `ProbeMatch` odpowiedź z powrotem do klienta. Klient może, skontaktuj się z usługi bezpośrednio przy użyciu usługi informacje zwrócone z serwera proxy. Zasady kluczy za zarządzany tryb jest, że żądań odnajdywania są wysyłane w sposób emisji pojedynczej na jeden urząd, serwera proxy odnajdywania. .NET Framework zawiera najważniejsze składniki, które pozwalają na tworzenie własnego serwera proxy. Klienci i usługi mogą zlokalizować serwer proxy przy użyciu wielu metod:  
  
-   Serwer proxy mogą odpowiadać na komunikaty ad hoc.  
  
-   Serwer proxy może wysyłać wiadomości ogłoszenie podczas uruchamiania.  
  
-   Klienci i usługi mogą być napisane do wyszukiwania określonego dobrze znanego punktu końcowego.  
  
 W trybie Ad-Hoc nie ma żadnych centralny serwer. Wszystkie komunikaty odnajdywania, takie jak Anonse usługi i żądania klientów są wysyłane w sposób multiemisji. Domyślnie .NET Framework obsługuje odnajdywania Ad-Hoc za pośrednictwem protokołu UDP. Na przykład jeśli usługa jest skonfigurowana do wysyłania anons Hello przy uruchamianiu, wysyła je za pośrednictwem adresu dobrze znanej i multiemisji przy użyciu protokołu UDP. Klienci będą musieli aktywnie nasłuchuje ogłoszenia i odpowiednio je przetwarzać. Gdy klient wysyła `Probe` wiadomości usługi są wysyłane za pośrednictwem sieci przy użyciu multiemisji protokołu. Każda usługa, która odbiera żądanie określa, czy jest zgodna z kryteriami `Probe` komunikat i odpowiada bezpośrednio do klienta z `ProbeMatch` komunikat, jeśli usługa spełnia kryteria określone we `Probe` wiadomości.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Korzyści z używania odnajdywanie w programie WCF  
 Ponieważ odnajdywanie w programie WCF jest implementowany przy użyciu protokołu WS Discovery jest współpracujący z innych klientów, usług i serwerów proxy, które również implementują protokołu WS Discovery. Odnajdywanie w programie WCF jest utworzonych na podstawie istniejących API WCF, która ułatwia dodawanie funkcji odnajdywania do istniejących usług i klientów. Odnajdowanie usługi można łatwo dodawać za pośrednictwem ustawień konfiguracji aplikacji. Ponadto odnajdywania WCF obsługuje również, przy użyciu protokołu odnajdowania przez inne transportu, takich jak elementu równorzędnego sieci nakładki nazewnictwa i HTTP. Odnajdywanie w programie WCF zapewnia obsługę zarządzany tryb działania serwera proxy odnajdywania jest używane w sytuacji. Może to zmniejszyć ruch sieciowy, ponieważ komunikaty są wysyłane bezpośrednio do serwera proxy odnajdywania, zamiast wysyłać komunikaty multiemisji do całej sieci. Odnajdywanie w programie WCF umożliwia również większą elastyczność podczas pracy z usługami sieci Web. Na przykład możesz zmienić adres usługi bez konieczności ponownie skonfigurować klienta lub usługi. Gdy klient musi uzyskać dostęp do usługi, które pozwala na wydawanie `Probe` komunikatu za pośrednictwem `Find` żądania i oczekiwać, że usługa reagować z jego bieżącym adresem. Odnajdywanie w programie WCF umożliwia wyszukiwanie usługi na podstawie różnych kryteriów, takich jak typy kontraktu, elementy powiązania, przestrzeni nazw, zakres oraz słowa kluczowe i numery wersji klienta. Odnajdywanie w programie WCF umożliwia wykrywanie w czasie środowiska uruchomieniowego i projektowania. Dodawanie odnajdywania aplikacji może służyć do włączyć inne scenariusze, takie jak odporność na uszkodzenia i automatyczną konfigurację.  
  
## <a name="service-publication"></a>Publikowania usług  
 Aby stał się wykrywalny, usługa <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musi zostać dodany host usługi i odnajdywanie punktu końcowego musi zostać dodany do określenia miejsca nasłuchiwać komunikatów odnajdywania. Poniższy przykład kodu pokazuje, jak usługa Self-Hosted można modyfikować, aby stał się wykrywalny.  
  
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
  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie musi zostać dodany do usługi jako wykrywalne opisu usługi. A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienia muszą zostać dodane do hosta usługi, aby skonfigurować usługę miejsce do nasłuchiwania żądań odnajdywania. W tym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (który jest tworzony na podstawie <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) jest dodawany do określenia, czy usługa powinna nasłuchiwać żądań odnajdywania za pośrednictwem protokołu UDP transportu multiemisji. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Służy do odnajdowania Ad-Hoc, ponieważ wszystkie komunikaty są wysyłane w sposób multiemisji.  
  
## <a name="announcement"></a>Ogłoszenie  
 Domyślnie publikowania usług nie wysłał wiadomości anonsów. Usługa musi być skonfigurowana do wysyłania wiadomości, ogłoszenia. To zapewnia większą elastyczność dla modułów zapisujących usługi, ponieważ ich poinformować o usługę, niezależnie od nasłuchiwać komunikatów odnajdywania. Ogłoszenie usługi również może służyć jako mechanizm służący do rejestrowania usług przy użyciu serwera proxy odnajdywania lub innych rejestrów usługi. Poniższy kod przedstawia sposób konfigurowania usługi do wysłania komunikatów Anons z powiązania protokołu UDP.  
  
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
 Aplikacja kliencka może używać <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, aby odnaleźć usług. Deweloper tworzy wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClient> klasę, która przekazuje do punktu końcowego wykrywania, która określa, gdzie wysyłać `Probe` lub `Resolve` wiadomości. Klient następnie wywołuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , który określa kryteria wyszukiwania, w ramach <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia. Jeśli zostaną znalezione usługi zgodne, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> zwraca kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Poniższy kod przedstawia sposób wywołania `Find` metody a następnie nawiązać połączenie z usługą odnalezione.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Odnajdywanie i zabezpieczenia na poziomie komunikatu  
 Korzystając z zabezpieczeń na poziomie komunikatu jest to konieczne określić <xref:System.ServiceModel.EndpointIdentity> na punkt końcowy odnajdowania usługi i pasującą <xref:System.ServiceModel.EndpointIdentity> na punkt końcowy odnajdywania klienta. Aby uzyskać więcej informacji na temat zabezpieczeń na poziomie komunikatu zobacz [zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Usługi hostowane w sieci Web i odnajdywania  
 Aby usług WCF pod być wykrywalne musi być uruchomiona. Usługi WCF hostowanej przez usługi IIS i WAS nie uruchamiaj aż do usług IIS / WAS odbiera komunikat powiązane usługi, dlatego nie może być wykrywalny domyślnie.  Dostępne są dwie opcje składania wykrywalny usługi hostowane w sieci Web:  
  
1.  Użyj funkcji systemu Windows Server AppFabric automatycznego uruchamiania  
  
2.  Komunikować się w imieniu usługi za pomocą serwera proxy odnajdywania  
  
 Windows Server AppFabric ma funkcję automatycznego uruchamiania, która umożliwi usługi do uruchomienia przed odbierał komunikaty. Auto-Start zestawu usług IIS / WAS hostowanej usługi można skonfigurować jako wykrywalne. Aby uzyskać więcej informacji na temat automatycznego uruchamiania funkcji, zobacz [systemu Windows Server AppFabric Auto-Start funkcji](https://go.microsoft.com/fwlink/?LinkId=205545). Wraz z włączając funkcję automatycznego uruchamiania, należy skonfigurować usługę odnajdywania. Aby uzyskać więcej informacji, zobacz [instrukcje: programowe Dodawanie możliwości odnajdywania do usługi i klienta WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Konfigurowanie odnajdywania w pliku konfiguracyjnym](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Serwera proxy odnajdywania może służyć do komunikowania się w imieniu usługi WCF, gdy usługa nie jest uruchomiona. Serwer proxy może nasłuchiwać sondy lub rozwiązać wiadomości i odpowiadać na klienta. Klient następnie może wysyłać wiadomości bezpośrednio do usługi. Gdy klient wysyła komunikat do usługi zostanie utworzone wystąpienie odpowiedzieć na wiadomość. Aby uzyskać więcej informacji o implementowaniu odnajdywania serwera proxy, zobacz temat [Implementowanie serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  Do odnajdywania WCF działała prawidłowo wszystkie karty sieciowe (kontrolera interfejsu sieciowego) powinien mieć tylko 1 adres IP.
