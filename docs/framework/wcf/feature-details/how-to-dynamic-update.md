---
title: 'Instrukcje: Aktualizacja dynamiczna'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 748286b4f6fa22b23423ff5c176c76d11fbe742d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamic-update"></a>Instrukcje: Aktualizacja dynamiczna
W tym temacie przedstawiono podstawowe czynności wymagane do tworzenia i dynamicznie Aktualizuj konfigurację routingu. W tym przykładzie początkowej konfiguracji routingu są uzyskiwane z pliku konfiguracji i kieruje komunikaty do usługi Kalkulator regularCalc; jednak jest następnie aktualizowany programowo Aby zmienić docelowy punkt końcowy usługi roundingCalc.  
  
> [!NOTE]
>  Wiele implementacji konfiguracji będzie można całkowicie dynamiczne i nie będzie używana domyślna konfiguracja; Istnieją jednak niektóre scenariusze, takie jak w tym temacie, w których konieczne jest mają domyślny stan konfiguracji podczas uruchamiania usługi.  
  
> [!NOTE]
>  Dynamiczne aktualizacje występuje tylko w pamięci i nie powoduje modyfikacji plików konfiguracji.  
  
 Zarówno regularCalc, jak i roundingCalc obsługuje te same operacje dodawania, odejmowania, mnożenia i dzielenia; jednak roundingCalc zaokrągla wszystkich obliczeń do najbliższej liczby całkowitej wartości przed zwróceniem. Plik konfiguracji jest używany do konfigurowania usługi do rozsyłania wszystkich wiadomości z usługą regularCalc. Po uruchomieniu usługi routingu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> umożliwia zmianę konfiguracji usługi do przesyłania wiadomości z usługą roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Wdrożenie konfiguracji początkowej  
  
1.  Utwórz podstawową konfigurację usługi routingu, podając punktów końcowych usług udostępnianych przez usługę. W poniższym przykładzie zdefiniowano pojedynczego punktu końcowego, która będzie używana do odbierania wiadomości. Definiuje również punkt końcowy klienta, który będzie używany do wysyłania komunikatów do regularCalc.  
  
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
  
2.  Zdefiniuj filtr służący do przesyłania wiadomości do punktów końcowych docelowego. Na przykład filtr MatchAll jest używany do rozsyłania wszystkich wiadomości do regularCalcEndpoint wcześniej zdefiniowane. W poniższym przykładzie zdefiniowano filtr i tabeli filtrów.  
  
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
  
3.  Aby ocenić wiadomości przychodzących filtry zawartych w tabeli filtru, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu. W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktem końcowym usługi.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Wdrożenie konfiguracji dynamicznej  
 Dynamiczne konfiguracji usługi routingu można wykonać tylko w kodzie, tworząc nowe <xref:System.ServiceModel.Routing.RoutingConfiguration> i przy użyciu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> zastąpić bieżącą konfigurację.  W tym przykładzie usługa routingu jest samodzielnie hostowana w aplikacji konsoli. Po uruchomieniu aplikacji, wprowadzając "regularny" lub "zaokrąglania" w oknie konsoli, aby skonfigurować docelowego punktu końcowego, że komunikaty są kierowane do; można zmodyfikować konfigurację routingu podano regularCalc po "regularny", w przeciwnym razie wartość jest wprowadzana roundingCalc po "zaokrąglania".  
  
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
  
2.  Poniższy kod służy do hosta samodzielnego usługa routingu jako aplikacji konsoli. Usługa routingu za pomocą konfiguracji opisanych w poprzednim kroku, który jest zawarty w pliku konfiguracji aplikacji jest inicjowana. While pętla zawiera kod używany w celu zmiany konfiguracji routingu.  
  
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
  
3.  Aby dynamicznie aktualizować konfiguracji routingu, należy utworzyć nową konfigurację routingu. Ten element musi zawierać wszystkie punkty końcowe, filtrów i filtrów tabel, które są wymagane dla nowej konfiguracji routingu, jak całkowicie zastąpi istniejącą konfigurację routingu. Aby można było korzystać z nowej konfiguracji routingu, należy wywołać <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> i przekaż nową konfigurację.  
  
     Dodaj następujący kod do while pętli zdefiniowana wcześniej, aby umożliwić usłudze zostać ponownie skonfigurowany oparte na danych wejściowych użytkownika.  
  
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
    >  Od metody do prezentowania nową konfigurację znajduje się w rozszerzeniu usługi rozszerzenia RoutingExtension, nową konfigurację obiektów można podać dowolne miejsce w modelu rozszerzalności WCF, który można uzyskać odwołania do obiektu ServiceHost lub lub ServiceExtensions (na przykład w innym ServiceExtension). Przykład konfigurację w ten sposób aktualizacji dynamicznej, zobacz [dynamiczna ponowna konfiguracja](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista aplikacji konsoli w tym przykładzie.  
  
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
 Poniżej znajduje się pełna lista konfiguracji pliku używana w tym przykładzie.  
  
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
