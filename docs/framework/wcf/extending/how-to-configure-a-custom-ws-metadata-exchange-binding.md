---
title: 'Instrukcje: konfigurowanie niestandardowego wiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851222"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Instrukcje: konfigurowanie niestandardowego wiązania WS-Metadata Exchange
W tym temacie opisano sposób konfigurowania niestandardowego powiązania usługi WS-Metadata Exchange. Windows Communication Foundation (WCF) obejmuje cztery zdefiniowane przez system powiązania metadanych, ale można opublikować metadane przy użyciu dowolnego powiązania. W `wsHttpBinding`tym temacie przedstawiono sposób publikowania metadanych przy użyciu. To powiązanie umożliwia bezpieczne udostępnianie metadanych. Kod w tym artykule jest oparty na [wprowadzenie](../samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Korzystanie z pliku konfiguracji  
  
1. W pliku konfiguracji usługi Dodaj zachowanie usługi, które zawiera `serviceMetadata` Tag:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. `behaviorConfiguration` Dodaj atrybut do tagu usługi, który odwołuje się do tego nowego zachowania:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Dodaj punkt końcowy metadanych określający MEX jako adres, `wsHttpBinding` jako powiązanie i <xref:System.ServiceModel.Description.IMetadataExchange> jako kontrakt:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, Dodaj tag punktu końcowego w pliku konfiguracji klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. W głównej <xref:System.ServiceModel.Description.MetadataExchangeClient> metodzie klienta Utwórz nowe wystąpienie, ustaw jego <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwość na `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonaj iterację w kolekcji zwróconych metadanych:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Konfigurowanie przez kod  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> powiązania:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <xref:System.ServiceModel.ServiceHost> Utwórz wystąpienie:  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Dodaj punkt końcowy wymiany metadanych, określając <xref:System.ServiceModel.WSHttpBinding> utworzony wcześniej:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, Dodaj tag punktu końcowego w pliku konfiguracji klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. W <xref:System.ServiceModel.Description.MetadataExchangeClient> głównej metodzie klienta Utwórz nowe wystąpienie, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> ustaw właściwość na `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonaj iterację w kolekcji zwróconych metadanych:  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zachowanie publikowania metadanych](../samples/metadata-publishing-behavior.md)
- [Pobieranie metadanych](../samples/retrieve-metadata.md)
- [Metadane](../feature-details/metadata.md)
- [Publikowanie metadanych](../feature-details/publishing-metadata.md)
- [Publikowanie punktów końcowych metadanych](../publishing-metadata-endpoints.md)
