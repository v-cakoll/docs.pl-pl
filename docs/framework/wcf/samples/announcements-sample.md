---
title: Anonse — przykład
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: d03f22b7dd4d9886151e61a2a846f2dc64e661c3
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347522"
---
# <a name="announcements-sample"></a>Anonse — przykład
W tym przykładzie pokazano, jak korzystać z funkcji ogłoszenie funkcji odnajdywania. Anonse Zezwól usługom do wysłania komunikatów Anons, które zawierają metadane dotyczące usługi. Domyślnie ogłoszenie hello jest wysyłany podczas uruchamiania usługi i ogłoszenie bye jest wysyłana, gdy usługa kończy pracę. Anonse te mogą być multiemisji lub mogą być wysyłane point-to-point. W tym przykładzie składa się z dwóch projektów usługi i klienta.  
  
## <a name="service"></a>Usługa  
 Ten projekt zawiera Kalkulator samodzielnie hostowanej usługi. W `Main` metoda, host usługi jest tworzona i punkt końcowy usługi jest dodawany do niego. Następnie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> zostanie utworzony. Aby włączyć anonsów, punkt końcowy ogłoszenie musi zostać dodany do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. W tym przypadku standardowy punkt końcowy przy użyciu protokołu UDP multiemisji jest dodawany jako punkt końcowy anonsu. Emituje to anonsów, za pośrednictwem dobrze znanego adresu protokołu UDP.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Klient  
 W tym projekcie, należy pamiętać, że hosty klienta <xref:System.ServiceModel.Discovery.AnnouncementService>. Ponadto dwa delegaty są rejestrowane zdarzenia. Zdarzenia te określają, klient działanie po odebraniu anonsów online i offline.  
  
```csharp
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` i `OnOfflineEvent` metody obsługi komunikatów Anons hello i bye odpowiednio.  
  
```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  W tym przykładzie użyto punktów końcowych HTTP i przeprowadzić to przykład, odpowiednie listy ACL adresu URL muszą zostać dodane zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Aby uzyskać szczegółowe informacje. Wykonując następujące polecenie w podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL. Można zastąpić Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchom aplikację client.exe.  
  
4.  Uruchom aplikację service.exe. Należy zauważyć, że klient odbierze anonsu online.  
  
5.  Zamknij aplikację service.exe. Należy pamiętać, że klient otrzymuje powiadomienia w trybie offline.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>Zobacz też
