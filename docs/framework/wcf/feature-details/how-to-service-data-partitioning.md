---
title: 'Instrukcje: Partycjonowanie danych usługi'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 3b2f86ee6a4dea25fb5c972d4cecb1b9ed411b29
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601195"
---
# <a name="how-to-service-data-partitioning"></a>Instrukcje: Partycjonowanie danych usługi
W tym temacie przedstawiono podstawowe kroki wymagane do dzielenia komunikatów między wiele wystąpień tej samej usługi docelowej. Partycjonowanie danych usługi jest zwykle używane, gdy konieczne jest skalowanie usługi w celu zapewnienia lepszej jakości usług lub w przypadku konieczności obsługi żądań od różnych klientów w określony sposób. Na przykład komunikaty z klientów o wysokiej wartości lub "Gold" mogą wymagać przetworzenia na wyższym priorytecie niż komunikaty od standardowego klienta.  
  
 W tym przykładzie komunikaty są kierowane do jednego z dwóch wystąpień usługi regularCalc. Oba wystąpienia usługi są identyczne; Jednak usługa reprezentowana przez punkt końcowy calculator1 przetwarza wiadomości odebrane od klientów o dużej wartości, punkt końcowy kalkulatora 2 przetwarza komunikaty od innych klientów  
  
 Komunikat wysłany z klienta nie zawiera żadnych unikatowych danych, których można użyć do zidentyfikowania wystąpienia usługi, do którego wiadomość powinna być kierowana. Aby umożliwić każdemu klientowi kierowanie danych do określonej usługi docelowej, zostaną zaimplementowane dwa punkty końcowe usługi, które będą używane do odbierania komunikatów.  
  
> [!NOTE]
> Chociaż w tym przykładzie użyto określonych punktów końcowych do partycjonowania danych, można to również zrobić przy użyciu informacji zawartych w komunikacie, na przykład nagłówka lub danych treści.  
  
### <a name="implement-service-data-partitioning"></a>Implementowanie partycjonowania danych usługi  
  
1. Utwórz podstawową konfigurację usługi routingu, określając punkty końcowe usługi udostępniane przez usługę. W poniższym przykładzie zdefiniowano dwa punkty końcowe, które będą używane do odbierania komunikatów. Definiuje również punkty końcowe klienta, które są używane do wysyłania komunikatów do wystąpień usługi regularCalc.  
  
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
  
2. Zdefiniuj filtry służące do kierowania komunikatów do docelowych punktów końcowych.  W tym przykładzie filtr EndpointName służy do określenia, który punkt końcowy usługi odebrał komunikat. W poniższym przykładzie zdefiniowano niezbędną sekcję routingu i filtry.  
  
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
  
3. Zdefiniuj tabelę filtrów, która kojarzy każdy filtr z punktem końcowym klienta. W tym przykładzie komunikat zostanie rozesłany na podstawie określonego punktu końcowego, który został odebrany. Ponieważ komunikat może pasować tylko do jednego z dwóch możliwych filtrów, nie ma potrzeby używania priorytetu filtru do kontrolowania kolejności, w której są oceniane filtry.  
  
     Poniższy schemat definiuje tabelę filtrów i dodaje filtry zdefiniowane wcześniej.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Aby oszacować komunikaty przychodzące względem filtrów zawartych w tabeli, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu. Poniższy przykład demonstruje kojarzenie "filterTable1" z punktami końcowymi usługi:  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Usługi routingu](../samples/routing-services.md)
