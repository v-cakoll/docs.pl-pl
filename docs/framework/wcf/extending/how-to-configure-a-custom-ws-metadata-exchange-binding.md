---
title: 'Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 0596e91204a2a9dbaed2fdbe85387ec3785fd3db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488702"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Instrukcje: Konfigurowanie niestandardowego powiązania WS-Metadata Exchange
W tym temacie będzie wyjaśniają sposób konfigurowania niestandardowych WS-Metadata exchange powiązania. Windows Communication Foundation (WCF) zawiera cztery powiązania zdefiniowane przez system metadanych, ale można opublikować metadanych za pomocą żadnego powiązania, które mają. W tym temacie opisano sposób publikowania metadanych za pomocą `wsHttpBinding`. To powiązanie daje możliwość udostępnia metadane w bezpieczny sposób. Kod w tym artykule jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Użycie pliku konfiguracji  
  
1.  W pliku konfiguracji usługi, dodać zachowanie usługi, który zawiera `serviceMetadata` tagu:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Dodaj `behaviorConfiguration` atrybut do tagu usługi, który odwołuje się do tego nowe zachowanie:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  Dodawanie punktu końcowego metadanych Określanie mex jako adres, `wsHttpBinding` jako powiązanie, i <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  Aby sprawdzić, czy punkt końcowy wymiany metadanych jest pracy poprawnie dodać tag końcowy w pliku konfiguracji klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, ustaw jej <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołania <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonać iterację kolekcji metadane zwrócony:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Konfigurowanie przez kod  
  
1.  Utwórz <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> wystąpienie obiektu binding:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  Dodaj punkt końcowy usługi i Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  Dodaj punkt końcowy wymiany metadanych, określając <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> utworzony wcześniej:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  Aby sprawdzić, czy punkt końcowy wymiany metadanych działa prawidłowo, należy dodać tag końcowy w pliku konfiguracji klienta:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  W metodzie Main() klienta, Utwórz nową <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, należy ustawić <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> właściwości `true`, wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> , a następnie wykonać iterację kolekcji metadane zwrócony:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Zachowanie publikowania metadanych](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [Pobieranie metadanych](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Publikowanie punktów końcowych metadanych](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
