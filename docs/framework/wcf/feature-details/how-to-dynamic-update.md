---
title: 'Instrukcje: Aktualizacja dynamiczna'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 597a4f8776398769307214090a8b463981bc0d46
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848143"
---
# <a name="how-to-dynamic-update"></a>Instrukcje: Aktualizacja dynamiczna
W tym temacie przedstawiono podstawowe kroki wymagane do tworzenia i dynamicznie aktualizować konfiguracji routingu. W tym przykładzie początkowej konfiguracji routingu jest uzyskiwana z pliku konfiguracji i kieruje wszystkie wiadomości w usłudze Kalkulator regularCalc; jednak jest następnie aktualizowany programowo Aby zmienić docelowy punkt końcowy usługi roundingCalc.  
  
> [!NOTE]
>  W wielu implementacjach konfiguracji będzie w pełni dynamicznego i nie będzie używana domyślna konfiguracja; Istnieją jednak pewne scenariusze, takie jak w tym temacie, w których konieczne jest zapewnienie domyślny stan konfiguracji podczas uruchamiania usługi.  
  
> [!NOTE]
>  Aktualizacje dynamiczne występuje tylko w pamięci i nie powodują modyfikacji plików konfiguracji.  
  
 RegularCalc i roundingCalc obsługują te same operacje dodawania, odejmowania, mnożenia i dzielenia; jednak roundingCalc zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Plik konfiguracji jest używany do konfigurowania usługi do rozsyłania wszystkich wiadomości w usłudze regularCalc. Po uruchomieniu usługa routingu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> służy do zmiany konfiguracji usługi przesyłania wiadomości w usłudze roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Implementowanie konfiguracji początkowej  
  
1.  Utwórz podstawową konfigurację usługi Routing, określając punktów końcowych usługi udostępniane przez usługę. Poniższy przykład definiuje pojedynczą usługę punktu końcowego, na który będzie używany do odbierania komunikatów. Definiuje również punkt końcowy klienta, która będzie służyć do wysyłania komunikatów do regularCalc.  
  
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
  
2.  Zdefiniuj filtr używany do przesyłania wiadomości do docelowych punktów końcowych. Na przykład filtr MatchAll służy do rozsyłania wszystkich wiadomości do regularCalcEndpoint zdefiniowany wcześniej. W poniższym przykładzie zdefiniowano filtr i tabelę filtru.  
  
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
  
3.  Aby ocenić komunikaty przychodzące filtry zawartych w tabeli filtru, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu. W poniższym przykładzie pokazano kojarzenie "filterTable1" z punktu końcowego usługi.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Implementowanie dynamiczną konfigurację  
 Dynamiczna konfiguracja usługa routingu można wykonać tylko w kodzie przez utworzenie nowego <xref:System.ServiceModel.Routing.RoutingConfiguration> i przy użyciu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> zastąpienie bieżącej konfiguracji.  W tym przykładzie usługa routingu jest samodzielnie hostowany w aplikacji konsoli. Po uruchomieniu aplikacji, można zmodyfikować konfiguracji routingu, wprowadzając "regularne" lub "zaokrąglania" w oknie konsoli aby skonfigurować docelowego punktu końcowego, że komunikaty są kierowane do; podano regularCalc po "regularne", w przeciwnym razie jest wprowadzana roundingCalc po "zaokrąglania".  
  
1.  Następujące instrukcje using muszą zostać dodane w celu obsługi usługi routingu.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  Poniższy kod jest używany na potrzeby samodzielnego hostowania usługa routingu jako aplikację konsolową w języku. Usługa routingu przy użyciu konfiguracji opisanej w poprzednim kroku, który jest zawarty w pliku konfiguracji aplikacji jest inicjowana. While pętla zawiera kod używany w celu zmiany konfiguracji routingu.  
  
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
  
3.  Aby dynamicznie aktualizować konfiguracji routingu, należy utworzyć nową konfigurację routingu. Ten element musi zawierać wszystkie punkty końcowe, filtry i tabel filtrów, które są wymagane dla nowej konfiguracji routingu, jak całkowicie zastąpi istniejącą konfigurację routingu. Aby można było korzystać z nowej konfiguracji routingu, należy wywołać <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> i przekaż nową konfigurację.  
  
     Dodaj następujący kod do while pętli zdefiniowany wcześniej, aby umożliwić usłudze ponownego oparte na danych wejściowych użytkownika.  
  
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
    > Od metody do prezentowania nowe RoutingConfiguration znajduje się w rozszerzeniu usługi RoutingExtension, RoutingConfiguration nowe obiekty można podać dowolne miejsce w modelu rozszerzalności usługi WCF, który można uzyskać odwołanie do elementu ServiceHost lub lub ServiceExtensions (na przykład w innym ServiceExtension).
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono pełną listę aplikacji konsoli, w tym przykładzie.  
  
```  
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
 Poniżej przedstawiono pełną listę konfiguracji plik używany w tym przykładzie.  
  
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
 [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
