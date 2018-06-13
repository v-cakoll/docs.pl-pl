---
title: 'Instrukcje: Pobieranie metadanych przez powiązanie inne niż wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 198c343aa6f25d55e518990dc1dbd2667a8c17ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488091"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="92147-102">Instrukcje: Pobieranie metadanych przez powiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="92147-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="92147-103">W tym temacie opisano, jak pobrać metadanych z punktu końcowego MEX za pośrednictwem powiązania-MEX.</span><span class="sxs-lookup"><span data-stu-id="92147-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="92147-104">Kod w tym przykładzie jest oparta na [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="92147-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="92147-105">Do pobierania metadanych za pośrednictwem powiązania-MEX</span><span class="sxs-lookup"><span data-stu-id="92147-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1.  <span data-ttu-id="92147-106">Określ powiązanie używane przez punkt końcowy MEX.</span><span class="sxs-lookup"><span data-stu-id="92147-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="92147-107">Dla usług Windows Communication Foundation (WCF) można określić powiązanie MEX uzyskując dostęp do pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="92147-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="92147-108">W takim przypadku powiązania MEX. jest zdefiniowany w następującej konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="92147-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2.  <span data-ttu-id="92147-109">W pliku konfiguracji klienta należy skonfigurować to samo powiązanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="92147-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="92147-110">Tutaj również definiuje klienta `clientCredentials` zachowanie w celu zapewnienia certyfikatu służącego do uwierzytelniania w usłudze, gdy żąda metadanych z punktu końcowego MEX.</span><span class="sxs-lookup"><span data-stu-id="92147-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="92147-111">Za pomocą Svcutil.exe żądanie metadanych przez powiązanie niestandardowych, konfiguracji punktu końcowego MEX należy dodać do pliku konfiguracji dla Svcutil.exe (Svcutil.exe.config), a nazwa konfiguracji punktu końcowego powinien być zgodny schemat identyfikatora URI adresu końcowy MEX, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="92147-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3.  <span data-ttu-id="92147-112">Utwórz `MetadataExchangeClient` i Wywołaj `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="92147-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="92147-113">Istnieją dwa sposoby, w tym celu: można określić niestandardowego powiązania w konfiguracji, lub można określić niestandardowego powiązania w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92147-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="92147-114">Utwórz `WsdlImporter` i Wywołaj `ImportAllEndpoints`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="92147-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5.  <span data-ttu-id="92147-115">W tym momencie masz kolekcję punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="92147-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="92147-116">Aby uzyskać więcej informacji na temat importowania metadanych, zobacz [porady: Importowanie metadanych do punktów końcowych usług](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="92147-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92147-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92147-117">See Also</span></span>  
 [<span data-ttu-id="92147-118">Metadane</span><span class="sxs-lookup"><span data-stu-id="92147-118">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
