---
title: 'Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: d8efe2522d17829cc42d8ed1304983f6da46fb58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111205"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver
W tym temacie dowiesz się, jak używać <xref:System.ServiceModel.Description.MetadataResolver> klasy dynamiczne uzyskiwanie metadanych powiązania.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Aby dynamiczne uzyskiwanie metadanych powiązania  
  
1.  Utwórz <xref:System.ServiceModel.EndpointAddress> obiektu przy użyciu adresu punktu końcowego metadanych.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Wywołaj <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, która przekazuje typ usługi i adres punktu końcowego metadanych. Spowoduje to zwrócenie kolekcją punktów końcowych, które implementują określonej umowy. Tylko informacje o powiązaniu została zaimportowana z metadanych; informacje na temat Umowy nie zostanie zaimportowany. Podany kontraktu jest używana zamiast tego.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Następnie można wykonać iterację kolekcji punktów końcowych usługi, aby wyodrębnić informacje o powiązaniu, które są potrzebne. Poniższy kod wykonuje iterację przez punkty końcowe, tworzy obiekt klienta usługi, który przekazuje powiązania oraz adres skojarzony z bieżącym punktem końcowym i następnie wywołuje metodę dla usługi.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
