---
title: 'Instrukcje: Partycjonowanie danych usługi'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 47e84555e38d2a71b7741c18de5f67349a622798
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491806"
---
# <a name="how-to-service-data-partitioning"></a>Instrukcje: Partycjonowanie danych usługi
W tym temacie przedstawiono podstawowe czynności wymagane do partycji komunikaty w wielu wystąpieniach tej samej usługi docelowej. Partycjonowanie danych usługi jest zwykle używany w przypadku konieczności zmiany skali usługi w celu zapewnienia lepszej jakości usługi lub gdy potrzebne do obsługi żądań od innych klientów w określony sposób. Na przykład wiadomości z wysokiej wartości lub klientów "Złota" może być konieczne przetworzenie na wyższy priorytet niż komunikatów standardowych klienta.  
  
 W tym przykładzie wiadomości są kierowane do jednej z dwóch wystąpień usługi regularCalc. Oba wystąpienia usługi są identyczne; Jednak usługa reprezentowany przez calculator1 punktu końcowego przetwarzania wiadomości odebrała od wysokiej wartości klientów, punkt końcowy Kalkulator 2 procesy wiadomości z innych klientów  
  
 Wiadomości wysłanych z klienta nie ma unikatowe dane, który może służyć do identyfikowania którego wiadomości powinny być kierowane do wystąpienia usługi. Aby umożliwić każdego klienta na przesyłanie danych do określonego miejsca docelowego usługi wprowadzimy dwa punkty końcowe usługi, które będą używane do odbierania wiadomości.  
  
> [!NOTE]
>  Gdy w tym przykładzie użyto określonych punktów końcowych do danych partycji, można to również osiągnąć, korzystając z informacji zawartych w wiadomości takich jak dane w nagłówku lub w treści.  
  
### <a name="implement-service-data-partitioning"></a>Partycjonowanie danych usługi implementacji  
  
1.  Utwórz podstawową konfigurację usługi routingu, podając punktów końcowych usług udostępnianych przez usługę. W poniższym przykładzie zdefiniowano dwa punkty końcowe, które będą używane do odbierania wiadomości. Definiuje punkty końcowe klienta, które są używane do wysyłania komunikatów do regularCalc wystąpień usługi.  
  
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
  
2.  Zdefiniuj filtry używane do przesyłania wiadomości do punktów końcowych docelowego.  Na przykład filtr EndpointName służy do określania, które punkt końcowy usługi odebrał wiadomość. W poniższym przykładzie zdefiniowano niezbędne sekcji routingu i filtry.  
  
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
  
3.  Zdefiniuj filtr tabeli, które kojarzy każdego filtru z punktem końcowym klienta. W tym przykładzie zostaną przesłane wiadomości na podstawie określonych w punkcie końcowym, które zostało przesłane za pośrednictwem. Ponieważ komunikat może dopasować tylko jeden z dwóch możliwych filtrów, nie istnieje potrzeba do sterowania do zlecenia w filtrach, które są oceniane przy użyciu priorytet filtru.  
  
     Następujące definiuje tabeli filtrów i dodaje filtry zdefiniowanego wcześniej.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  Aby ocenić wiadomości przychodzących filtry zawarte w tabeli, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu. W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktów końcowych usługi:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
