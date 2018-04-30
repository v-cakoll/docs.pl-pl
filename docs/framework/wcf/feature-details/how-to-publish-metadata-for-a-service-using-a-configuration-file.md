---
title: 'Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d30031db590b424688cc0af6a573c1042099e64e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="16f6e-102">Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="16f6e-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="16f6e-103">Jest to jeden z dwóch tematy porad, które przedstawiają Publikowanie metadanych dla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="16f6e-103">This is one of two how-to topics that demonstrate publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="16f6e-104">Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i kod.</span><span class="sxs-lookup"><span data-stu-id="16f6e-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="16f6e-105">W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="16f6e-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="16f6e-106">W tym temacie pokazano, jak publikować metadane w sposób niezabezpieczonych.</span><span class="sxs-lookup"><span data-stu-id="16f6e-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="16f6e-107">Dowolny klient może pobrać metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="16f6e-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="16f6e-108">Jeśli potrzebujesz usługi publikować metadane w sposób bezpieczny, zobacz [niestandardowe bezpiecznego punktu końcowego metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="16f6e-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="16f6e-109">Aby uzyskać więcej informacji o publikowaniu metadanych w kodzie, zobacz [porady: Publikowanie metadanych dla kodu przy użyciu usługi](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="16f6e-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="16f6e-110">Publikowanie metadanych pozwala klientom na pobieranie metadanych za pomocą żądania GET usługi WS-Transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="16f6e-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="16f6e-111">Aby się upewnić, że działa kod, należy utworzyć basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="16f6e-111">To be sure that the code is working, create a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="16f6e-112">Dla uproszczenia podstawowej usługi hostowanej własnym znajduje się w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="16f6e-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="16f6e-113">Ta usługa jest samodzielnie hostowana usługa, która jest konfigurowana przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="16f6e-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="16f6e-114">Następujący plik konfiguracji służy jako punkt początkowy.</span><span class="sxs-lookup"><span data-stu-id="16f6e-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="16f6e-115">Publikowanie metadanych dla usługi WCF, przy użyciu pliku konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="16f6e-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="16f6e-116">W pliku App.config, po upływie `</services>` elementu, Utwórz `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="16f6e-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="16f6e-117">W ramach `<behaviors>` elementu, Dodaj `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="16f6e-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="16f6e-118">Dodaj `<behavior>` elementu `<serviceBehaviors>` element i określić wartość dla `name` atrybutu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="16f6e-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="16f6e-119">Dodaj `<serviceMetadata>` elementu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="16f6e-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="16f6e-120">Ustaw `httpGetEnabled` atrybutu `true` i `policyVersion` atrybutu Policy15.</span><span class="sxs-lookup"><span data-stu-id="16f6e-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="16f6e-121">`httpGetEnabled` Umożliwia usłudze odpowiadać na żądania metadanych przez żądanie HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="16f6e-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="16f6e-122">`policyVersion` Określa, że usługa odpowiadają WS-Policy 1.5 podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="16f6e-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="16f6e-123">Dodaj `behaviorConfiguration` atrybutu `<service>` element i określ `name` atrybutu `<behavior>` element dodanej w kroku 1, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="16f6e-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6.  <span data-ttu-id="16f6e-124">Dodaj jeden lub kilka `<endpoint>` ustawioną elementy z kontraktem `IMetadataExchange`, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="16f6e-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7.  <span data-ttu-id="16f6e-125">Punkty końcowe metadanych dodanym w poprzednim kroku, można ustawić `binding` atrybutu do jednej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="16f6e-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="16f6e-126">`mexHttpBinding` dla publikacji HTTP.</span><span class="sxs-lookup"><span data-stu-id="16f6e-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="16f6e-127">`mexHttpsBinding` dla publikacji HTTPS.</span><span class="sxs-lookup"><span data-stu-id="16f6e-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="16f6e-128">`mexNamedPipeBinding` dla publikacji nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="16f6e-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="16f6e-129">`mexTcpBinding` dla publikacji TCP.</span><span class="sxs-lookup"><span data-stu-id="16f6e-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="16f6e-130">Punkty końcowe metadanych dodanym w poprzednim kroku należy ustawić adres równe:</span><span class="sxs-lookup"><span data-stu-id="16f6e-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="16f6e-131">Pusty ciąg, aby użyć adresu podstawowego w aplikacji hosta jako punktu publikacji, jeśli podstawowy adres jest taki sam jak metadanych powiązania.</span><span class="sxs-lookup"><span data-stu-id="16f6e-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="16f6e-132">Adres względny, jeśli aplikacja hosta ma adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="16f6e-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="16f6e-133">Jako adres bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="16f6e-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="16f6e-134">Tworzenie i uruchamianie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="16f6e-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="16f6e-135">Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączony.</span><span class="sxs-lookup"><span data-stu-id="16f6e-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="16f6e-136">Jeśli nie, zostanie wyświetlony komunikat w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."</span><span class="sxs-lookup"><span data-stu-id="16f6e-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="16f6e-137">Aby użyć domyślnych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="16f6e-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="16f6e-138">Aby skonfigurować metadanych od usługi, która używa domyślne punkty końcowe, określić <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w konfiguracji pliku co w poprzednim przykładzie, ale nie określono żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="16f6e-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="16f6e-139">Plik konfiguracji następnie będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="16f6e-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="16f6e-140">Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> z `httpGetEnabled` ustawioną `true`, usługa ma Publikowanie metadanych włączone, a ponieważ punkty końcowe nie zostały dodane w sposób jawny, środowisko uruchomieniowe dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="16f6e-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="16f6e-141">Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="16f6e-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f6e-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="16f6e-142">Example</span></span>  
 <span data-ttu-id="16f6e-143">Poniższy przykładowy kod przedstawia implementację podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi i pliku konfiguracji, która umożliwia publikowanie metadanych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="16f6e-143">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16f6e-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16f6e-144">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="16f6e-145">Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="16f6e-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="16f6e-146">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="16f6e-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="16f6e-147">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="16f6e-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="16f6e-148">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="16f6e-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="16f6e-149">Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="16f6e-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
