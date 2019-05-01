---
title: 'Instrukcje: Przechowywanie wersji usługi'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: afc1a690cae020ded3988cfd41f0e926a2e86f1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047480"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="4be61-102">Instrukcje: Przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="4be61-102">How To: Service Versioning</span></span>
<span data-ttu-id="4be61-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, które kieruje komunikaty do różnych wersji tej samej usługi.</span><span class="sxs-lookup"><span data-stu-id="4be61-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="4be61-104">W tym przykładzie komunikaty są kierowane do dwóch różnych wersji usługi Kalkulator `roundingCalc` (wersja 1) i `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="4be61-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="4be61-105">Zarówno implementacje obsługują te same operacje; Jednak ze starszej usługi `roundingCalc`, zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="4be61-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="4be61-106">Aplikacja kliencka musi być w stanie wskazać, czy skorzystanie z nowszych `regularCalc` usługi.</span><span class="sxs-lookup"><span data-stu-id="4be61-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4be61-107">W celu kierowania komunikatu do określonej wersji usługi, usługa routingu musi być możliwe ustalenie, miejsce docelowe komunikat na podstawie zawartości komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4be61-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="4be61-108">W metodzie, pokazano poniżej klient będzie Określ wersję, wstawiając informacji w nagłówku komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4be61-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="4be61-109">Istnieją metody przechowywanie wersji usługi, które nie wymagają klientów przekazać dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="4be61-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="4be61-110">Na przykład komunikat może być kierowany do najnowszego lub najbardziej zgodną wersję usługi lub router wystarczą środki w ramach standardowego koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4be61-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="4be61-111">Operacje udostępniane przez obie te usługi są:</span><span class="sxs-lookup"><span data-stu-id="4be61-111">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="4be61-112">Dodaj</span><span class="sxs-lookup"><span data-stu-id="4be61-112">Add</span></span>  
  
- <span data-ttu-id="4be61-113">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="4be61-113">Subtract</span></span>  
  
- <span data-ttu-id="4be61-114">Mnożenie</span><span class="sxs-lookup"><span data-stu-id="4be61-114">Multiply</span></span>  
  
- <span data-ttu-id="4be61-115">Dzielenie</span><span class="sxs-lookup"><span data-stu-id="4be61-115">Divide</span></span>  
  
 <span data-ttu-id="4be61-116">Ponieważ zarówno implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowy dane zawarte w wiadomości wysyłanych z aplikacji klienckich nie jest unikatowy, aby możliwe było określić, jak kierować żądanie.</span><span class="sxs-lookup"><span data-stu-id="4be61-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="4be61-117">Na przykład nie można użyć filtrów akcji, ponieważ domyślne akcje dla obu usług są takie same.</span><span class="sxs-lookup"><span data-stu-id="4be61-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="4be61-118">Ten problem można rozwiązać na kilka sposobów, takie jak udostępnianie określonego punktu końcowego na routerze dla każdej wersji usługi lub Dodawanie elementu niestandardowego nagłówka do wiadomości wskazania usługi w wersji.</span><span class="sxs-lookup"><span data-stu-id="4be61-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="4be61-119">Każda z tych metod pozwala jednoznacznie kierowanie komunikatów przychodzących do określonej wersji usługi, ale korzystanie z zawartości wiadomości unikatowy jest preferowaną metodą rozróżnianiu poszczególnych żądań dla różnych wersji dodatku service.</span><span class="sxs-lookup"><span data-stu-id="4be61-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="4be61-120">W tym przykładzie aplikacja kliencka dodaje niestandardowy nagłówek "CalcVer" komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="4be61-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="4be61-121">Ten nagłówek będzie zawierać wartość, która wskazuje wersję komunikat powinien być kierowane do usługi.</span><span class="sxs-lookup"><span data-stu-id="4be61-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="4be61-122">Wartość "1" wskazuje, że komunikat muszą zostać przetworzone przez usługę roundingCalc, natomiast wartość "2" oznacza usługę regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4be61-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="4be61-123">Dzięki temu aplikacja kliencka do kontrolowania bezpośrednio, która wersja usługi będzie przetwarzać komunikat.</span><span class="sxs-lookup"><span data-stu-id="4be61-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="4be61-124">Ponieważ niestandardowy nagłówek wartości zawarte w wiadomości, można użyć jeden punkt końcowy do odbierania komunikatów przeznaczonych dla obu wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="4be61-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="4be61-125">Poniższy kod może służyć w aplikacji klienckiej, aby dodać nagłówek niestandardowy komunikat o:</span><span class="sxs-lookup"><span data-stu-id="4be61-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="4be61-126">Implementowanie przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="4be61-126">Implement Service Versioning</span></span>  
  
1. <span data-ttu-id="4be61-127">Tworzenie podstawowej konfiguracji usługa routingu, określając punkt końcowy usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4be61-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="4be61-128">Poniższy przykład definiuje pojedynczą usługę punktu końcowego, na który będzie używany do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4be61-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="4be61-129">Umożliwia on również definiowanie punktów końcowych klienta, które będą używane do wysyłania wiadomości `roundingCalc` (wersja 1) i `regularCalc` services (wersja 2).</span><span class="sxs-lookup"><span data-stu-id="4be61-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
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
  
2. <span data-ttu-id="4be61-130">Zdefiniuj filtry używane do przesyłania wiadomości do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4be61-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="4be61-131">W tym przykładzie filtr XPath jest używana wartość niestandardowego nagłówka "CalcVer", aby określić, która wersja komunikatu, powinny być kierowane do wykrywania.</span><span class="sxs-lookup"><span data-stu-id="4be61-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="4be61-132">Filtr XPath jest również używane do wykrywania wiadomości, które nie zawierają nagłówek "CalcVer".</span><span class="sxs-lookup"><span data-stu-id="4be61-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="4be61-133">W poniższym przykładzie zdefiniowano wymagane filtry i przestrzeń nazw tabeli.</span><span class="sxs-lookup"><span data-stu-id="4be61-133">The following example defines the required filters and namespace table.</span></span>  
  
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
    > <span data-ttu-id="4be61-134">Prefiks przestrzeni nazw s12 jest zdefiniowana w przestrzeni nazw tabeli i reprezentuje obszar nazw `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="4be61-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3. <span data-ttu-id="4be61-135">Definiowanie tabeli filtru każdy filtr zostanie skojarzony z punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="4be61-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="4be61-136">Jeśli wiadomość zawiera nagłówek "CalcVer" o wartości 1, zostanie wysłany do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4be61-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="4be61-137">Nagłówek zawiera wartość 2, będą przesyłane do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="4be61-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="4be61-138">Jeśli występuje bez nagłówka wiadomości będą kierowane do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4be61-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="4be61-139">Poniżej definiuje tabelę filtru i dodaje zdefiniowane wcześniej filtry.</span><span class="sxs-lookup"><span data-stu-id="4be61-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
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
  
4. <span data-ttu-id="4be61-140">Aby ocenić komunikaty przychodzące filtry zawartych w tabeli filtru, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="4be61-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="4be61-141">W poniższym przykładzie pokazano kojarzenie `filterTable1` z punktami końcowymi usługi:</span><span class="sxs-lookup"><span data-stu-id="4be61-141">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4be61-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="4be61-142">Example</span></span>  
 <span data-ttu-id="4be61-143">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4be61-143">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4be61-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="4be61-144">Example</span></span>  
 <span data-ttu-id="4be61-145">Poniżej znajduje się pełna lista aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="4be61-145">The following is a complete listing of the client application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4be61-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4be61-146">See also</span></span>

- [<span data-ttu-id="4be61-147">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="4be61-147">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
