---
title: "Przykład serwera proxy odnajdywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b6e24c72002c7eef0e03af18f43992cc93b1d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-proxy-sample"></a>Przykład serwera proxy odnajdywania
W tym przykładzie pokazano, jak utworzyć wdrożenia serwera proxy odnajdywania do przechowywania informacji o istniejących usług i jak klienci mogą wykonywać kwerendę czy serwera proxy, aby uzyskać informacje. Ten przykład zawiera trzy projekty:  
  
-   **Usługa**: prosty [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kalkulator usługa, która rejestruje się przy użyciu serwera proxy odnajdywania.  
  
-   **Serwera Proxy odnajdywania**: implementacja usługi serwera proxy odnajdywania.  
  
-   **Klient**: A WCF aplikacji klienckiej, która wymaga usługi serwera proxy odnajdywania do wyszukiwania.  
  
## <a name="demonstrates"></a>Demonstracje  
 Implementacja serwera proxy odnajdywania  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>Obiektu DiscoveryProxy  
 W `Main` metody pliku Program.cs przykładzie przedstawiono sposób usługa typu <xref:System.ServiceModel.Discovery.DiscoveryProxy> jest obsługiwana. Udostępnia ona dwa punkty końcowe, jednego z typów <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> i innego typu <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Oba punkty końcowe użycia TCP jako transportu. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Prowadzi nasłuchiwanie na określony przez identyfikator URI `probeEndpointAddress` parametru, jest to, gdzie klienci mogą wysyłać wiadomości sondy do badania serwera proxy danych. <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Prowadzi nasłuchiwanie na określony przez identyfikator URI `announcementEndpointAddress` parametru. Jest to, gdy serwer proxy nasłuchuje dla anonsów. Po otrzymaniu powiadomienia online proxy dodaje usługę do pamięci podręcznej i po otrzymaniu powiadomienia w trybie offline Usuwa usługę z pamięci podręcznej.  
  
 DiscoveryProxy.cs zawiera implementację <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Serwer Proxy musi dziedziczyć z <xref:System.Object> klasy i wymaga wykonania <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Przy tworzeniu wystąpienia, tworzy nowy serwer Proxy <xref:System.Collections.Generic.Dictionary%602>, która jest używana do przechowywania elementów bez informacji o.  
  
 Plik jest podzielony na dwa obszary, serwer Proxy pamięci podręcznej metod i wdrażania serwera Proxy odnajdywania. Region metody pamięci podręcznej serwera Proxy zawiera metody używane do aktualizowania <xref:System.Collections.Generic.Dictionary%602>, wykonywać zapytania względem <xref:System.Collections.Generic.Dictionary%602>i wydrukować dane użytkowników. Region wdrożenia serwera Proxy odnajdywania zawiera przesłonięte metody wymagane dla funkcji anons i badania. Określają one akcje wykonywane przez serwer proxy po otrzymaniu powiadomienia Online, anons w trybie Offline lub wiadomości sondy.  
  
## <a name="service"></a>Usługa  
 W pliku Program.cs w projekcie usługi ten sam identyfikator URI jest używane dla punktu końcowego powiadomienia jako serwera proxy odnajdywania. Jest to spowodowane usługa używa punktu końcowego do wysyłania anonsów, gdy serwer proxy używa go do ich odbierania. Używane przez usługę <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> i dodaje punkt końcowy powiadomienia.  
  
## <a name="client"></a>Klient  
 Projekt klienta używa tego samego identyfikatora URI dla punktu końcowego sondowania jako serwer Proxy. Jest to spowodowane sond w tym scenariuszu są również emisji pojedynczej specjalnie do punktu końcowego, które są dostępne na serwerze proxy. Klient łączy się to dobrze znanego adresu, a następnie wysyła zapytanie do usługi. Po odnalezieniu usługi, który nawiązuje z nim połączenie.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załadowanie projektu rozwiązania w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i skompilować projekt.  
  
2.  Najpierw uruchom aplikację serwera Proxy odnajdywania, generowane w \DiscoveryProxy\bin\debug [katalogu podstawowego rozwiązania]. Serwera Proxy odnajdywania muszą najpierw uruchomić, ponieważ punkty końcowe TCP i anonsu musi mieć konto usługi do wysyłania swoich anonsów.  
  
3.  Po drugie Uruchom aplikację usługi wygenerowanych w \Service\bin\debug [katalogu podstawowego rozwiązania]. Podczas rozruchu usługa wysyła powiadomienia do punktu końcowego powiadomienia odnajdowania serwera proxy i jest zarejestrowana w pamięci podręcznej serwera proxy.  
  
4.  Uruchom aplikację klienta, generowane w \Client\bin\debug [katalogu podstawowego rozwiązania]. Klient wysyła zapytanie do serwera proxy, pobiera adres usługi i następnie łączy się z usługą.  
  
5.  Ponadto przerwanie klienta, usługę, a następnie serwer proxy. Serwer proxy musi być uruchomiona, aby otrzymywać powiadomienia w trybie offline usługi.  
  
## <a name="see-also"></a>Zobacz też
