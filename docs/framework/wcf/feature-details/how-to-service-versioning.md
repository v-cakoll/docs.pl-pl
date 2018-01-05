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
ms.workload: dotnet
ms.openlocfilehash: a4da80d264b05f9c7a1461a7298e521623a97f31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-service-versioning"></a>Instrukcje: Przechowywanie wersji usługi
W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia konfiguracji routingu, który kieruje komunikaty do różnych wersji tę samą usługę. W tym przykładzie wiadomości są kierowane do dwóch różnych wersji usługi Kalkulator `roundingCalc` (wersja 1) i `regularCalc` (v2). Zarówno implementacje obsługują te same operacje; jednak starsza usługa `roundingCalc`, zaokrągla przed zwróceniem wszystkich obliczeń do najbliższej wartości całkowitej. Aplikacja kliencka musi mieć możliwość wskazuje, czy należy użyć nowszej `regularCalc` usługi.  
  
> [!WARNING]
>  Celu kierowania wiadomości do wersji określonej usługi, usługa routingu musi być możliwe ustalenie docelowy komunikatu na podstawie zawartości komunikatu. W metodzie przedstawiona poniżej klient będzie Określ wersję wstawiając informacji w nagłówku wiadomości. Brak metody przechowywanie wersji usługi, które nie wymagają klientów do przekazywania dodatkowych danych. Na przykład komunikat może być kierowane do najbardziej aktualnych lub najbardziej zgodną wersję usługi lub routera można użyć częścią standardowej koperty protokołu SOAP.  
  
 Operacje udostępnianych przez obie te usługi są:  
  
-   Dodaj  
  
-   Odejmowanie  
  
-   Mnożenia  
  
-   Podziel  
  
 Ponieważ obu implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowe dane zawarte w wiadomości wysyłane przez aplikacje klienckie nie jest unikatowa, co pozwala określić sposób kierowania żądanie. Na przykład filtry akcji nie można użyć, ponieważ akcje domyślne obie te usługi są takie same.  
  
 Ten problem można rozwiązać na różne sposoby, takie jak udostępnianie określonego punktu końcowego na routerze dla każdej wersji usługi lub Dodawanie elementu niestandardowego nagłówka do komunikat, aby wskazywać wersję usługi.  Każdy z tych metod umożliwia jednoznacznie kierowania wiadomości przychodzących do określonej wersji usługi, ale przy użyciu zawartość komunikatu unikatowy jest preferowana metoda rozróżnianie między żądań dla różnych wersji dodatku service.  
  
 W tym przykładzie aplikacja kliencka dodaje nagłówek niestandardowy "CalcVer" komunikat żądania. Ten nagłówek będzie zawierać wartość, która wskazuje wersję wiadomości powinny być kierowane do usługi. Wartość "1" wskazuje, że komunikat muszą zostać przetworzone przez usługę roundingCalc, natomiast wartość "2" oznacza usługę regularCalc. Dzięki temu aplikacja kliencka bezpośrednio kontrolować wersji usługi będzie przetwarzać komunikatu.  Ponieważ nagłówek niestandardowy jest wartość zawartych w komunikacie, umożliwia jeden punkt końcowy komunikaty przeznaczone dla obu wersji usługi. Poniższy kod umożliwia w aplikacji klienckiej Dodaj nagłówek niestandardowy komunikat:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Implementowanie przechowywanie wersji usługi  
  
1.  Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi udostępniane przez usługę. W poniższym przykładzie zdefiniowano pojedynczego punktu końcowego, która będzie używana do odbierania wiadomości. Definiuje punkty końcowe klienta, które będą używane do wysyłania wiadomości do `roundingCalc` (wersja 1) i `regularCalc` usługi (v2).  
  
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
  
2.  Zdefiniuj filtry używane do przesyłania wiadomości do punktów końcowych docelowego.  Na przykład filtr XPath jest używana do wykrywania wartość niestandardowego nagłówka "CalcVer" Aby ustalić, która wersja komunikatu powinny być kierowane do. Filtr XPath służy również do wykrywania wiadomości, które nie zawierają nagłówka "CalcVer". W poniższym przykładzie zdefiniowano wymagane filtry i przestrzeni nazw tabeli.  
  
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
    >  Prefiks przestrzeni nazw s12 jest zdefiniowany w tabeli nazw domyślnie i reprezentuje przestrzeni nazw "http://www.w3.org/2003/05/soap-envelope".  
  
3.  Zdefiniuj filtr tabeli, które kojarzy każdego filtru z punktem końcowym klienta. Komunikat zawiera nagłówek "CalcVer" o wartości 1, będą przesyłane do usługi regularCalc. Nagłówek zawiera wartość 2, będą przesyłane do usługi roundingCalc. Jeśli występuje bez nagłówka wiadomości będą kierowane do regularCalc.  
  
     Następujące definiuje tabeli filtrów i dodaje filtry zdefiniowanego wcześniej.  
  
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
  
4.  Aby ocenić wiadomości przychodzących filtry zawartych w tabeli filtru, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu.  W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktów końcowych usługi:  
  
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
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista pliku konfiguracji.  
  
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
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista aplikacji klienckiej.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
