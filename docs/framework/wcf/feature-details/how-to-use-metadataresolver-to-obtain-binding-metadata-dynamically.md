---
title: 'Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 3fe09699304de42ed00312f50f3b9e0edb20615d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047558"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver
W tym temacie dowiesz się, jak używać <xref:System.ServiceModel.Description.MetadataResolver> klasy dynamiczne uzyskiwanie metadanych powiązania.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Aby dynamiczne uzyskiwanie metadanych powiązania  
  
1. Utwórz <xref:System.ServiceModel.EndpointAddress> obiektu przy użyciu adresu punktu końcowego metadanych.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Wywołaj <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, która przekazuje typ usługi i adres punktu końcowego metadanych. Spowoduje to zwrócenie kolekcją punktów końcowych, które implementują określonej umowy. Tylko informacje o powiązaniu została zaimportowana z metadanych; informacje na temat Umowy nie zostanie zaimportowany. Podany kontraktu jest używana zamiast tego.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Następnie można wykonać iterację kolekcji punktów końcowych usługi, aby wyodrębnić informacje o powiązaniu, które są potrzebne. Poniższy kod wykonuje iterację przez punkty końcowe, tworzy obiekt klienta usługi, który przekazuje powiązania oraz adres skojarzony z bieżącym punktem końcowym i następnie wywołuje metodę dla usługi.  
  
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
