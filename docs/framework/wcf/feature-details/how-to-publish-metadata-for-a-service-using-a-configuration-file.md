---
title: 'Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 367ebeee5c12d809a758f1bee73dfaadda85788d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761458"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="e63d0-102">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e63d0-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="e63d0-103">Jest to jedna z dwóch tematy porad, które pokazują Publikowanie metadanych dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e63d0-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e63d0-104">Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="e63d0-105">W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e63d0-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e63d0-106">W tym temacie przedstawiono sposób Publikowanie metadanych w niezabezpieczony sposób.</span><span class="sxs-lookup"><span data-stu-id="e63d0-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="e63d0-107">Dowolny klient może pobierać metadanych z usługi.</span><span class="sxs-lookup"><span data-stu-id="e63d0-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="e63d0-108">Jeśli potrzebujesz usługi w celu publikowania metadanych w bezpieczny sposób, zobacz [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="e63d0-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="e63d0-109">Aby uzyskać więcej informacji na temat publikowania metadanych w kodzie, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="e63d0-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="e63d0-110">Publikowanie metadanych zezwala klientom na pobieranie metadanych za pomocą ROZPOCZYNANIE transferu WS żądania lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="e63d0-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="e63d0-111">Aby się upewnić, że kod działa, Utwórz podstawowej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e63d0-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="e63d0-112">Dla uproszczenia podstawowa usługa Self-Hosted znajduje się w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e63d0-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="e63d0-113">Ta usługa jest samodzielnie hostowana usługa, która została skonfigurowana przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e63d0-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="e63d0-114">Następujący plik konfiguracji, służy jako punkt wyjścia.</span><span class="sxs-lookup"><span data-stu-id="e63d0-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="e63d0-115">Publikowanie metadanych dla usługi WCF, za pomocą pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="e63d0-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="e63d0-116">W pliku App.config, po upływie `</services>` elementu, Utwórz `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="e63d0-117">W ramach `<behaviors>` elementu Dodawanie `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="e63d0-118">Dodaj `<behavior>` elementu `<serviceBehaviors>` elementu i określić wartość dla `name` atrybutu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="e63d0-119">Dodaj `<serviceMetadata>` elementu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="e63d0-120">Ustaw `httpGetEnabled` atrybutu `true` i `policyVersion` atrybutu Policy15.</span><span class="sxs-lookup"><span data-stu-id="e63d0-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="e63d0-121">`httpGetEnabled` Umożliwia usłudze odpowiadanie na żądania metadanych przez żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="e63d0-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="e63d0-122">`policyVersion` informuje usługę do odpowiadają WS-Policy w wersji 1.5 podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="e63d0-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="e63d0-123">Dodaj `behaviorConfiguration` atrybutu `<service>` elementu i określ `name` atrybutu `<behavior>` elementu dodany w kroku 1, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6. <span data-ttu-id="e63d0-124">Dodaj jeden lub kilka `<endpoint>` elementy z zamówienia równa `IMetadataExchange`, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e63d0-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7. <span data-ttu-id="e63d0-125">W przypadku punktów końcowych metadanych, dodane w poprzednim kroku, ustawić `binding` atrybut do jednego z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e63d0-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="e63d0-126">`mexHttpBinding` dla publikacji HTTP.</span><span class="sxs-lookup"><span data-stu-id="e63d0-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="e63d0-127">`mexHttpsBinding` dla publikacji protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e63d0-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="e63d0-128">`mexNamedPipeBinding` dla publikacji nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="e63d0-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="e63d0-129">`mexTcpBinding` dla publikacji TCP.</span><span class="sxs-lookup"><span data-stu-id="e63d0-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="e63d0-130">Dla punktów końcowych metadanych, dodane w poprzednim kroku należy ustawić adres równe:</span><span class="sxs-lookup"><span data-stu-id="e63d0-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="e63d0-131">Pusty ciąg do użycia jako punkt publikacji aplikacji hosta, adres podstawowy, jeśli podstawowy adres jest taki sam jak powiązanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="e63d0-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="e63d0-132">Adres względny Jeśli aplikacja hosta ma adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="e63d0-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="e63d0-133">Bezwzględny adres.</span><span class="sxs-lookup"><span data-stu-id="e63d0-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="e63d0-134">Skompiluj i uruchom aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="e63d0-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="e63d0-135">Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e63d0-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="e63d0-136">W przeciwnym razie komunikat wyświetlany w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."</span><span class="sxs-lookup"><span data-stu-id="e63d0-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="e63d0-137">Aby użyć domyślnych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="e63d0-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="e63d0-138">Aby skonfigurować usługę korzystającą z domyślnych punktów końcowych metadanych, określ <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w konfiguracji pliku co w poprzednim przykładzie, ale nie określono żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="e63d0-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="e63d0-139">Plik konfiguracji będzie następnie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="e63d0-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="e63d0-140">Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> z `httpGetEnabled` równa `true`, usługa ma Publikowanie metadanych włączone, a ponieważ punkty końcowe nie zostały jawnie dodane, środowiska uruchomieniowego dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="e63d0-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="e63d0-141">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e63d0-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e63d0-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="e63d0-142">Example</span></span>  
 <span data-ttu-id="e63d0-143">Poniższy przykład kodu pokazuje wdrażania podstawowej usługi WCF i pliku konfiguracji, która umożliwia publikowanie metadanych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="e63d0-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e63d0-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e63d0-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="e63d0-145">Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="e63d0-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="e63d0-146">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="e63d0-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="e63d0-147">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="e63d0-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="e63d0-148">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="e63d0-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="e63d0-149">Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="e63d0-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
