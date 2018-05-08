---
title: 'Instrukcje: Pobieranie metadanych przez powiązanie inne niż wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 198c343aa6f25d55e518990dc1dbd2667a8c17ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Instrukcje: Pobieranie metadanych przez powiązanie inne niż wymiany metadanych
W tym temacie opisano, jak pobrać metadanych z punktu końcowego MEX za pośrednictwem powiązania-MEX. Kod w tym przykładzie jest oparta na [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) próbki.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Do pobierania metadanych za pośrednictwem powiązania-MEX  
  
1.  Określ powiązanie używane przez punkt końcowy MEX. Dla usług Windows Communication Foundation (WCF) można określić powiązanie MEX uzyskując dostęp do pliku konfiguracji usługi. W takim przypadku powiązania MEX. jest zdefiniowany w następującej konfiguracji usługi.  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2.  W pliku konfiguracji klienta należy skonfigurować to samo powiązanie niestandardowe. Tutaj również definiuje klienta `clientCredentials` zachowanie w celu zapewnienia certyfikatu służącego do uwierzytelniania w usłudze, gdy żąda metadanych z punktu końcowego MEX. Za pomocą Svcutil.exe żądanie metadanych przez powiązanie niestandardowych, konfiguracji punktu końcowego MEX należy dodać do pliku konfiguracji dla Svcutil.exe (Svcutil.exe.config), a nazwa konfiguracji punktu końcowego powinien być zgodny schemat identyfikatora URI adresu końcowy MEX, jak pokazano w poniższym kodzie.  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>    
    </system.serviceModel>  
    ```  
  
3.  Utwórz `MetadataExchangeClient` i Wywołaj `GetMetadata`. Istnieją dwa sposoby, w tym celu: można określić niestandardowego powiązania w konfiguracji, lub można określić niestandardowego powiązania w kodzie, jak pokazano w poniższym przykładzie.  
  
    ```  
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4.  Utwórz `WsdlImporter` i Wywołaj `ImportAllEndpoints`, jak pokazano w poniższym kodzie.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5.  W tym momencie masz kolekcję punktów końcowych usługi. Aby uzyskać więcej informacji na temat importowania metadanych, zobacz [porady: Importowanie metadanych do punktów końcowych usług](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
