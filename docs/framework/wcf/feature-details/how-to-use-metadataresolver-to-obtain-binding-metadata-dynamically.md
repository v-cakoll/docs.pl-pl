---
title: 'Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 98fe4977f270b008c51039af19261ca86b8d6642
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601130"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Instrukcje: Dynamiczne uzyskiwanie metadanych powiązania przy użyciu klasy MetadataResolver
W tym temacie pokazano, jak używać <xref:System.ServiceModel.Description.MetadataResolver> klasy do dynamicznego uzyskiwania metadanych powiązań.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Aby dynamicznie uzyskać metadane powiązania  
  
1. Utwórz <xref:System.ServiceModel.EndpointAddress> obiekt z adresem punktu końcowego metadanych.  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Wywołanie <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29> , które przekazuje typ usługi i adres punktu końcowego metadanych. Zwraca kolekcję punktów końcowych, które implementują określony kontrakt. Tylko informacje o powiązaniu są importowane z metadanych; Informacje o kontrakcie nie zostały zaimportowane. Zamiast tego użyto dostarczonej umowy.  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Następnie można wykonać iterację kolekcji punktów końcowych usługi w celu wyodrębnienia potrzebnych informacji o powiązaniach. Poniższy kod wykonuje iterację punktów końcowych, tworzy obiekt klienta usługi, który przekazuje powiązanie i adres skojarzony z bieżącym punktem końcowym, a następnie wywołuje metodę w usłudze.  
  
    ```csharp  
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

- [Metadane](metadata.md)
