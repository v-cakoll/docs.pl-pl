---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b3272b642a04821d8343cae776e48f90d266cfe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Zobacz też
