---
title: Odnajdywanie usługi działającej w trybie unikatowego identyfikatora URI nasłuchiwania — przykład
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: 7e1c5ae0cb1a44c72a27566035b4bc20acbf1614
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077047"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Odnajdywanie usługi działającej w trybie unikatowego identyfikatora URI nasłuchiwania — przykład
W tym przykładzie przedstawiono sposób odnajdowania usługi, która ma <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> właściwością <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Gdy <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, zapewniony ListenUri być unikatowy, ustawiając portu, aby była unikatowa lub ścieżki była unikatowa przez dołączenie identyfikatora GUID.  
  
### <a name="features-on-the-service"></a>Funkcje usługi  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Właściwość jest ustawiona na <xref:System.ServiceModel.Description.ListenUriMode.Unique> dla punktu końcowego TCP. Usługa jest następnie wykrywalne za pośrednictwem <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punktu końcowego.  
  
### <a name="features-on-the-client"></a>Funkcje na komputerze klienckim  
 Ten klient nawiąże połączenie z tą usługą przy użyciu prawidłowego `Via.Uri` przy użyciu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody. <xref:System.ServiceModel.Discovery.FindResponse> Zwrócone z metody następnie zostaje przesłane zapytanie do tego, czy zawiera prawidłową <xref:System.ServiceModel.Endpoint.ListenUri%2A> i czy jest on inny niż `Address.Uri`. Odpowiednie informacje są następnie przekazywane do `InvokeCalculatorService` metody. W `InvokeCalculatorService` metody <xref:System.ServiceModel.Endpoint.ListenUri%2A> została przekazana przez obiekt wywołujący, a następnie `ClientViaBehavior` z prawidłowymi `Via.Uri` jest dodawany do endpoint klienta.  
  
##### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz UniqueListenUriMode.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Uruchamianie aplikacji usługi, który jest generowany w folderze \service\bin\debug [katalog podstawowy rozwiązania].  
  
4.  Uruchom aplikację klienta, który jest generowany w folderze \Client\bin\debug [katalog podstawowy rozwiązania].  
  
     Klient lokalizuje uruchomionej usługi i zapisuje do konsoli metadanych opublikowanych przez punkt końcowy usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Zobacz też
