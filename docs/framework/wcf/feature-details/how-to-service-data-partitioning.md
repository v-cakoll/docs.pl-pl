---
title: 'Instrukcje: Partycjonowanie danych usługi'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300388"
---
# <a name="how-to-service-data-partitioning"></a>Instrukcje: Partycjonowanie danych usługi
W tym temacie przedstawiono podstawowe kroki wymagane do partycji wiadomości na wiele wystąpień tej samej usługi docelowej. Partycjonowanie danych usługi jest zazwyczaj używany w przypadku konieczności skalowania usługi w celu zapewnienia lepszej jakości usługi, lub gdy potrzebujesz do obsługi żądań od innych klientów w określony sposób. Na przykład wiadomości od wysokiej wartości lub klientów "Złota" może być konieczne do przetworzenia na wyższy priorytet niż wiadomości od standardowego klienta.  
  
 W tym przykładzie komunikaty są kierowane do jednej z dwóch wystąpień usługi regularCalc. Oba wystąpienia usługi są identyczne; Jednak usługa reprezentowane przez wiadomości procesy punktu końcowego calculator1 odebrała od klientów o wysokiej wartości, punkt końcowy Kalkulator 2 przetwarzania wiadomości od innych klientów  
  
 Wiadomości wysłanych z klienta nie ma unikatowe dane, który może służyć do identyfikowania wystąpienia usługi, które komunikat powinien być kierowane do. Aby zezwolić na każdym kliencie do kierowania danych do określonego miejsca docelowego usługi wdrażamy dwa punkty końcowe usługi, które będą używane do odbierania komunikatów.  
  
> [!NOTE]
>  Chociaż w tym przykładzie użyto określonych punktów końcowych do partycjonowania danych, to może być również wykonywane przy użyciu informacji zawartych w wiadomości takich jak dane w nagłówku lub w treści.  
  
### <a name="implement-service-data-partitioning"></a>Partycjonowanie danych usługi implementacji  
  
1. Tworzenie podstawowej konfiguracji usługa routingu przez określenie punktów końcowych usługi udostępniane przez usługę. W poniższym przykładzie zdefiniowano dwa punkty końcowe, które będą używane w celu odbierania komunikatów. Definiuje również punkty końcowe klienta, które są używane do wysyłania komunikatów do regularCalc wystąpień usługi.  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2. Zdefiniuj filtry używane do przesyłania wiadomości do docelowych punktów końcowych.  Na przykład filtr Nazwapunktukoncowego jest używany do określenia, które punkt końcowy usługi komunikat. W poniższym przykładzie zdefiniowano niezbędne sekcji routingu i filtry.  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3. Definiowanie tabeli filtru każdy filtr zostanie skojarzony z punktem końcowym klienta. W tym przykładzie będą kierowane komunikat zgodnie z określonego punktu końcowego, który został odebrany przez. Ponieważ komunikat może wyłącznie odpowiadać jednej z dwóch możliwych filtrów, nie ma potrzeby używania priorytet filtru do kontrolowania kolejności, w które filtry są oceniane.  
  
     Poniżej definiuje tabelę filtru i dodaje zdefiniowane wcześniej filtry.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Aby ocenić komunikaty przychodzące filtry zawarte w tabeli, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu. W poniższym przykładzie pokazano kojarzenie "filterTable1" z punktami końcowymi usługi:  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
