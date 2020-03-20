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
# <a name="how-to-dynamic-update"></a><span data-ttu-id="ca0cd-102">Instrukcje: Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="ca0cd-102">How To: Dynamic Update</span></span>
<span data-ttu-id="ca0cd-103">W tym temacie opisano podstawowe kroki wymagane do utworzenia i dynamicznej aktualizacji konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="ca0cd-104">W tym przykładzie początkowa konfiguracja routingu jest uzyskiwana z pliku konfiguracji i kieruje wszystkie komunikaty do usługi kalkulatora regularCalc; jednak jest następnie aktualizowana programowo w celu zmiany docelowego punktu końcowego usługi zaokrąglaniakłość.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca0cd-105">W wielu implementacjach konfiguracja będzie w pełni dynamiczna i nie będzie polegać na domyślnej konfiguracji; Jednak istnieją pewne scenariusze, takie jak ten w tym temacie, gdzie pożądane jest, aby mieć domyślny stan konfiguracji po uruchomieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca0cd-106">Aktualizacje dynamiczne występują tylko w pamięci i nie powodują modyfikacji plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="ca0cd-107">Zarówno regularCalc, jak i zaokrąglanieCalc obsługują te same operacje dodawania, odejmowania, mnożenia i dzielenia; jednak zaokrąglenieKal zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="ca0cd-108">Plik konfiguracyjny służy do konfigurowania usługi do kierowania wszystkich wiadomości do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="ca0cd-109">Po uruchomieniu usługi <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> routingu, służy do ponownego konfigurowania usługi do kierowania wiadomości do usługi zaokrąglaniaCalc.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="ca0cd-110">Implementowanie konfiguracji początkowej</span><span class="sxs-lookup"><span data-stu-id="ca0cd-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="ca0cd-111">Utwórz podstawową konfigurację usługi routingu, określając punkty końcowe usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="ca0cd-112">Poniższy przykład definiuje punkt końcowy pojedynczej usługi, który będzie używany do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="ca0cd-113">Definiuje również punkt końcowy klienta, który będzie używany do wysyłania wiadomości do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2. <span data-ttu-id="ca0cd-114">Zdefiniuj filtr używany do kierowania wiadomości do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="ca0cd-115">W tym przykładzie MatchAll filtr jest używany do kierowania wszystkich wiadomości do regularCalcEndpoint zdefiniowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="ca0cd-116">Poniższy przykład definiuje tabelę filtrów i filtrów.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3. <span data-ttu-id="ca0cd-117">Aby ocenić przychodzące wiadomości względem filtrów zawartych w tabeli filtrów, należy skojarzyć tabelę filtrów z punktami końcowymi usługi przy użyciu zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="ca0cd-118">W poniższym przykładzie pokazano skojarzenia "filterTable1" z punktem końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="ca0cd-119">Implementowanie konfiguracji dynamicznej</span><span class="sxs-lookup"><span data-stu-id="ca0cd-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="ca0cd-120">Dynamiczną konfigurację usługi routingu można wykonać tylko <xref:System.ServiceModel.Routing.RoutingConfiguration> w <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> kodzie, tworząc nową i używając do zastąpienia bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="ca0cd-121">W tym przykładzie usługa routingu jest hostowana samodzielnie w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="ca0cd-122">Po uruchomieniu aplikacji można zmodyfikować konfigurację routingu, wprowadzając "regularne" lub "zaokrąglanie" w oknie konsoli, aby skonfigurować docelowy punkt końcowy, do którego są kierowane wiadomości; regularCalc, gdy "regularne" jest wprowadzany, w przeciwnym razie zaokrąglaniaCalc po wprowadzeniu "zaokrąglania".</span><span class="sxs-lookup"><span data-stu-id="ca0cd-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="ca0cd-123">Następujące instrukcje using należy dodać w celu obsługi usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="ca0cd-124">Poniższy kod jest używany do samodzielnego hostowania usługi routingu jako aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="ca0cd-125">Spowoduje to zainicjowanie usługi routingu przy użyciu konfiguracji opisanej w poprzednim kroku, która znajduje się w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="ca0cd-126">While Pętli zawiera kod używany do zmiany konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3. <span data-ttu-id="ca0cd-127">Aby dynamicznie aktualizować konfigurację routingu, należy utworzyć nową konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="ca0cd-128">Musi to zawierać wszystkie punkty końcowe, filtry i tabele filtrów, które są wymagane dla nowej konfiguracji routingu, ponieważ całkowicie zastąpi istniejącą konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="ca0cd-129">Aby użyć nowej konfiguracji routingu, należy <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> wywołać i przekazać nową konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="ca0cd-130">Dodaj następujący kod do while pętli zdefiniowane wcześniej, aby umożliwić usługę do ponownego skonfigurowania na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ca0cd-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    > <span data-ttu-id="ca0cd-131">Ponieważ metoda dostarczania nowej konfiguracji routingu jest zawarta w rozszerzeniu usługi RoutingExtension, nowe obiekty RoutingConfiguration mogą być dostarczane w dowolnym miejscu w modelu rozszerzalności WCF, który ma lub może uzyskać odwołanie do ServiceHost lub ServiceExtensions (na przykład w innym ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="ca0cd-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="ca0cd-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca0cd-132">Example</span></span>  

<span data-ttu-id="ca0cd-133">Poniżej znajduje się pełna lista aplikacji konsoli używane w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ca0cd-133">The following is a complete listing of the console application used in this example:</span></span>
  
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
  
## <a name="example"></a><span data-ttu-id="ca0cd-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca0cd-134">Example</span></span>  

<span data-ttu-id="ca0cd-135">Poniżej znajduje się pełna lista pliku konfiguracyjnego użytego w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ca0cd-135">The following is a complete listing of the configuration file used in this example:</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca0cd-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca0cd-136">See also</span></span>

- [<span data-ttu-id="ca0cd-137">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="ca0cd-137">Routing Services</span></span>](../samples/routing-services.md)
