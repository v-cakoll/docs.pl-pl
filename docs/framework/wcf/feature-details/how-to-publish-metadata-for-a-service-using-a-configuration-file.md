---
title: 'Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 94013c69bec0ea37c9260567437aeada3ebe2ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji
Jest to jeden z dwóch tematy porad, które przedstawiają Publikowanie metadanych dla usługi Windows Communication Foundation (WCF). Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i kod. W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji.  
  
> [!CAUTION]
>  W tym temacie pokazano, jak publikować metadane w sposób niezabezpieczonych. Dowolny klient może pobrać metadanych usługi. Jeśli potrzebujesz usługi publikować metadane w sposób bezpieczny, zobacz [niestandardowe bezpiecznego punktu końcowego metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Aby uzyskać więcej informacji o publikowaniu metadanych w kodzie, zobacz [porady: Publikowanie metadanych dla kodu przy użyciu usługi](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikowanie metadanych pozwala klientom na pobieranie metadanych za pomocą żądania GET usługi WS-Transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania. Aby się upewnić, że działa kod, należy utworzyć podstawowej usługi WCF. Dla uproszczenia podstawowej usługi hostowanej własnym znajduje się w następującym kodem.  
  
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
  
 Ta usługa jest samodzielnie hostowana usługa, która jest konfigurowana przy użyciu pliku konfiguracji. Następujący plik konfiguracji służy jako punkt początkowy.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Publikowanie metadanych dla usługi WCF, przy użyciu pliku konfiguracji aplikacji  
  
1.  W pliku App.config, po upływie `</services>` elementu, Utwórz `<behaviors>` elementu.  
  
  
  
2.  W ramach `<behaviors>` elementu, Dodaj `<serviceBehaviors>` elementu.  
  
  
  
3.  Dodaj `<behavior>` elementu `<serviceBehaviors>` element i określić wartość dla `name` atrybutu `<behavior>` elementu.  
  
  
  
4.  Dodaj `<serviceMetadata>` elementu `<behavior>` elementu. Ustaw `httpGetEnabled` atrybutu `true` i `policyVersion` atrybutu Policy15. `httpGetEnabled` Umożliwia usłudze odpowiadać na żądania metadanych przez żądanie HTTP GET. `policyVersion` Określa, że usługa odpowiadają WS-Policy 1.5 podczas generowania metadanych.  
  
  
  
5.  Dodaj `behaviorConfiguration` atrybutu `<service>` element i określ `name` atrybutu `<behavior>` element dodanej w kroku 1, jak pokazano w poniższym przykładzie kodu.  
  
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
  
6.  Dodaj jeden lub kilka `<endpoint>` ustawioną elementy z kontraktem `IMetadataExchange`, jak pokazano w poniższym przykładzie kodu.  
  
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
  
7.  Punkty końcowe metadanych dodanym w poprzednim kroku, można ustawić `binding` atrybutu do jednej z następujących czynności:  
  
    -   `mexHttpBinding` dla publikacji HTTP.  
  
    -   `mexHttpsBinding` dla publikacji HTTPS.  
  
    -   `mexNamedPipeBinding` dla publikacji nazwanego potoku.  
  
    -   `mexTcpBinding` dla publikacji TCP.  
  
8.  Punkty końcowe metadanych dodanym w poprzednim kroku należy ustawić adres równe:  
  
    -   Pusty ciąg, aby użyć adresu podstawowego w aplikacji hosta jako punktu publikacji, jeśli podstawowy adres jest taki sam jak metadanych powiązania.  
  
    -   Adres względny, jeśli aplikacja hosta ma adres podstawowy.  
  
    -   Jako adres bezwzględny.  
  
9. Tworzenie i uruchamianie aplikacji konsoli.  
  
10. Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączony. Jeśli nie, zostanie wyświetlony komunikat w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."  
  
### <a name="to-use-default-endpoints"></a>Aby użyć domyślnych punktów końcowych  
  
1.  Aby skonfigurować metadanych od usługi, która używa domyślne punkty końcowe, określić <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w konfiguracji pliku co w poprzednim przykładzie, ale nie określono żadnych punktów końcowych. Plik konfiguracji następnie będzie wyglądać następująco.  
  
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
  
     Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> z `httpGetEnabled` ustawioną `true`, usługa ma Publikowanie metadanych włączone, a ponieważ punkty końcowe nie zostały dodane w sposób jawny, środowisko uruchomieniowe dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia implementację podstawowej usługi WCF i pliku konfiguracji, która umożliwia publikowanie metadanych dla usługi.  
  
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
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Host samodzielny](../../../../docs/framework/wcf/samples/self-host.md)  
 [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
