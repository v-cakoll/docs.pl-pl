---
title: "Odnajdywanie usługi działającej w trybie unikatowego identyfikatora URI nasłuchiwania — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 017a14794dfb2cb2c49cc32df038600a984acf3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Odnajdywanie usługi działającej w trybie unikatowego identyfikatora URI nasłuchiwania — przykład
W tym przykładzie pokazano, jak odnajdywanie usługi, która ma <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> ustawioną właściwość <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Gdy <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Description.ListenUriMode.Unique>, zapewniony ListenUri być unikatowy, ustawiając portu unikatowa lub ścieżka, które mają być unikatowe przez dołączenie identyfikatora GUID.  
  
### <a name="features-on-the-service"></a>Funkcje usługi  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Ma ustawioną wartość właściwości <xref:System.ServiceModel.Description.ListenUriMode.Unique> dla punktu końcowego TCP. Usługa jest przeprowadzane wykrywalny przez <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punktu końcowego.  
  
### <a name="features-on-the-client"></a>Funkcje na kliencie  
 Ten klient nawiąże połączenie z usługą przy użyciu prawidłowego `Via.Uri` przy użyciu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody. <xref:System.ServiceModel.Discovery.FindResponse> Która jest zwracana z metody następnie zostanie zapytany o Określa, czy zawiera prawidłową <xref:System.ServiceModel.Endpoint.ListenUri%2A> i czy jest ona inna niż `Address.Uri`. Odpowiednie informacje są następnie przekazywane do `InvokeCalculatorService` metody. W `InvokeCalculatorService` metody, <xref:System.ServiceModel.Endpoint.ListenUri%2A> przekazany przez wywołującego, a następnie `ClientViaBehavior` z prawidłowym `Via.Uri` zostanie dodany do punktu końcowego klienta.  
  
##### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz UniqueListenUriMode.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Uruchamianie aplikacji usługi, która jest generowana w folderze \service\bin\debug [katalogu podstawowego rozwiązania].  
  
4.  Uruchom aplikację klienta, generowany w folderze \Client\bin\debug [katalogu podstawowego rozwiązania].  
  
     Klient lokalizuje uruchomionej usługi i zapisuje konsoli metadanych opublikowanych przez punkt końcowy usługi.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Zobacz też
