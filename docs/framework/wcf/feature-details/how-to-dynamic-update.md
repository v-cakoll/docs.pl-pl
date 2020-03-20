---
title: 'Instrukcje: Aktualizacja dynamiczna'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: aaeb4d9d42c289cf34a6aee9212fc2d74b8f8c01
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184968"
---
# <a name="how-to-dynamic-update"></a>Instrukcje: Aktualizacja dynamiczna
W tym temacie opisano podstawowe kroki wymagane do utworzenia i dynamicznej aktualizacji konfiguracji routingu. W tym przykładzie początkowa konfiguracja routingu jest uzyskiwana z pliku konfiguracji i kieruje wszystkie komunikaty do usługi kalkulatora regularCalc; jednak jest następnie aktualizowana programowo w celu zmiany docelowego punktu końcowego usługi zaokrąglaniakłość.  
  
> [!NOTE]
> W wielu implementacjach konfiguracja będzie w pełni dynamiczna i nie będzie polegać na domyślnej konfiguracji; Jednak istnieją pewne scenariusze, takie jak ten w tym temacie, gdzie pożądane jest, aby mieć domyślny stan konfiguracji po uruchomieniu usługi.  
  
> [!NOTE]
> Aktualizacje dynamiczne występują tylko w pamięci i nie powodują modyfikacji plików konfiguracyjnych.  
  
 Zarówno regularCalc, jak i zaokrąglanieCalc obsługują te same operacje dodawania, odejmowania, mnożenia i dzielenia; jednak zaokrąglenieKal zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Plik konfiguracyjny służy do konfigurowania usługi do kierowania wszystkich wiadomości do usługi regularCalc. Po uruchomieniu usługi <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> routingu, służy do ponownego konfigurowania usługi do kierowania wiadomości do usługi zaokrąglaniaCalc.  
  
### <a name="implement-initial-configuration"></a>Implementowanie konfiguracji początkowej  
  
1. Utwórz podstawową konfigurację usługi routingu, określając punkty końcowe usługi udostępniane przez usługę. Poniższy przykład definiuje punkt końcowy pojedynczej usługi, który będzie używany do odbierania wiadomości. Definiuje również punkt końcowy klienta, który będzie używany do wysyłania wiadomości do regularCalc.  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. Zdefiniuj filtr używany do kierowania wiadomości do docelowych punktów końcowych. W tym przykładzie MatchAll filtr jest używany do kierowania wszystkich wiadomości do regularCalcEndpoint zdefiniowane wcześniej. Poniższy przykład definiuje tabelę filtrów i filtrów.  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. Aby ocenić przychodzące wiadomości względem filtrów zawartych w tabeli filtrów, należy skojarzyć tabelę filtrów z punktami końcowymi usługi przy użyciu zachowania routingu. W poniższym przykładzie pokazano skojarzenia "filterTable1" z punktem końcowym usługi.  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="implement-dynamic-configuration"></a>Implementowanie konfiguracji dynamicznej  
 Dynamiczną konfigurację usługi routingu można wykonać tylko <xref:System.ServiceModel.Routing.RoutingConfiguration> w <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> kodzie, tworząc nową i używając do zastąpienia bieżącej konfiguracji.  W tym przykładzie usługa routingu jest hostowana samodzielnie w aplikacji konsoli. Po uruchomieniu aplikacji można zmodyfikować konfigurację routingu, wprowadzając "regularne" lub "zaokrąglanie" w oknie konsoli, aby skonfigurować docelowy punkt końcowy, do którego są kierowane wiadomości; regularCalc, gdy "regularne" jest wprowadzany, w przeciwnym razie zaokrąglaniaCalc po wprowadzeniu "zaokrąglania".  
  
1. Następujące instrukcje using należy dodać w celu obsługi usługi routingu.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Poniższy kod jest używany do samodzielnego hostowania usługi routingu jako aplikacji konsoli. Spowoduje to zainicjowanie usługi routingu przy użyciu konfiguracji opisanej w poprzednim kroku, która znajduje się w pliku konfiguracji aplikacji. While Pętli zawiera kod używany do zmiany konfiguracji routingu.  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. Aby dynamicznie aktualizować konfigurację routingu, należy utworzyć nową konfigurację routingu. Musi to zawierać wszystkie punkty końcowe, filtry i tabele filtrów, które są wymagane dla nowej konfiguracji routingu, ponieważ całkowicie zastąpi istniejącą konfigurację routingu. Aby użyć nowej konfiguracji routingu, należy <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> wywołać i przekazać nową konfigurację.  
  
     Dodaj następujący kod do while pętli zdefiniowane wcześniej, aby umożliwić usługę do ponownego skonfigurowania na podstawie danych wejściowych użytkownika.  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > Ponieważ metoda dostarczania nowej konfiguracji routingu jest zawarta w rozszerzeniu usługi RoutingExtension, nowe obiekty RoutingConfiguration mogą być dostarczane w dowolnym miejscu w modelu rozszerzalności WCF, który ma lub może uzyskać odwołanie do ServiceHost lub ServiceExtensions (na przykład w innym ServiceExtension).
  
## <a name="example"></a>Przykład  

Poniżej znajduje się pełna lista aplikacji konsoli używane w tym przykładzie:
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a>Przykład  

Poniżej znajduje się pełna lista pliku konfiguracyjnego użytego w tym przykładzie:
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Usługi routingu](../samples/routing-services.md)
