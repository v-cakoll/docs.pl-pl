---
title: 'Instrukcje: Aktualizacja dynamiczna'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 95d99afd09daf4d9bf3937a71d7773332ff1bc14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834723"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="54bca-102">Instrukcje: Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="54bca-102">How To: Dynamic Update</span></span>
<span data-ttu-id="54bca-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia i dynamicznej aktualizacji konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="54bca-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="54bca-104">W tym przykładzie początkowa konfiguracja routingu jest uzyskiwana z pliku konfiguracji i kieruje wszystkie komunikaty do usługi kalkulatora regularCalc. jest to jednak aktualizowane programowo w celu zmiany docelowego punktu końcowego usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="54bca-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54bca-105">W wielu implementacjach konfiguracja będzie w pełni dynamiczna i nie będzie polegać na konfiguracji domyślnej. Istnieje jednak kilka scenariuszy, takich jak wymienione w tym temacie, w przypadku których pożądane jest posiadanie domyślnego stanu konfiguracji podczas uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="54bca-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54bca-106">Aktualizacje dynamiczne są wykonywane tylko w pamięci i nie powodują modyfikacji plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="54bca-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="54bca-107">Zarówno regularCalc, jak i roundingCalc obsługują te same operacje operacji dodawania, odejmowania, mnożenia i dzielenia; jednak roundingCalc zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="54bca-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="54bca-108">Plik konfiguracji służy do konfigurowania usługi do kierowania wszystkich komunikatów do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="54bca-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="54bca-109">Po uruchomieniu usługi routingu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> służy do ponownego skonfigurowania usługi do przesyłania komunikatów do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="54bca-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="54bca-110">Zaimplementuj konfigurację początkową</span><span class="sxs-lookup"><span data-stu-id="54bca-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="54bca-111">Utwórz podstawową konfigurację usługi routingu, określając punkty końcowe usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="54bca-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="54bca-112">W poniższym przykładzie zdefiniowano pojedynczy punkt końcowy usługi, który będzie używany do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="54bca-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="54bca-113">Definiuje również punkt końcowy klienta, który będzie używany do wysyłania komunikatów do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="54bca-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2. <span data-ttu-id="54bca-114">Zdefiniuj filtr używany do przesyłania komunikatów do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="54bca-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="54bca-115">W tym przykładzie filtr MatchAll służy do kierowania wszystkich komunikatów do zdefiniowanej wcześniej regularCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="54bca-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="54bca-116">W poniższym przykładzie zdefiniowano tabelę filtrów i filtrów.</span><span class="sxs-lookup"><span data-stu-id="54bca-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3. <span data-ttu-id="54bca-117">Aby oszacować komunikaty przychodzące względem filtrów zawartych w tabeli filtrów, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="54bca-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="54bca-118">Poniższy przykład demonstruje kojarzenie "filterTable1" z punktem końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="54bca-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="54bca-119">Zaimplementuj konfigurację dynamiczną</span><span class="sxs-lookup"><span data-stu-id="54bca-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="54bca-120">Konfigurację dynamiczną usługi routingu można wykonać tylko w kodzie, tworząc nową <xref:System.ServiceModel.Routing.RoutingConfiguration> i używając <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A>, aby zastąpić bieżącą konfigurację.</span><span class="sxs-lookup"><span data-stu-id="54bca-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="54bca-121">W tym przykładzie usługa routingu jest samodzielna w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="54bca-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="54bca-122">Po uruchomieniu aplikacji można zmodyfikować konfigurację routingu, wprowadzając wartość "Regular" lub "rounding" w oknie konsoli, aby skonfigurować docelowy punkt końcowy, do którego są kierowane komunikaty. regularCalc, gdy wprowadzono wartość "Regular", w przeciwnym razie roundingCalc, gdy zostanie wprowadzone "zaokrąglenie".</span><span class="sxs-lookup"><span data-stu-id="54bca-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="54bca-123">Aby można było obsługiwać usługę routingu, należy dodać następujące instrukcje using.</span><span class="sxs-lookup"><span data-stu-id="54bca-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="54bca-124">Poniższy kod służy do samodzielnego hostowania usługi routingu jako aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="54bca-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="54bca-125">Spowoduje to zainicjowanie usługi routingu przy użyciu konfiguracji opisanej w poprzednim kroku, która jest zawarta w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54bca-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="54bca-126">Pętla WHILE zawiera kod używany do zmiany konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="54bca-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3. <span data-ttu-id="54bca-127">Aby dynamicznie zaktualizować konfigurację routingu, należy utworzyć nową konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="54bca-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="54bca-128">Musi zawierać wszystkie punkty końcowe, filtry i tabele filtrów, które są wymagane dla nowej konfiguracji routingu, ponieważ całkowicie zastąpią istniejącą konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="54bca-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="54bca-129">Aby można było użyć nowej konfiguracji routingu, należy wywołać <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> i przekazać nową konfigurację.</span><span class="sxs-lookup"><span data-stu-id="54bca-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="54bca-130">Dodaj następujący kod do pętli while zdefiniowanej wcześniej, aby zezwolić na ponowną konfigurację usługi na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="54bca-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    > <span data-ttu-id="54bca-131">Ponieważ metoda udostępniania nowego zastosowano jest zawarta w rozszerzeniu usługi RoutingExtension, nowe obiekty zastosowano mogą być udostępniane w dowolnym miejscu w modelu rozszerzalności WCF, który ma lub może uzyskać odwołanie do ServiceHost lub Rozszerzenia serviceextension (na przykład w innym rozszerzeniu serviceextension).</span><span class="sxs-lookup"><span data-stu-id="54bca-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="54bca-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="54bca-132">Example</span></span>  

<span data-ttu-id="54bca-133">Poniżej przedstawiono pełną listę aplikacji konsolowej używanej w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="54bca-133">The following is a complete listing of the console application used in this example:</span></span>
  
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
  
## <a name="example"></a><span data-ttu-id="54bca-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="54bca-134">Example</span></span>  
 
<span data-ttu-id="54bca-135">Poniżej znajduje się kompletna lista plików konfiguracyjnych użytych w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="54bca-135">The following is a complete listing of the configuration file used in this example:</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="54bca-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54bca-136">See also</span></span>

- [<span data-ttu-id="54bca-137">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="54bca-137">Routing Services</span></span>](../samples/routing-services.md)
