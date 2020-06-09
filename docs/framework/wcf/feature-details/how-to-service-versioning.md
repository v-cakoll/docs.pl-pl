---
title: 'Instrukcje: Przechowywanie wersji usługi'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: beb7de63d300ad7986bfc59093006b074b9456ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586939"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="07725-102">Instrukcje: Przechowywanie wersji usługi</span><span class="sxs-lookup"><span data-stu-id="07725-102">How To: Service Versioning</span></span>
<span data-ttu-id="07725-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, która kieruje komunikaty do różnych wersji tej samej usługi.</span><span class="sxs-lookup"><span data-stu-id="07725-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="07725-104">W tym przykładzie komunikaty są kierowane do dwóch różnych wersji usługi kalkulatora `roundingCalc` (v1) i `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="07725-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="07725-105">Obie implementacje obsługują te same operacje; jednak Starsza usługa, `roundingCalc` zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="07725-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="07725-106">Aplikacja kliencka musi być w stanie wskazać, czy ma być używana nowsza `regularCalc` Usługa.</span><span class="sxs-lookup"><span data-stu-id="07725-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="07725-107">Aby można było skierować komunikat do określonej wersji usługi, usługa routingu musi być w stanie określić miejsce docelowe wiadomości na podstawie zawartości komunikatu.</span><span class="sxs-lookup"><span data-stu-id="07725-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="07725-108">W poniższej metodzie klient określi wersję, wstawiając informacje do nagłówka komunikatu.</span><span class="sxs-lookup"><span data-stu-id="07725-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="07725-109">Istnieją metody obsługi wersji usługi, które nie wymagają od klientów przekazywania dodatkowych danych.</span><span class="sxs-lookup"><span data-stu-id="07725-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="07725-110">Na przykład komunikat może być kierowany do najnowszej lub najbardziej zgodnej wersji usługi lub router może użyć części standardowej koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="07725-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="07725-111">Operacje udostępniane przez obie usługi są następujące:</span><span class="sxs-lookup"><span data-stu-id="07725-111">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="07725-112">Dodaj</span><span class="sxs-lookup"><span data-stu-id="07725-112">Add</span></span>  
  
- <span data-ttu-id="07725-113">Odejmowanie</span><span class="sxs-lookup"><span data-stu-id="07725-113">Subtract</span></span>  
  
- <span data-ttu-id="07725-114">Mnożenie</span><span class="sxs-lookup"><span data-stu-id="07725-114">Multiply</span></span>  
  
- <span data-ttu-id="07725-115">Dzielenie</span><span class="sxs-lookup"><span data-stu-id="07725-115">Divide</span></span>  
  
 <span data-ttu-id="07725-116">Ponieważ oba implementacje usług obsługują te same operacje i są zasadniczo identyczne jak dane, które zwracają, dane podstawowe zawarte w komunikatach wysyłanych z aplikacji klienckich nie są wystarczająco unikatowe, aby umożliwić określenie sposobu kierowania żądania.</span><span class="sxs-lookup"><span data-stu-id="07725-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="07725-117">Na przykład filtry akcji nie mogą być używane, ponieważ domyślne akcje obu usług są takie same.</span><span class="sxs-lookup"><span data-stu-id="07725-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="07725-118">Można to rozwiązać na kilka sposobów, takich jak ujawnienie określonego punktu końcowego na routerze dla każdej wersji usługi lub dodanie niestandardowego elementu nagłówka do komunikatu w celu wskazania wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="07725-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="07725-119">Każdy z tych metod umożliwia jednoznaczne kierowanie komunikatów przychodzących do określonej wersji usługi, ale używanie unikatowej zawartości komunikatów jest preferowaną metodą rozróżniania między żądaniami dla różnych wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="07725-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="07725-120">W tym przykładzie aplikacja kliencka dodaje niestandardowy nagłówek "CalcVer" do komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="07725-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="07725-121">Ten nagłówek będzie zawierać wartość wskazującą wersję usługi, do której ma być kierowany komunikat.</span><span class="sxs-lookup"><span data-stu-id="07725-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="07725-122">Wartość "1" wskazuje, że komunikat musi być przetwarzany przez usługę roundingCalc, podczas gdy wartość "2" wskazuje usługę regularCalc.</span><span class="sxs-lookup"><span data-stu-id="07725-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="07725-123">Dzięki temu aplikacja kliencka może bezpośrednio kontrolować, która wersja usługi będzie przetwarzać komunikat.</span><span class="sxs-lookup"><span data-stu-id="07725-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="07725-124">Ponieważ nagłówek niestandardowy jest wartością znajdującą się w komunikacie, można użyć jednego punktu końcowego do odbierania komunikatów przeznaczonych dla obu wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="07725-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="07725-125">Poniższy kod może być używany w aplikacji klienckiej w celu dodania tego niestandardowego nagłówka do wiadomości:</span><span class="sxs-lookup"><span data-stu-id="07725-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="07725-126">Implementowanie obsługi wersji usługi</span><span class="sxs-lookup"><span data-stu-id="07725-126">Implement Service Versioning</span></span>  
  
1. <span data-ttu-id="07725-127">Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi uwidoczniony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="07725-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="07725-128">W poniższym przykładzie zdefiniowano pojedynczy punkt końcowy usługi, który będzie używany do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="07725-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="07725-129">Definiuje również punkty końcowe klienta, które będą używane do wysyłania komunikatów do `roundingCalc` (v1) i `regularCalc` (v2) usług.</span><span class="sxs-lookup"><span data-stu-id="07725-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
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
  
2. <span data-ttu-id="07725-130">Zdefiniuj filtry służące do kierowania komunikatów do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="07725-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="07725-131">W tym przykładzie filtr XPath służy do wykrywania wartości niestandardowego nagłówka "CalcVer" w celu określenia wersji, do której ma być kierowany komunikat.</span><span class="sxs-lookup"><span data-stu-id="07725-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="07725-132">Filtr XPath służy również do wykrywania komunikatów, które nie zawierają nagłówka "CalcVer".</span><span class="sxs-lookup"><span data-stu-id="07725-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="07725-133">W poniższym przykładzie zdefiniowano wymagane filtry i tabelę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="07725-133">The following example defines the required filters and namespace table.</span></span>  
  
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
    </filters>
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="07725-134">Prefiks przestrzeni nazw S12 jest definiowany domyślnie w tabeli przestrzeni nazw i reprezentuje przestrzeń nazw `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="07725-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3. <span data-ttu-id="07725-135">Zdefiniuj tabelę filtrów, która kojarzy każdy filtr z punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="07725-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="07725-136">Jeśli komunikat zawiera nagłówek "CalcVer" o wartości 1, zostanie on wysłany do usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="07725-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="07725-137">Jeśli nagłówek zawiera wartość 2, zostanie wysłany do usługi roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="07725-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="07725-138">Jeśli nagłówek nie jest obecny, komunikat zostanie rozesłany do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="07725-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="07725-139">Poniższy schemat definiuje tabelę filtrów i dodaje filtry zdefiniowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="07725-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
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
  
4. <span data-ttu-id="07725-140">Aby oszacować komunikaty przychodzące względem filtrów zawartych w tabeli filtrów, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="07725-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="07725-141">Poniższy przykład ilustruje kojarzenie `filterTable1` z punktami końcowymi usługi:</span><span class="sxs-lookup"><span data-stu-id="07725-141">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="07725-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="07725-142">Example</span></span>  
 <span data-ttu-id="07725-143">Poniżej znajduje się kompletna lista plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="07725-143">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="07725-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="07725-144">Example</span></span>  
 <span data-ttu-id="07725-145">Poniżej znajduje się kompletna lista aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="07725-145">The following is a complete listing of the client application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07725-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07725-146">See also</span></span>

- [<span data-ttu-id="07725-147">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="07725-147">Routing Services</span></span>](../samples/routing-services.md)
