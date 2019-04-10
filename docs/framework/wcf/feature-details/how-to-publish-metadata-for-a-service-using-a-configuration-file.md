---
title: 'Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 367ebeee5c12d809a758f1bee73dfaadda85788d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295539"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji
Jest to jedna z dwóch tematy porad, które pokazują Publikowanie metadanych dla usługi Windows Communication Foundation (WCF). Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i przy użyciu kodu. W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji.  
  
> [!CAUTION]
>  W tym temacie przedstawiono sposób Publikowanie metadanych w niezabezpieczony sposób. Dowolny klient może pobierać metadanych z usługi. Jeśli potrzebujesz usługi w celu publikowania metadanych w bezpieczny sposób, zobacz [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Aby uzyskać więcej informacji na temat publikowania metadanych w kodzie, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikowanie metadanych zezwala klientom na pobieranie metadanych za pomocą ROZPOCZYNANIE transferu WS żądania lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania. Aby się upewnić, że kod działa, Utwórz podstawowej usługi WCF. Dla uproszczenia podstawowa usługa Self-Hosted znajduje się w poniższym kodzie.  
  
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
  
 Ta usługa jest samodzielnie hostowana usługa, która została skonfigurowana przy użyciu pliku konfiguracji. Następujący plik konfiguracji, służy jako punkt wyjścia.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Publikowanie metadanych dla usługi WCF, za pomocą pliku konfiguracji aplikacji  
  
1. W pliku App.config, po upływie `</services>` elementu, Utwórz `<behaviors>` elementu.  

2. W ramach `<behaviors>` elementu Dodawanie `<serviceBehaviors>` elementu.  

3. Dodaj `<behavior>` elementu `<serviceBehaviors>` elementu i określić wartość dla `name` atrybutu `<behavior>` elementu.  

4. Dodaj `<serviceMetadata>` elementu `<behavior>` elementu. Ustaw `httpGetEnabled` atrybutu `true` i `policyVersion` atrybutu Policy15. `httpGetEnabled` Umożliwia usłudze odpowiadanie na żądania metadanych przez żądanie HTTP GET. `policyVersion` informuje usługę do odpowiadają WS-Policy w wersji 1.5 podczas generowania metadanych.  

5. Dodaj `behaviorConfiguration` atrybutu `<service>` elementu i określ `name` atrybutu `<behavior>` elementu dodany w kroku 1, jak pokazano w poniższym przykładzie kodu.  
  
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
  
6. Dodaj jeden lub kilka `<endpoint>` elementy z zamówienia równa `IMetadataExchange`, jak pokazano w poniższym przykładzie kodu.  
  
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
  
7. W przypadku punktów końcowych metadanych, dodane w poprzednim kroku, ustawić `binding` atrybut do jednego z następujących czynności:  
  
    -   `mexHttpBinding` dla publikacji HTTP.  
  
    -   `mexHttpsBinding` dla publikacji protokołu HTTPS.  
  
    -   `mexNamedPipeBinding` dla publikacji nazwanego potoku.  
  
    -   `mexTcpBinding` dla publikacji TCP.  
  
8. Dla punktów końcowych metadanych, dodane w poprzednim kroku należy ustawić adres równe:  
  
    -   Pusty ciąg do użycia jako punkt publikacji aplikacji hosta, adres podstawowy, jeśli podstawowy adres jest taki sam jak powiązanie metadanych.  
  
    -   Adres względny Jeśli aplikacja hosta ma adres podstawowy.  
  
    -   Bezwzględny adres.  
  
9. Skompiluj i uruchom aplikację konsolową.  
  
10. Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączona. W przeciwnym razie komunikat wyświetlany w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."  
  
### <a name="to-use-default-endpoints"></a>Aby użyć domyślnych punktów końcowych  
  
1. Aby skonfigurować usługę korzystającą z domyślnych punktów końcowych metadanych, określ <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w konfiguracji pliku co w poprzednim przykładzie, ale nie określono żadnych punktów końcowych. Plik konfiguracji będzie następnie wyglądać następująco.  
  
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
  
     Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> z `httpGetEnabled` równa `true`, usługa ma Publikowanie metadanych włączone, a ponieważ punkty końcowe nie zostały jawnie dodane, środowiska uruchomieniowego dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje wdrażania podstawowej usługi WCF i pliku konfiguracji, która umożliwia publikowanie metadanych dla usługi.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Host samodzielny](../../../../docs/framework/wcf/samples/self-host.md)
- [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
