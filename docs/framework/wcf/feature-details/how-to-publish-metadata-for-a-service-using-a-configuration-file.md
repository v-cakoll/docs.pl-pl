---
title: 'Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 7ea0a2aa386f747b89f56f21d75a97e4409140a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184866"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="69639-102">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="69639-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="69639-103">Jest to jeden z dwóch tematów in how-to, które pokazują publikowania metadanych dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="69639-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="69639-104">Istnieją dwa sposoby określania sposobu publikowania metadanych przez usługę przy użyciu pliku konfiguracji i przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="69639-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="69639-105">W tym temacie pokazano, jak opublikować metadane dla usługi przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="69639-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="69639-106">W tym temacie pokazano, jak opublikować metadane w sposób niezabezpieczony.</span><span class="sxs-lookup"><span data-stu-id="69639-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="69639-107">Każdy klient może pobrać metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="69639-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="69639-108">Jeśli chcesz, aby usługa publikowała metadane w bezpieczny sposób, zobacz [Niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="69639-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="69639-109">Aby uzyskać więcej informacji na temat publikowania metadanych w kodzie, zobacz [Jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="69639-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="69639-110">Publikowanie metadanych umożliwia klientom pobieranie metadanych przy użyciu żądania GET transferu `?wsdl` WS lub żądania HTTP/GET przy użyciu ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="69639-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="69639-111">Aby upewnić się, że kod działa, należy utworzyć podstawową usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="69639-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="69639-112">Dla uproszczenia podstawowa usługa hostowana samodzielnie jest dostępna w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="69639-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="69639-113">Ta usługa jest usługą hostowana samodzielnie, która jest konfigurowana przy użyciu pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="69639-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="69639-114">Następujący plik konfiguracyjny służy jako punkt wyjścia.</span><span class="sxs-lookup"><span data-stu-id="69639-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="69639-115">Aby opublikować metadane usługi WCF przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="69639-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="69639-116">W pliku App.config, po `</services>` zamknięciu `<behaviors>` elementu, utwórz element.</span><span class="sxs-lookup"><span data-stu-id="69639-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="69639-117">W `<behaviors>` obrębie elementu `<serviceBehaviors>` dodaj element.</span><span class="sxs-lookup"><span data-stu-id="69639-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="69639-118">Dodaj `<behavior>` element do `<serviceBehaviors>` elementu i określ `name` wartość atrybutu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="69639-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="69639-119">Dodaj `<serviceMetadata>` element do `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="69639-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="69639-120">Ustaw `httpGetEnabled` atrybut `true` i `policyVersion` atrybut policy15.</span><span class="sxs-lookup"><span data-stu-id="69639-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="69639-121">`httpGetEnabled`umożliwia usłudze odpowiadanie na żądania metadanych wykonane przez żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="69639-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="69639-122">`policyVersion`informuje usługę, aby była zgodna z zasadą WS 1.5 podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="69639-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="69639-123">Dodaj `behaviorConfiguration` atrybut do `<service>` elementu i `name` określ atrybut `<behavior>` elementu dodanego w kroku 1, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="69639-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. <span data-ttu-id="69639-124">Dodaj jeden `<endpoint>` lub więcej elementów `IMetadataExchange`z zestawem kontraktu do , jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="69639-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. <span data-ttu-id="69639-125">W przypadku punktów końcowych metadanych dodanych `binding` w poprzednim kroku ustaw atrybut na jeden z następujących:</span><span class="sxs-lookup"><span data-stu-id="69639-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="69639-126">`mexHttpBinding`do publikacji HTTP.</span><span class="sxs-lookup"><span data-stu-id="69639-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="69639-127">`mexHttpsBinding`do publikacji HTTPS.</span><span class="sxs-lookup"><span data-stu-id="69639-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="69639-128">`mexNamedPipeBinding`dla nazwanego publikowania potoków.</span><span class="sxs-lookup"><span data-stu-id="69639-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="69639-129">`mexTcpBinding`do publikacji TCP.</span><span class="sxs-lookup"><span data-stu-id="69639-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="69639-130">Dla punktów końcowych metadanych dodanych w poprzednim kroku ustaw adres równy:</span><span class="sxs-lookup"><span data-stu-id="69639-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="69639-131">Pusty ciąg do używania adresu podstawowego aplikacji hosta jako punktu publikacji, jeśli adres podstawowy jest taki sam jak powiązanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="69639-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="69639-132">Adres względny, jeśli aplikacja hosta ma adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="69639-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="69639-133">Adres bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="69639-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="69639-134">Skompiluj i uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="69639-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="69639-135">Użyj programu Internet Explorer, aby przejść dohttp://localhost:8001/MetadataSample adresu podstawowego usługi (w tym przykładzie) i sprawdzić, czy publikowanie metadanych jest włączone.</span><span class="sxs-lookup"><span data-stu-id="69639-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="69639-136">Jeśli nie, w górnej części strony wynikowej zostanie wyświetlony komunikat: "Publikowanie metadanych dla tej usługi jest obecnie wyłączone".</span><span class="sxs-lookup"><span data-stu-id="69639-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="69639-137">Aby użyć domyślnych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="69639-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="69639-138">Aby skonfigurować metadane w usłudze, która używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior> domyślnych punktów końcowych, należy określić w pliku konfiguracyjnym, jak w poprzednim przykładzie, ale nie określać żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="69639-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="69639-139">Plik konfiguracyjny będzie wyglądać w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="69639-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="69639-140">Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> `httpGetEnabled` z zestawem do `true`, usługa ma włączone metadane publikowania, a ponieważ nie punkty końcowe zostały jawnie dodane, środowisko wykonawcze dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="69639-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="69639-141">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="69639-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69639-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="69639-142">Example</span></span>  
 <span data-ttu-id="69639-143">Poniższy przykład kodu przedstawia implementację podstawowej usługi WCF i pliku konfiguracji, który publikuje metadane dla usługi.</span><span class="sxs-lookup"><span data-stu-id="69639-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69639-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69639-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="69639-145">Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="69639-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="69639-146">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="69639-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="69639-147">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="69639-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="69639-148">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="69639-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="69639-149">Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="69639-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
