---
title: 'Instrukcje: Obsługa błędów'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 4958e7914d9feb32dc00d11a215cf8247e9baffc
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424603"
---
# <a name="how-to-error-handling"></a>Instrukcje: Obsługa błędów

W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, który używa obsługi błędów. W tym przykładzie komunikaty są kierowane do docelowego punktu końcowego. Jeśli nie można dostarczyć komunikatu z powodu błędu związanego z komunikacji lub sieci (<xref:System.ServiceModel.CommunicationException>), wiadomości jest wysyłane ponownie do alternatywnego punktu końcowego.

> [!NOTE]
> Symulowanie awarii sieci, docelowy punkt końcowy, w tym przykładzie zawiera nieprawidłowy adres. Wiadomości kierowane do tego niepowodzenia punktu końcowego jako żadna usługa nasłuchuje na określonym adresie.

> [!NOTE]
> Podczas przykład zawarte w tym temacie nie omówiono jawnie ustawienia limitu czasu, należy wykonać je pod uwagę podczas korzystania z obsługi błędów. Gdy wystąpią błędy, nastąpi dodatkowych opóźnień, napotkano zanim klient otrzyma odpowiedź. Jest to spowodowane jest błąd w usługa routingu, który próbuje wysłać wiadomość do kopii zapasowej punktu końcowego. Jeśli wartości limitu czasu skojarzony z podstawowego i zapasowego docelowych punktów końcowych są duże, klienta mogą wystąpić znaczne opóźnienie, jak komunikat przechodzi w trybie Failover wiele punktów końcowych na liście kopii zapasowej przed wysłaniem pomyślnie.
>
> Ponieważ usługa routingu z tym może wystąpić opóźnienie maksymalna równa sumie wartość limitu czasu dla wszystkich punktów końcowych skojarzonych z filtrem, zaleca się odpowiednio zwiększyć oczekiwanego limit czasu po stronie klienta.

### <a name="implement-error-handling"></a>Implementowanie obsługi błędów

1. Tworzenie podstawowej konfiguracji usługa routingu, określając punkt końcowy usługi udostępniane przez usługę. Poniższy przykład definiuje pojedynczą usługę punktu końcowego, na który jest używany do odbierania komunikatów. Umożliwia on również definiowanie punktów końcowych klienta, które są używane do wysyłania wiadomości; deadDestination i realDestination. Punkt końcowy deadDestination zawiera adres który nie odwołuje się do uruchomionej usługi i jest używana do symulacji awarii sieci, podczas wysyłania komunikatów do tego punktu końcowego.

    ```xml
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>

    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    ```

2. Zdefiniuj filtry używane do przesyłania wiadomości do docelowych punktów końcowych.  Na przykład filtr MatchAll jest używany do dopasowywania wszystkich komunikatów odebranych przez usługę routingu.

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. Zdefiniuj listę kopii zapasowych punktu końcowego, która zawiera punkty końcowe, które wiadomość jest wysyłana do awarii sieci lub komunikacji podczas wysyłania do docelowego podstawowego punktu końcowego. W poniższym przykładzie zdefiniowano listę kopii zapasowych, która zawiera jeden punkt końcowy; jednak można określić wiele punktów końcowych na liście kopii zapasowych.

     Jeśli lista kopii zapasowych zawiera wiele punktów końcowych, gdy sieć lub usługa routingu wystąpi awaria łączności próbuje wysłać wiadomość do pierwszego punktu końcowego na liście. Jeśli wystąpi awaria sieci lub komunikacji przy wysyłaniu do tego punktu końcowego, usługa routingu próbuje wysłać wiadomość do następnego punktu końcowego znajdujących się na liście. Usługa będzie wysyłania komunikatu do każdego punktu końcowego na liście punktów końcowych kopii zapasowej, dopóki pomyślnie wysłania komunikatu, wszystkie punkty końcowe kopii zapasowej zwracają sieci lub w przypadku błąd związany z komunikacji lub komunikat jest wysyłany i poza siecią, zwracany przez punkt końcowy Błąd dotyczące komunikacji.

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. Definiowanie tabeli filtru, które kojarzy filtr z punktu końcowego deadDestination i listy kopii zapasowej punktu końcowego.  Usługa routingu najpierw próbuje wysłać wiadomość do docelowego punktu końcowego skojarzone z filtrem. Ponieważ deadDestination zawiera adres który nie odwołuje się do czynnej usługi, powoduje to błąd sieci. Następnie usługa routingu próbuje wysłać wiadomość do punktu końcowego określonego w backupEndpointList.

    ```xml
    <filterTables>
            <!-- Set up the Routing Service's Message Filter Table -->
            <filterTable name="filterTable1">
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
                <!-- Listed in the backupEndpointList -->
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
            </filterTable>
          </filterTables>
    ```

5. Aby ocenić komunikaty przychodzące za filtr zawartych w tabeli filtru, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu.  W poniższym przykładzie pokazano kojarzenie "filterTable1" z punktami końcowymi usługi.

    ```xml
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>Przykład

Poniżej przedstawiono pełną listę pliku konfiguracji.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    <routing>
      <filters>
        <!-- Create a MatchAll filter which will catch all messages -->
        <filter name="MatchAllFilter1" filterType="MatchAll" />
      </filters>
      <filterTables>
        <!-- Set up the Routing Service's Message Filter Table -->
        <filterTable name="filterTable1">
            <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
            <!-- Listed in the backupEndpointList -->
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
        </filterTable>
      </filterTables>
      <!-- Create the backup endpoint list -->
      <backupLists>
        <backupList name="backupEndpointList">
            <add endpointName="realDestination" />
        </backupList>
      </backupLists>
      </routing>
  </system.serviceModel>
</configuration>
```
