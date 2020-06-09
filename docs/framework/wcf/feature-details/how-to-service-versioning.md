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
# <a name="how-to-service-versioning"></a>Instrukcje: Przechowywanie wersji usługi
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, która kieruje komunikaty do różnych wersji tej samej usługi. W tym przykładzie komunikaty są kierowane do dwóch różnych wersji usługi kalkulatora `roundingCalc` (v1) i `regularCalc` (v2). Obie implementacje obsługują te same operacje; jednak Starsza usługa, `roundingCalc` zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Aplikacja kliencka musi być w stanie wskazać, czy ma być używana nowsza `regularCalc` Usługa.  
  
> [!WARNING]
> Aby można było skierować komunikat do określonej wersji usługi, usługa routingu musi być w stanie określić miejsce docelowe wiadomości na podstawie zawartości komunikatu. W poniższej metodzie klient określi wersję, wstawiając informacje do nagłówka komunikatu. Istnieją metody obsługi wersji usługi, które nie wymagają od klientów przekazywania dodatkowych danych. Na przykład komunikat może być kierowany do najnowszej lub najbardziej zgodnej wersji usługi lub router może użyć części standardowej koperty protokołu SOAP.  
  
 Operacje udostępniane przez obie usługi są następujące:  
  
- Dodaj  
  
- Odejmowanie  
  
- Mnożenie  
  
- Dzielenie  
  
 Ponieważ oba implementacje usług obsługują te same operacje i są zasadniczo identyczne jak dane, które zwracają, dane podstawowe zawarte w komunikatach wysyłanych z aplikacji klienckich nie są wystarczająco unikatowe, aby umożliwić określenie sposobu kierowania żądania. Na przykład filtry akcji nie mogą być używane, ponieważ domyślne akcje obu usług są takie same.  
  
 Można to rozwiązać na kilka sposobów, takich jak ujawnienie określonego punktu końcowego na routerze dla każdej wersji usługi lub dodanie niestandardowego elementu nagłówka do komunikatu w celu wskazania wersji usługi.  Każdy z tych metod umożliwia jednoznaczne kierowanie komunikatów przychodzących do określonej wersji usługi, ale używanie unikatowej zawartości komunikatów jest preferowaną metodą rozróżniania między żądaniami dla różnych wersji usługi.  
  
 W tym przykładzie aplikacja kliencka dodaje niestandardowy nagłówek "CalcVer" do komunikatu żądania. Ten nagłówek będzie zawierać wartość wskazującą wersję usługi, do której ma być kierowany komunikat. Wartość "1" wskazuje, że komunikat musi być przetwarzany przez usługę roundingCalc, podczas gdy wartość "2" wskazuje usługę regularCalc. Dzięki temu aplikacja kliencka może bezpośrednio kontrolować, która wersja usługi będzie przetwarzać komunikat.  Ponieważ nagłówek niestandardowy jest wartością znajdującą się w komunikacie, można użyć jednego punktu końcowego do odbierania komunikatów przeznaczonych dla obu wersji usługi. Poniższy kod może być używany w aplikacji klienckiej w celu dodania tego niestandardowego nagłówka do wiadomości:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Implementowanie obsługi wersji usługi  
  
1. Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi uwidoczniony przez usługę. W poniższym przykładzie zdefiniowano pojedynczy punkt końcowy usługi, który będzie używany do odbierania komunikatów. Definiuje również punkty końcowe klienta, które będą używane do wysyłania komunikatów do `roundingCalc` (v1) i `regularCalc` (v2) usług.  
  
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
  
2. Zdefiniuj filtry służące do kierowania komunikatów do docelowych punktów końcowych.  W tym przykładzie filtr XPath służy do wykrywania wartości niestandardowego nagłówka "CalcVer" w celu określenia wersji, do której ma być kierowany komunikat. Filtr XPath służy również do wykrywania komunikatów, które nie zawierają nagłówka "CalcVer". W poniższym przykładzie zdefiniowano wymagane filtry i tabelę przestrzeni nazw.  
  
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
    > Prefiks przestrzeni nazw S12 jest definiowany domyślnie w tabeli przestrzeni nazw i reprezentuje przestrzeń nazw `http://www.w3.org/2003/05/soap-envelope` .
  
3. Zdefiniuj tabelę filtrów, która kojarzy każdy filtr z punktem końcowym klienta. Jeśli komunikat zawiera nagłówek "CalcVer" o wartości 1, zostanie on wysłany do usługi regularCalc. Jeśli nagłówek zawiera wartość 2, zostanie wysłany do usługi roundingCalc. Jeśli nagłówek nie jest obecny, komunikat zostanie rozesłany do regularCalc.  
  
     Poniższy schemat definiuje tabelę filtrów i dodaje filtry zdefiniowane wcześniej.  
  
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
  
4. Aby oszacować komunikaty przychodzące względem filtrów zawartych w tabeli filtrów, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu. Poniższy przykład ilustruje kojarzenie `filterTable1` z punktami końcowymi usługi:  
  
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
 Poniżej znajduje się kompletna lista plików konfiguracyjnych.  
  
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
 Poniżej znajduje się kompletna lista aplikacji klienckich.  
  
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

- [Usługi routingu](../samples/routing-services.md)
