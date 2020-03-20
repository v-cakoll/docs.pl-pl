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
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji
Jest to jeden z dwóch tematów in how-to, które pokazują publikowania metadanych dla usługi Windows Communication Foundation (WCF). Istnieją dwa sposoby określania sposobu publikowania metadanych przez usługę przy użyciu pliku konfiguracji i przy użyciu kodu. W tym temacie pokazano, jak opublikować metadane dla usługi przy użyciu pliku konfiguracji.  
  
> [!CAUTION]
> W tym temacie pokazano, jak opublikować metadane w sposób niezabezpieczony. Każdy klient może pobrać metadane z usługi. Jeśli chcesz, aby usługa publikowała metadane w bezpieczny sposób, zobacz [Niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Aby uzyskać więcej informacji na temat publikowania metadanych w kodzie, zobacz [Jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikowanie metadanych umożliwia klientom pobieranie metadanych przy użyciu żądania GET transferu `?wsdl` WS lub żądania HTTP/GET przy użyciu ciągu zapytania. Aby upewnić się, że kod działa, należy utworzyć podstawową usługę WCF. Dla uproszczenia podstawowa usługa hostowana samodzielnie jest dostępna w poniższym kodzie.  
  
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
  
 Ta usługa jest usługą hostowana samodzielnie, która jest konfigurowana przy użyciu pliku konfiguracyjnego. Następujący plik konfiguracyjny służy jako punkt wyjścia.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Aby opublikować metadane usługi WCF przy użyciu pliku konfiguracji aplikacji  
  
1. W pliku App.config, po `</services>` zamknięciu `<behaviors>` elementu, utwórz element.  

2. W `<behaviors>` obrębie elementu `<serviceBehaviors>` dodaj element.  

3. Dodaj `<behavior>` element do `<serviceBehaviors>` elementu i określ `name` wartość atrybutu `<behavior>` elementu.  

4. Dodaj `<serviceMetadata>` element do `<behavior>` elementu. Ustaw `httpGetEnabled` atrybut `true` i `policyVersion` atrybut policy15. `httpGetEnabled`umożliwia usłudze odpowiadanie na żądania metadanych wykonane przez żądanie HTTP GET. `policyVersion`informuje usługę, aby była zgodna z zasadą WS 1.5 podczas generowania metadanych.  

5. Dodaj `behaviorConfiguration` atrybut do `<service>` elementu i `name` określ atrybut `<behavior>` elementu dodanego w kroku 1, jak pokazano w poniższym przykładzie kodu.  
  
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
  
6. Dodaj jeden `<endpoint>` lub więcej elementów `IMetadataExchange`z zestawem kontraktu do , jak pokazano w poniższym przykładzie kodu.  
  
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
  
7. W przypadku punktów końcowych metadanych dodanych `binding` w poprzednim kroku ustaw atrybut na jeden z następujących:  
  
    - `mexHttpBinding`do publikacji HTTP.  
  
    - `mexHttpsBinding`do publikacji HTTPS.  
  
    - `mexNamedPipeBinding`dla nazwanego publikowania potoków.  
  
    - `mexTcpBinding`do publikacji TCP.  
  
8. Dla punktów końcowych metadanych dodanych w poprzednim kroku ustaw adres równy:  
  
    - Pusty ciąg do używania adresu podstawowego aplikacji hosta jako punktu publikacji, jeśli adres podstawowy jest taki sam jak powiązanie metadanych.  
  
    - Adres względny, jeśli aplikacja hosta ma adres podstawowy.  
  
    - Adres bezwzględny.  
  
9. Skompiluj i uruchom aplikację konsolową.  
  
10. Użyj programu Internet Explorer, aby przejść dohttp://localhost:8001/MetadataSample adresu podstawowego usługi (w tym przykładzie) i sprawdzić, czy publikowanie metadanych jest włączone. Jeśli nie, w górnej części strony wynikowej zostanie wyświetlony komunikat: "Publikowanie metadanych dla tej usługi jest obecnie wyłączone".  
  
### <a name="to-use-default-endpoints"></a>Aby użyć domyślnych punktów końcowych  
  
1. Aby skonfigurować metadane w usłudze, która używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior> domyślnych punktów końcowych, należy określić w pliku konfiguracyjnym, jak w poprzednim przykładzie, ale nie określać żadnych punktów końcowych. Plik konfiguracyjny będzie wyglądać w ten sposób.  
  
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
  
     Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> `httpGetEnabled` z zestawem do `true`, usługa ma włączone metadane publikowania, a ponieważ nie punkty końcowe zostały jawnie dodane, środowisko wykonawcze dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia implementację podstawowej usługi WCF i pliku konfiguracji, który publikuje metadane dla usługi.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Host samodzielny](../../../../docs/framework/wcf/samples/self-host.md)
- [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
