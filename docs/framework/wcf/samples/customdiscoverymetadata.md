---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525424"
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Ten przykład pokazuje, jak wstawianie niestandardowych metadanych XML metadanych odnajdywania dla punktu końcowego wykrywalny udostępnianych przez usługę. Przykład następnie pokazano, jak wyszukać usługę klienta i wyodrębniania danych z tego niestandardowego. W tym przykładzie składa się z dwóch projektów, usługi i klienta.  
  
## <a name="service"></a>Usługa  
 W `main` metody przykład pokazuje, że obiekt typu <xref:System.Xml.Linq.XElement> jest wypełniana przy użyciu żądane pola i jest dodawany do <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. To <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zostanie dodany do określonego punktu końcowego. Po odnalezieniu tego punktu końcowego metadanych odnajdywania zawiera danych niestandardowych, który został dodany tutaj.  
  
## <a name="client"></a>Klient  
 Przedstawia przykładowe <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metody wywoływane na <xref:System.ServiceModel.Discovery.DiscoveryClient>. Wartość wynikowa <xref:System.ServiceModel.Discovery.FindResponse> następnie zostaje przesłane zapytanie dla elementów XML odpowiednie i oczekiwane. Elementy te są następnie drukowane w konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załaduj projekt rozwiązanie w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i skompiluj projekt.  
  
2.  Pierwsze uruchomienie aplikacji usługi generowane w \service\bin\debug [katalog podstawowy rozwiązania] i następnie uruchom aplikację klienta, wygenerowane w \Client\bin\debug [katalog podstawowy rozwiązania]  
  
3.  Należy pamiętać, że usługa przejściu do trybu online klienta lokalizuje usługę i wyświetla metadane, opublikowane w punkcie końcowym.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Zobacz też
