---
title: "Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab95212d0f7b57b2bc076bed862b3d07c3c93df9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver
W tym temacie przedstawiono sposób użycia <xref:System.ServiceModel.Description.MetadataResolver> klasy dynamiczne uzyskiwanie metadanych powiązania.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Aby dynamiczne uzyskiwanie metadanych powiązania  
  
1.  Utwórz <xref:System.ServiceModel.EndpointAddress> obiektu adres punktu końcowego metadanych.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Wywołanie <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, która przechodzi w typu usługi i adres punktu końcowego metadanych. To zwraca kolekcję punktów końcowych, które implementuje kontrakt określony. Tylko informacje o powiązaniu została zaimportowana z metadanymi; kontrakt informacji nie zostanie zaimportowany. Zamiast niego jest używana dostarczony kontraktu.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Następnie można wykonać iterację kolekcji punktów końcowych usługi, aby wyodrębnić informacje o powiązaniu, które są potrzebne. Poniższy kod iteruje punkty końcowe, tworzy obiekt klienta usługi, który przekazuje powiązanie i adres skojarzony z bieżącym punktem końcowym i następnie wywołuje metodę dla usługi.  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
