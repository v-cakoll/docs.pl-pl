---
title: 'Instrukcje: konfigurowanie niestandardowego wiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 51681e258e6a21b3a7ae604d1c0ef65d320bfb4f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311880"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Instrukcje: konfigurowanie niestandardowego wiązania WS-Metadata Exchange
W tym temacie wyjaśniono, jak skonfigurować niestandardowe protokołu WS-Metadata exchange powiązania. Windows Communication Foundation (WCF) zawiera cztery powiązania metadane zdefiniowane przez system, ale można opublikować za pomocą dowolnego powiązania, który ma metadanych. W tym temacie opisano, jak można opublikować za pomocą metadanych `wsHttpBinding`. To powiązanie zapewnia możliwość ujawnienia metadanych w bezpieczny sposób. Kod ten artykuł jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Korzystanie z pliku konfiguracji  
  
1. W pliku konfiguracji usługi, należy dodać zachowanie usługi, który zawiera `serviceMetadata` tag:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Dodaj `behaviorConfiguration` atrybut do tagu usługi, która odwołuje się to nowe zachowanie:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Dodawanie punktu końcowego metadanych, określając mex jako adres, `wsHttpBinding` używanego w powiązaniu i <xref:System.ServiceModel.Description.IMetadataExchange> jako umowy:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Aby sprawdzić, czy punkt końcowy wymiany metadanych jest pracy poprawnie dodać tag punktu końcowego w pliku konfiguracji klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, ustaw jego <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> i następnie iterację kolekcji metadanych zwróconych:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Skonfigurować przy użyciu kodu  
  
1. Utwórz <xref:System.ServiceModel.WSHttpBinding> wystąpienie obiektu binding:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Dodaj punkt końcowy wymiany metadanych, określając <xref:System.ServiceModel.WSHttpBinding> utworzony wcześniej:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Aby sprawdzić, czy punkt końcowy wymiany metadanych działa poprawnie, należy dodać tag punktu końcowego w pliku konfiguracji klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, należy ustawić <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> i następnie iterację kolekcji metadanych zwróconych:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zachowanie publikowania metadanych](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
- [Pobieranie metadanych](../../../../docs/framework/wcf/samples/retrieve-metadata.md)
- [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [Publikowanie punktów końcowych metadanych](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
