---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501052"
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
W tym przykładzie pokazano, jak można wstawić niestandardowych metadanych XML do odnajdowania metadanych dla punktu końcowego wykrywalny udostępnianych przez usługę. Przykładowe następnie przedstawiono, jak wyszukać usługę klienta i wyodrębnić te niestandardowe dane. W tym przykładzie składa się z dwóch projektów, usług i klientów.  
  
## <a name="service"></a>Usługa  
 W `main` metody próbki wskazuje, że obiekt typu <xref:System.Xml.Linq.XElement> jest wypełniana wymagane pola i jest dodawany do <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> jest dodawany do danego punktu końcowego. Gdy tego punktu końcowego zostanie wykryta, metadane odnajdywania zawiera niestandardowych danych, które zostały dodane w tym miejscu.  
  
## <a name="client"></a>Klient  
 Pokazuje przykładowe <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> wywołana metoda <xref:System.ServiceModel.Discovery.DiscoveryClient>. Powstałe w ten sposób <xref:System.ServiceModel.Discovery.FindResponse> następnie zostanie zapytany o odpowiednie i oczekiwanych elementów XML. Te elementy są następnie podane w konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załadowanie projektu rozwiązania w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i skompilować projekt.  
  
2.  Najpierw uruchomić aplikację usługi, generowane w \service\bin\debug [katalogu podstawowego rozwiązania], a następnie uruchomić aplikacji klienckiej, generowane w \Client\bin\debug [katalogu podstawowego rozwiązania]  
  
3.  Należy pamiętać, że usługa jest dostępna online klienta lokalizuje usługę i wyświetla metadane opublikowany w punkcie końcowym.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Zobacz też
