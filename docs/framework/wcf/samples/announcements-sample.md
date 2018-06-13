---
title: Anonse — przykład
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: ee58a2fef970fa3e7936e2fc26a9e7fd31633347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500041"
---
# <a name="announcements-sample"></a>Anonse — przykład
Ten przykład przedstawia sposób użycia anonsu działanie funkcji odnajdywania. Anonse Zezwalaj usługom do wysłania wiadomości anonsów, zawierające metadane dotyczące usługi. Domyślnie powiadomienia hello są wysyłane podczas uruchamiania usługi i anonsu bye są wysyłane podczas zamykania usługi. Anonse te mogą być multiemisji lub mogą być wysyłane point-to-point. W tym przykładzie obejmuje dwa projekty usługi i klienta.  
  
## <a name="service"></a>Usługa  
 Ten projekt zawiera usługi Kalkulator siebie. W `Main` metody, host usługi jest tworzony i punktu końcowego zostaną dodane do niego. Następnie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> jest tworzony. Aby włączyć anonsów, punkt końcowy powiadomienia musi zostać dodany do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. W takim przypadku standardowy punkt końcowy, za pomocą multiemisji UDP jest dodawana jako punktu końcowego powiadomienia. Anonsy to emituje za pośrednictwem dobrze znanego adresu protokołu UDP.  
  
```  
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
 W tym projekcie, należy pamiętać, że hosty klienta <xref:System.ServiceModel.Discovery.AnnouncementService>. Ponadto dwa obiekty delegowane są rejestrowane zdarzenia. Zdarzenia te określają, co klient nie w przypadku online i offline anonse są odbierane.  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` i `OnOfflineEvent` metody obsługi wiadomości anonsów hello i bye odpowiednio.  
  
```  
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
  
1.  W przykładzie użyto punktów końcowych HTTP i do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL muszą zostać dodane zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje. Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL. Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchom aplikację client.exe.  
  
4.  Uruchom aplikację service.exe. Należy zauważyć, że klient otrzymuje powiadomienia online.  
  
5.  Zamknij aplikację service.exe. Należy zauważyć, że klient otrzymuje powiadomienia w trybie offline.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>Zobacz też
