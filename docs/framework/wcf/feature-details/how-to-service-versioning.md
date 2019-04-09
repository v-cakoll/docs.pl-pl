---
title: 'Instrukcje: Przechowywanie wersji usługi'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: dc81fcde3c4f731257bf759cbd3f31542483618d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085379"
---
# <a name="how-to-service-versioning"></a>Instrukcje: Przechowywanie wersji usługi
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, które kieruje komunikaty do różnych wersji tej samej usługi. W tym przykładzie komunikaty są kierowane do dwóch różnych wersji usługi Kalkulator `roundingCalc` (wersja 1) i `regularCalc` (v2). Zarówno implementacje obsługują te same operacje; Jednak ze starszej usługi `roundingCalc`, zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Aplikacja kliencka musi być w stanie wskazać, czy skorzystanie z nowszych `regularCalc` usługi.  
  
> [!WARNING]
>  W celu kierowania komunikatu do określonej wersji usługi, usługa routingu musi być możliwe ustalenie, miejsce docelowe komunikat na podstawie zawartości komunikatu. W metodzie, pokazano poniżej klient będzie Określ wersję, wstawiając informacji w nagłówku komunikatu. Istnieją metody przechowywanie wersji usługi, które nie wymagają klientów przekazać dodatkowe dane. Na przykład komunikat może być kierowany do najnowszego lub najbardziej zgodną wersję usługi lub router wystarczą środki w ramach standardowego koperty protokołu SOAP.  
  
 Operacje udostępniane przez obie te usługi są:  
  
-   Dodaj  
  
-   Odejmowanie  
  
-   Mnożenie  
  
-   Dzielenie  
  
 Ponieważ zarówno implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowy dane zawarte w wiadomości wysyłanych z aplikacji klienckich nie jest unikatowy, aby możliwe było określić, jak kierować żądanie. Na przykład nie można użyć filtrów akcji, ponieważ domyślne akcje dla obu usług są takie same.  
  
 Ten problem można rozwiązać na kilka sposobów, takie jak udostępnianie określonego punktu końcowego na routerze dla każdej wersji usługi lub Dodawanie elementu niestandardowego nagłówka do wiadomości wskazania usługi w wersji.  Każda z tych metod pozwala jednoznacznie kierowanie komunikatów przychodzących do określonej wersji usługi, ale korzystanie z zawartości wiadomości unikatowy jest preferowaną metodą rozróżnianiu poszczególnych żądań dla różnych wersji dodatku service.  
  
 W tym przykładzie aplikacja kliencka dodaje niestandardowy nagłówek "CalcVer" komunikat żądania. Ten nagłówek będzie zawierać wartość, która wskazuje wersję komunikat powinien być kierowane do usługi. Wartość "1" wskazuje, że komunikat muszą zostać przetworzone przez usługę roundingCalc, natomiast wartość "2" oznacza usługę regularCalc. Dzięki temu aplikacja kliencka do kontrolowania bezpośrednio, która wersja usługi będzie przetwarzać komunikat.  Ponieważ niestandardowy nagłówek wartości zawarte w wiadomości, można użyć jeden punkt końcowy do odbierania komunikatów przeznaczonych dla obu wersji usługi. Poniższy kod może służyć w aplikacji klienckiej, aby dodać nagłówek niestandardowy komunikat o:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Implementowanie przechowywanie wersji usługi  
  
1.  Tworzenie podstawowej konfiguracji usługa routingu, określając punkt końcowy usługi udostępniane przez usługę. Poniższy przykład definiuje pojedynczą usługę punktu końcowego, na który będzie używany do odbierania komunikatów. Umożliwia on również definiowanie punktów końcowych klienta, które będą używane do wysyłania wiadomości `roundingCalc` (wersja 1) i `regularCalc` services (wersja 2).  
  
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
  
2.  Zdefiniuj filtry używane do przesyłania wiadomości do docelowych punktów końcowych.  W tym przykładzie filtr XPath jest używana wartość niestandardowego nagłówka "CalcVer", aby określić, która wersja komunikatu, powinny być kierowane do wykrywania. Filtr XPath jest również używane do wykrywania wiadomości, które nie zawierają nagłówek "CalcVer". W poniższym przykładzie zdefiniowano wymagane filtry i przestrzeń nazw tabeli.  
  
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
    > Prefiks przestrzeni nazw s12 jest zdefiniowana w przestrzeni nazw tabeli i reprezentuje obszar nazw `http://www.w3.org/2003/05/soap-envelope`.
  
3.  Definiowanie tabeli filtru każdy filtr zostanie skojarzony z punktem końcowym klienta. Jeśli wiadomość zawiera nagłówek "CalcVer" o wartości 1, zostanie wysłany do usługi regularCalc. Nagłówek zawiera wartość 2, będą przesyłane do usługi roundingCalc. Jeśli występuje bez nagłówka wiadomości będą kierowane do regularCalc.  
  
     Poniżej definiuje tabelę filtru i dodaje zdefiniowane wcześniej filtry.  
  
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
  
4.  Aby ocenić komunikaty przychodzące filtry zawartych w tabeli filtru, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu. W poniższym przykładzie pokazano kojarzenie `filterTable1` z punktami końcowymi usługi:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
