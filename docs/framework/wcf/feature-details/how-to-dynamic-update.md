---
title: 'Instrukcje: Aktualizacja dynamiczna'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 0a103e980d0d1be08f3ae6850c6af64405582c7b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972077"
---
# <a name="how-to-dynamic-update"></a>Instrukcje: Aktualizacja dynamiczna
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia i dynamicznej aktualizacji konfiguracji routingu. W tym przykładzie początkowa konfiguracja routingu jest uzyskiwana z pliku konfiguracji i kieruje wszystkie komunikaty do usługi kalkulatora regularCalc. jest to jednak aktualizowane programowo w celu zmiany docelowego punktu końcowego usługi roundingCalc.  
  
> [!NOTE]
> W wielu implementacjach konfiguracja będzie w pełni dynamiczna i nie będzie polegać na konfiguracji domyślnej. Istnieje jednak kilka scenariuszy, takich jak wymienione w tym temacie, w przypadku których pożądane jest posiadanie domyślnego stanu konfiguracji podczas uruchamiania usługi.  
  
> [!NOTE]
> Aktualizacje dynamiczne są wykonywane tylko w pamięci i nie powodują modyfikacji plików konfiguracji.  
  
 Zarówno regularCalc, jak i roundingCalc obsługują te same operacje operacji dodawania, odejmowania, mnożenia i dzielenia; jednak roundingCalc zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Plik konfiguracji służy do konfigurowania usługi do kierowania wszystkich komunikatów do usługi regularCalc. Po uruchomieniu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> usługi routingu jest używana do ponownego skonfigurowania usługi do przesyłania komunikatów do usługi roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Zaimplementuj konfigurację początkową  
  
1. Utwórz podstawową konfigurację usługi routingu, określając punkty końcowe usługi udostępniane przez usługę. W poniższym przykładzie zdefiniowano pojedynczy punkt końcowy usługi, który będzie używany do odbierania komunikatów. Definiuje również punkt końcowy klienta, który będzie używany do wysyłania komunikatów do regularCalc.  
  
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
  
2. Zdefiniuj filtr używany do przesyłania komunikatów do docelowych punktów końcowych. W tym przykładzie filtr MatchAll służy do kierowania wszystkich komunikatów do zdefiniowanej wcześniej regularCalcEndpoint. W poniższym przykładzie zdefiniowano tabelę filtrów i filtrów.  
  
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
  
3. Aby oszacować komunikaty przychodzące względem filtrów zawartych w tabeli filtrów, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu. Poniższy przykład demonstruje kojarzenie "filterTable1" z punktem końcowym usługi.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Zaimplementuj konfigurację dynamiczną  
 Konfigurację dynamiczną usługi routingu można wykonać tylko w kodzie, tworząc nowe <xref:System.ServiceModel.Routing.RoutingConfiguration> i używając <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> , aby zastąpić bieżącą konfigurację.  W tym przykładzie usługa routingu jest samodzielna w aplikacji konsolowej. Po uruchomieniu aplikacji można zmodyfikować konfigurację routingu, wprowadzając wartość "Regular" lub "rounding" w oknie konsoli, aby skonfigurować docelowy punkt końcowy, do którego są kierowane komunikaty. regularCalc, gdy wprowadzono wartość "Regular", w przeciwnym razie roundingCalc, gdy zostanie wprowadzone "zaokrąglenie".  
  
1. Aby można było obsługiwać usługę routingu, należy dodać następujące instrukcje using.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Poniższy kod służy do samodzielnego hostowania usługi routingu jako aplikacji konsolowej. Spowoduje to zainicjowanie usługi routingu przy użyciu konfiguracji opisanej w poprzednim kroku, która jest zawarta w pliku konfiguracyjnym aplikacji. Pętla WHILE zawiera kod używany do zmiany konfiguracji routingu.  
  
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
  
3. Aby dynamicznie zaktualizować konfigurację routingu, należy utworzyć nową konfigurację routingu. Musi zawierać wszystkie punkty końcowe, filtry i tabele filtrów, które są wymagane dla nowej konfiguracji routingu, ponieważ całkowicie zastąpią istniejącą konfigurację routingu. Aby można było użyć nowej konfiguracji routingu, należy wywołać <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> i przekazać nową konfigurację.  
  
     Dodaj następujący kod do pętli while zdefiniowanej wcześniej, aby zezwolić na ponowną konfigurację usługi na podstawie danych wejściowych użytkownika.  
  
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
    > Ponieważ metoda udostępniania nowego zastosowano jest zawarta w rozszerzeniu usługi RoutingExtension, nowe obiekty zastosowano mogą być udostępniane w dowolnym miejscu w modelu rozszerzalności WCF, który ma lub może uzyskać odwołanie do ServiceHost lub Rozszerzenia serviceextension (na przykład w innym rozszerzeniu serviceextension).
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kompletna lista aplikacji konsolowej użyta w tym przykładzie.  
  
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
 Poniżej znajduje się kompletna lista plików konfiguracyjnych użytych w tym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
