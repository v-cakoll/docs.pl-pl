---
title: 'Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 26894a3951b91879a7b3e6f66731891113394082
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045305"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji
Jest to jeden z dwóch tematów, które przedstawiają Publikowanie metadanych dla usługi Windows Communication Foundation (WCF). Istnieją dwa sposoby, aby określić, w jaki sposób usługa powinna publikować metadane przy użyciu pliku konfiguracji i przy użyciu kodu. W tym temacie przedstawiono sposób publikowania metadanych dla usługi za pomocą pliku konfiguracji.  
  
> [!CAUTION]
> W tym temacie przedstawiono sposób publikowania metadanych w niezabezpieczony sposób. Dowolny klient może pobrać metadane z usługi. Jeśli wymagasz, aby usługa opublikowała metadane w bezpieczny sposób, zobacz [Niestandardowy bezpieczny metadanych punkt końcowy](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Aby uzyskać więcej informacji na temat publikowania metadanych w kodzie [, zobacz How to: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikowanie metadanych umożliwia klientom Pobieranie metadanych przy użyciu żądania GET WS-transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania. Aby upewnić się, że kod działa, Utwórz podstawową usługę WCF. Dla uproszczenia podstawowa usługa samoobsługowa jest udostępniana w poniższym kodzie.  
  
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
  
 Ta usługa to usługa samodzielna, która jest konfigurowana przy użyciu pliku konfiguracji. Następujący plik konfiguracyjny służy jako punkt wyjścia.  
  
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
  
1. W pliku App. config po elemencie zamykającym `</services>` `<behaviors>` Utwórz element.  

2. `<behaviors>` W elemencie`<serviceBehaviors>` Dodaj element.  

3. Dodaj element do elementu i `name` Określ wartość atrybutu `<behavior>` elementu. `<serviceBehaviors>` `<behavior>`  

4. `<serviceMetadata>` Dodaj element`<behavior>` do elementu. Ustaw atrybut na `true` i`policyVersion` atrybut na Policy15. `httpGetEnabled` `httpGetEnabled`umożliwia usłudze reagowanie na żądania metadanych wykonywane przez żądanie HTTP GET. `policyVersion`instruuje usługę, aby była zgodna z usługą WS-Policy 1,5 podczas generowania metadanych.  

5. Dodaj atrybut do elementu i określ `name`atrybutelementudodanego w kroku 1, jak pokazano w poniższym przykładzie kodu. `<behavior>` `<service>` `behaviorConfiguration`  
  
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
  
6. Dodaj jeden lub więcej `<endpoint>` elementów z ustawioną umową `IMetadataExchange`do, jak pokazano w poniższym przykładzie kodu.  
  
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
  
7. Dla punktów końcowych metadanych dodanych w poprzednim kroku Ustaw `binding` atrybut na jeden z następujących:  
  
    - `mexHttpBinding`dla publikacji HTTP.  
  
    - `mexHttpsBinding`dla publikacji HTTPS.  
  
    - `mexNamedPipeBinding`dla publikacji nazwanego potoku.  
  
    - `mexTcpBinding`dla publikacji TCP.  
  
8. Dla punktów końcowych metadanych dodanych w poprzednim kroku Ustaw adres równy:  
  
    - Pusty ciąg, który będzie używać adresu podstawowego aplikacji hosta jako punktu publikacji, jeśli adres podstawowy jest taki sam jak powiązanie metadanych.  
  
    - Adres względny, jeśli aplikacja hosta ma adres podstawowy.  
  
    - Adres bezwzględny.  
  
9. Kompiluj i uruchom aplikację konsolową.  
  
10. Użyj programu Internet Explorer, aby przejść do adresu podstawowego usługi (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdzić, czy Publikowanie metadanych jest włączone. W przeciwnym razie zostanie wyświetlony komunikat w górnej części strony wyników: "Publikowanie metadanych dla tej usługi jest obecnie wyłączone".  
  
### <a name="to-use-default-endpoints"></a>Aby użyć domyślnych punktów końcowych  
  
1. Aby skonfigurować metadane w usłudze korzystającej z domyślnych punktów końcowych, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Określ w pliku konfiguracji, jak w poprzednim przykładzie, ale nie określaj żadnych punktów końcowych. Plik konfiguracji będzie wyglądał następująco.  
  
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
  
     Ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> `httpGetEnabled` ustawioną wartość `true`, usługa ma włączone metadane publikowania i ponieważ żadne punkty końcowe nie zostały jawnie dodane, środowisko uruchomieniowe dodaje domyślne punkty końcowe. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje implementację podstawowej usługi WCF i plik konfiguracji, który publikuje metadane dla usługi.  
  
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
