---
title: Przykład serwera proxy odnajdywania
ms.date: 03/30/2017
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
ms.openlocfilehash: 6fc0680bc6b61a6fe1b4b141c8b1e5081df5a124
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180400"
---
# <a name="discovery-proxy-sample"></a>Przykład serwera proxy odnajdywania
Niniejszy przykład pokazuje, jak utworzyć wdrożenia serwera proxy odnajdywania do przechowywania informacji o istniejących usług i jak klienci mogą wysyłać zapytania tego serwera proxy, aby uzyskać informacje. Ten przykład obejmuje trzy projekty:  
  
-   **Usługa**: prostą usługę kalkulatora usług Windows Communication Foundation (WCF), który rejestruje się za pomocą serwera proxy odnajdywania.  
  
-   **Serwera Proxy odnajdywania**: implementacja usługi serwera proxy odnajdywania.  
  
-   **Klient**: aplikacja kliencka usługi WCF, która wymaga serwera proxy odnajdywania do wyszukiwania usługi.  
  
## <a name="demonstrates"></a>Demonstracje  
 Implementacja serwera proxy odnajdywania  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 W `Main` metody części pliku Program.cs, przykład pokazuje, w jaki sposób usługa typu <xref:System.ServiceModel.Discovery.DiscoveryProxy> jest obsługiwana. Udostępnia dwa punkty końcowe, które typ <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> , a drugi typ <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Zarówno punkty końcowe Użyj protokołu TCP jako transportu. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Nasłuchuje na określony przez identyfikator URI `probeEndpointAddress` parametr, jest to, gdzie klienci mogą wysyłać wiadomości sondujące kwerendy serwera proxy dla swoich danych. <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Nasłuchuje na określony przez identyfikator URI `announcementEndpointAddress` parametru. Jest to, gdzie serwer proxy nasłuchuje zapowiedzi. Po otrzymaniu zawiadomienia online serwer proxy dodaje usługę do pamięci podręcznej, a po otrzymaniu zawiadomienia w trybie offline spowoduje usunięcie usługi z pamięci podręcznej.  
  
 DiscoveryProxy.cs zawiera implementację <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Serwer Proxy musi dziedziczyć <xref:System.Object> klasy i wymaga wykonania <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Przy konkretyzacji, tworzy nowy serwer Proxy <xref:System.Collections.Generic.Dictionary%602>, która jest używana do przechowywania elementów dysponuje informacjami.  
  
 Plik jest podzielony na dwa regiony metody pamięci podręcznej serwera Proxy i wdrożenia serwera Proxy odnajdywania. Region metody pamięci podręcznej serwera Proxy zawiera metody używane do aktualizowania <xref:System.Collections.Generic.Dictionary%602>, wykonywania zapytań względem <xref:System.Collections.Generic.Dictionary%602>i drukowanie danych dla użytkowników. Region wdrożenia serwera Proxy odnajdywania zawiera przesłonięte metody wymagane dla funkcji anonsu i badania. Określają one akcje wykonywane przez serwer proxy po otrzymaniu zawiadomienia Online, anons w trybie Offline lub wiadomości sondy.  
  
## <a name="service"></a>Usługa  
 W pliku Program.cs w projekcie usługi tego samego identyfikatora URI jest używany dla punktu końcowego ogłoszenie jako serwera proxy odnajdywania. Jest to spowodowane usługa korzysta z punktu końcowego do wysyłania anonsów, podczas gdy serwer proxy używa go do ich odbierania. Używa usługi <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> i dodaje punkt końcowy anonsu.  
  
## <a name="client"></a>Klient  
 Projekt klienta używa tego samego identyfikatora URI dla punktu końcowego sondy jako Agent Proxy. Jest to spowodowane sondy w tym scenariuszu są również emisji pojedynczej specjalnie do punktu końcowego, które są dostępne na serwerze proxy. Klient łączy się tego dobrze znanego adresu, a następnie wykonuje zapytanie usługi. Po odnalezieniu usługi, który nawiązuje z nim połączenie.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załaduj projekt rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i skompiluj projekt.  
  
2.  Najpierw uruchom aplikację serwera Proxy odnajdywania, wygenerowane w \DiscoveryProxy\bin\debug [katalog podstawowy rozwiązania]. Serwera Proxy odnajdywania należy najpierw uruchomić, ponieważ punkty końcowe TCP i ogłoszenie musi znajdować się dla usługi by wysłać swoich anonsów.  
  
3.  Po drugie Uruchom aplikację usługi, wygenerowane w \Service\bin\debug [katalog podstawowy rozwiązania]. Podczas rozruchu usługa wysyła powiadomienia do anonsowania punktu końcowego serwera proxy odnajdywania i jest zarejestrowany w pamięci podręcznej serwera proxy.  
  
4.  Następnie uruchom aplikację kliencką, wygenerowane w \Client\bin\debug [katalog podstawowy rozwiązania]. Klient wysyła zapytanie serwera proxy, pobiera adres usługi i następnie łączy się z usługą.  
  
5.  Na koniec zakończyć klienta, usługę i następnie serwera proxy. Serwer proxy musi działać dla jej otrzymywanie usługi anonsu w trybie offline.  
  
## <a name="see-also"></a>Zobacz też
