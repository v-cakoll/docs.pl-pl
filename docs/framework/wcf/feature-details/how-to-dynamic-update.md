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
# <a name="how-to-dynamic-update"></a><span data-ttu-id="b3df4-102">Instrukcje: Aktualizacja dynamiczna</span><span class="sxs-lookup"><span data-stu-id="b3df4-102">How To: Dynamic Update</span></span>
<span data-ttu-id="b3df4-103">W tym temacie przedstawiono podstawowe czynności wymagane do tworzenia i dynamicznie Aktualizuj konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="b3df4-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="b3df4-104">W tym przykładzie początkowej konfiguracji routingu są uzyskiwane z pliku konfiguracji i kieruje komunikaty do usługi Kalkulator regularCalc; jednak jest następnie aktualizowany programowo Aby zmienić docelowy punkt końcowy usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="b3df4-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3df4-105">Wiele implementacji konfiguracji będzie można całkowicie dynamiczne i nie będzie używana domyślna konfiguracja; Istnieją jednak niektóre scenariusze, takie jak w tym temacie, w których konieczne jest mają domyślny stan konfiguracji podczas uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="b3df4-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3df4-106">Dynamiczne aktualizacje występuje tylko w pamięci i nie powoduje modyfikacji plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b3df4-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="b3df4-107">Zarówno regularCalc, jak i roundingCalc obsługuje te same operacje dodawania, odejmowania, mnożenia i dzielenia; jednak roundingCalc zaokrągla wszystkich obliczeń do najbliższej liczby całkowitej wartości przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="b3df4-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="b3df4-108">Plik konfiguracji jest używany do konfigurowania usługi do rozsyłania wszystkich wiadomości z usługą regularCalc.</span><span class="sxs-lookup"><span data-stu-id="b3df4-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="b3df4-109">Po uruchomieniu usługi routingu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> umożliwia zmianę konfiguracji usługi do przesyłania wiadomości z usługą roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="b3df4-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="b3df4-110">Wdrożenie konfiguracji początkowej</span><span class="sxs-lookup"><span data-stu-id="b3df4-110">Implement Initial Configuration</span></span>  
  
1.  <span data-ttu-id="b3df4-111">Utwórz podstawową konfigurację usługi routingu, podając punktów końcowych usług udostępnianych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="b3df4-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="b3df4-112">W poniższym przykładzie zdefiniowano pojedynczego punktu końcowego, która będzie używana do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b3df4-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="b3df4-113">Definiuje również punkt końcowy klienta, który będzie używany do wysyłania komunikatów do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="b3df4-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2.  <span data-ttu-id="b3df4-114">Zdefiniuj filtr służący do przesyłania wiadomości do punktów końcowych docelowego.</span><span class="sxs-lookup"><span data-stu-id="b3df4-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="b3df4-115">Na przykład filtr MatchAll jest używany do rozsyłania wszystkich wiadomości do regularCalcEndpoint wcześniej zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b3df4-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="b3df4-116">W poniższym przykładzie zdefiniowano filtr i tabeli filtrów.</span><span class="sxs-lookup"><span data-stu-id="b3df4-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3.  <span data-ttu-id="b3df4-117">Aby ocenić wiadomości przychodzących filtry zawartych w tabeli filtru, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="b3df4-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="b3df4-118">W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktem końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="b3df4-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="b3df4-119">Wdrożenie konfiguracji dynamicznej</span><span class="sxs-lookup"><span data-stu-id="b3df4-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="b3df4-120">Dynamiczne konfiguracji usługi routingu można wykonać tylko w kodzie, tworząc nowe <xref:System.ServiceModel.Routing.RoutingConfiguration> i przy użyciu <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> zastąpić bieżącą konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b3df4-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="b3df4-121">W tym przykładzie usługa routingu jest samodzielnie hostowana w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b3df4-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="b3df4-122">Po uruchomieniu aplikacji, wprowadzając "regularny" lub "zaokrąglania" w oknie konsoli, aby skonfigurować docelowego punktu końcowego, że komunikaty są kierowane do; można zmodyfikować konfigurację routingu podano regularCalc po "regularny", w przeciwnym razie wartość jest wprowadzana roundingCalc po "zaokrąglania".</span><span class="sxs-lookup"><span data-stu-id="b3df4-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1.  <span data-ttu-id="b3df4-123">Następujące instrukcje using muszą zostać dodane w celu obsługi usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="b3df4-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  <span data-ttu-id="b3df4-124">Poniższy kod służy do hosta samodzielnego usługa routingu jako aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b3df4-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="b3df4-125">Usługa routingu za pomocą konfiguracji opisanych w poprzednim kroku, który jest zawarty w pliku konfiguracji aplikacji jest inicjowana.</span><span class="sxs-lookup"><span data-stu-id="b3df4-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="b3df4-126">While pętla zawiera kod używany w celu zmiany konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="b3df4-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3.  <span data-ttu-id="b3df4-127">Aby dynamicznie aktualizować konfiguracji routingu, należy utworzyć nową konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="b3df4-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="b3df4-128">Ten element musi zawierać wszystkie punkty końcowe, filtrów i filtrów tabel, które są wymagane dla nowej konfiguracji routingu, jak całkowicie zastąpi istniejącą konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="b3df4-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="b3df4-129">Aby można było korzystać z nowej konfiguracji routingu, należy wywołać <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> i przekaż nową konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b3df4-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="b3df4-130">Dodaj następujący kod do while pętli zdefiniowana wcześniej, aby umożliwić usłudze zostać ponownie skonfigurowany oparte na danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b3df4-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    >  <span data-ttu-id="b3df4-131">Od metody do prezentowania nową konfigurację znajduje się w rozszerzeniu usługi rozszerzenia RoutingExtension, nową konfigurację obiektów można podać dowolne miejsce w modelu rozszerzalności WCF, który można uzyskać odwołania do obiektu ServiceHost lub lub ServiceExtensions (na przykład w innym ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="b3df4-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span> <span data-ttu-id="b3df4-132">Przykład konfigurację w ten sposób aktualizacji dynamicznej, zobacz [dynamiczna ponowna konfiguracja](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).</span><span class="sxs-lookup"><span data-stu-id="b3df4-132">For an example of dynamically updating the RoutingConfiguration in this manner, see [Dynamic Reconfiguration](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3df4-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3df4-133">Example</span></span>  
 <span data-ttu-id="b3df4-134">Poniżej znajduje się pełna lista aplikacji konsoli w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3df4-134">Following is a complete listing of the console application used in this example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b3df4-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3df4-135">Example</span></span>  
 <span data-ttu-id="b3df4-136">Poniżej znajduje się pełna lista konfiguracji pliku używana w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3df4-136">Following is a complete listing of the configuration file used in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3df4-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3df4-137">See Also</span></span>  
 [<span data-ttu-id="b3df4-138">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="b3df4-138">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
