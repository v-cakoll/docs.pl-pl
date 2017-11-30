---
title: "Instrukcje: Przechowywanie wersji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
caps.latest.revision: "6"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 4c4bd28c1a59d422c4ec0c65e133d253cabf16c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="15ef8-102">Instrukcje: Przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="15ef8-102">How To: Service Versioning</span></span>
<span data-ttu-id="15ef8-103">W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia konfiguracji routingu, który kieruje komunikaty do różnych wersji tę samą usługę.</span><span class="sxs-lookup"><span data-stu-id="15ef8-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="15ef8-104">W tym przykładzie wiadomości są kierowane do dwóch różnych wersji usługi Kalkulator `roundingCalc` (wersja 1) i `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="15ef8-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="15ef8-105">Zarówno implementacje obsługują te same operacje; jednak starsza usługa `roundingCalc`, zaokrągla przed zwróceniem wszystkich obliczeń do najbliższej wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="15ef8-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="15ef8-106">Aplikacja kliencka musi mieć możliwość wskazuje, czy należy użyć nowszej `regularCalc` usługi.</span><span class="sxs-lookup"><span data-stu-id="15ef8-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="15ef8-107">Celu kierowania wiadomości do wersji określonej usługi, usługa routingu musi być możliwe ustalenie docelowy komunikatu na podstawie zawartości komunikatu.</span><span class="sxs-lookup"><span data-stu-id="15ef8-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="15ef8-108">W metodzie przedstawiona poniżej klient będzie Określ wersję wstawiając informacji w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="15ef8-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="15ef8-109">Brak metody przechowywanie wersji usługi, które nie wymagają klientów do przekazywania dodatkowych danych.</span><span class="sxs-lookup"><span data-stu-id="15ef8-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="15ef8-110">Na przykład komunikat może być kierowane do najbardziej aktualnych lub najbardziej zgodną wersję usługi lub routera można użyć częścią standardowej koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="15ef8-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="15ef8-111">Operacje udostępnianych przez obie te usługi są:</span><span class="sxs-lookup"><span data-stu-id="15ef8-111">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="15ef8-112">Dodaj</span><span class="sxs-lookup"><span data-stu-id="15ef8-112">Add</span></span>  
  
-   <span data-ttu-id="15ef8-113">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="15ef8-113">Subtract</span></span>  
  
-   <span data-ttu-id="15ef8-114">Mnożenia</span><span class="sxs-lookup"><span data-stu-id="15ef8-114">Multiply</span></span>  
  
-   <span data-ttu-id="15ef8-115">Podziel</span><span class="sxs-lookup"><span data-stu-id="15ef8-115">Divide</span></span>  
  
 <span data-ttu-id="15ef8-116">Ponieważ obu implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowe dane zawarte w wiadomości wysyłane przez aplikacje klienckie nie jest unikatowa, co pozwala określić sposób kierowania żądanie.</span><span class="sxs-lookup"><span data-stu-id="15ef8-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="15ef8-117">Na przykład filtry akcji nie można użyć, ponieważ akcje domyślne obie te usługi są takie same.</span><span class="sxs-lookup"><span data-stu-id="15ef8-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="15ef8-118">Ten problem można rozwiązać na różne sposoby, takie jak udostępnianie określonego punktu końcowego na routerze dla każdej wersji usługi lub Dodawanie elementu niestandardowego nagłówka do komunikat, aby wskazywać wersję usługi.</span><span class="sxs-lookup"><span data-stu-id="15ef8-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="15ef8-119">Każdy z tych metod umożliwia jednoznacznie kierowania wiadomości przychodzących do określonej wersji usługi, ale przy użyciu zawartość komunikatu unikatowy jest preferowana metoda rozróżnianie między żądań dla różnych wersji dodatku service.</span><span class="sxs-lookup"><span data-stu-id="15ef8-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="15ef8-120">W tym przykładzie aplikacja kliencka dodaje nagłówek niestandardowy "CalcVer" komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="15ef8-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="15ef8-121">Ten nagłówek będzie zawierać wartość, która wskazuje wersję wiadomości powinny być kierowane do usługi.</span><span class="sxs-lookup"><span data-stu-id="15ef8-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="15ef8-122">Wartość "1" wskazuje, że komunikat muszą zostać przetworzone przez usługę roundingCalc, natomiast wartość "2" oznacza usługę regularCalc.</span><span class="sxs-lookup"><span data-stu-id="15ef8-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="15ef8-123">Dzięki temu aplikacja kliencka bezpośrednio kontrolować wersji usługi będzie przetwarzać komunikatu.</span><span class="sxs-lookup"><span data-stu-id="15ef8-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="15ef8-124">Ponieważ nagłówek niestandardowy jest wartość zawartych w komunikacie, umożliwia jeden punkt końcowy komunikaty przeznaczone dla obu wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="15ef8-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="15ef8-125">Poniższy kod umożliwia w aplikacji klienckiej Dodaj nagłówek niestandardowy komunikat:</span><span class="sxs-lookup"><span data-stu-id="15ef8-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="15ef8-126">Implementowanie przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="15ef8-126">Implement Service Versioning</span></span>  
  
1.  <span data-ttu-id="15ef8-127">Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="15ef8-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="15ef8-128">W poniższym przykładzie zdefiniowano pojedynczego punktu końcowego, która będzie używana do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="15ef8-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="15ef8-129">Definiuje punkty końcowe klienta, które będą używane do wysyłania wiadomości do `roundingCalc` (wersja 1) i `regularCalc` usługi (v2).</span><span class="sxs-lookup"><span data-stu-id="15ef8-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
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
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2.  <span data-ttu-id="15ef8-130">Zdefiniuj filtry używane do przesyłania wiadomości do punktów końcowych docelowego.</span><span class="sxs-lookup"><span data-stu-id="15ef8-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="15ef8-131">Na przykład filtr XPath jest używana do wykrywania wartość niestandardowego nagłówka "CalcVer" Aby ustalić, która wersja komunikatu powinny być kierowane do.</span><span class="sxs-lookup"><span data-stu-id="15ef8-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="15ef8-132">Filtr XPath służy również do wykrywania wiadomości, które nie zawierają nagłówka "CalcVer".</span><span class="sxs-lookup"><span data-stu-id="15ef8-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="15ef8-133">W poniższym przykładzie zdefiniowano wymagane filtry i przestrzeni nazw tabeli.</span><span class="sxs-lookup"><span data-stu-id="15ef8-133">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="15ef8-134">Prefiks przestrzeni nazw s12 jest zdefiniowany w tabeli nazw domyślnie i reprezentuje przestrzeni nazw "http://www.w3.org/2003/05/soap-envelope".</span><span class="sxs-lookup"><span data-stu-id="15ef8-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
3.  <span data-ttu-id="15ef8-135">Zdefiniuj filtr tabeli, które kojarzy każdego filtru z punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="15ef8-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="15ef8-136">Komunikat zawiera nagłówek "CalcVer" o wartości 1, będą przesyłane do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="15ef8-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="15ef8-137">Nagłówek zawiera wartość 2, będą przesyłane do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="15ef8-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="15ef8-138">Jeśli występuje bez nagłówka wiadomości będą kierowane do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="15ef8-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="15ef8-139">Następujące definiuje tabeli filtrów i dodaje filtry zdefiniowanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="15ef8-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="15ef8-140">Aby ocenić wiadomości przychodzących filtry zawartych w tabeli filtru, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="15ef8-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="15ef8-141">W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktów końcowych usługi:</span><span class="sxs-lookup"><span data-stu-id="15ef8-141">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="15ef8-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="15ef8-142">Example</span></span>  
 <span data-ttu-id="15ef8-143">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="15ef8-143">The following is a complete listing of the configuration file.</span></span>  
  
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
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="15ef8-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="15ef8-144">Example</span></span>  
 <span data-ttu-id="15ef8-145">Poniżej znajduje się pełna lista aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="15ef8-145">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to   
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="15ef8-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15ef8-146">See Also</span></span>  
 [<span data-ttu-id="15ef8-147">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="15ef8-147">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
