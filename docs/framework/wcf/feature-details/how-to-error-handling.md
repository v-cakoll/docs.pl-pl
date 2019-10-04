---
title: 'Instrukcje: obsługa błędów'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3b8e48a74ff7671b942b5499fb3a0b5d0f389d61
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834713"
---
# <a name="how-to-error-handling"></a>Instrukcje: obsługa błędów

W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu korzystającej z obsługi błędów. W tym przykładzie komunikaty są kierowane do docelowego punktu końcowego. Jeśli nie można dostarczyć komunikatu z powodu niepowodzenia sieci lub komunikacji (<xref:System.ServiceModel.CommunicationException>), komunikat jest ponownie wysyłany do alternatywnego punktu końcowego.

> [!NOTE]
> Aby symulować awarię sieci, docelowy punkt końcowy użyty w tym przykładzie zawiera nieprawidłowy adres. Komunikaty kierowane do tego punktu końcowego nie powiodą się, ponieważ żadna usługa nie nasłuchuje na określonym adresie.

> [!NOTE]
> Chociaż w przykładzie zawartym w tym temacie nie omówiono jawnie ustawień limitu czasu, należy wziąć pod uwagę podczas korzystania z obsługi błędów. Po napotkaniu błędów zostanie wykryte dodatkowe opóźnienie, zanim klient otrzyma odpowiedź. Wynika to z faktu, że błąd jest odbierany w usłudze routingu, a następnie próbuje wysłać komunikat do punktu końcowego kopii zapasowej. Jeśli wartość limitu czasu skojarzona z punktami końcowymi podstawowego i docelowego kopii zapasowej jest duża, klient może wystąpić z długim opóźnieniem, ponieważ komunikat przejdzie do trybu failover w wielu punktach końcowych na liście kopii zapasowych przed pomyślnym wysłaniem.
>
> Ponieważ usługa routingu może napotkać maksymalne opóźnienie równe sumie wartości limitu czasu dla wszystkich punktów końcowych skojarzonych z filtrem, zalecamy odpowiednio zwiększyć oczekiwany limit czasu na kliencie.

### <a name="implement-error-handling"></a>Zaimplementuj obsługę błędów

1. Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi uwidoczniony przez usługę. W poniższym przykładzie zdefiniowano pojedynczy punkt końcowy usługi, który jest używany do odbierania komunikatów. Definiuje również punkty końcowe klienta, które są używane do wysyłania wiadomości; deadDestination i realDestination. Punkt końcowy deadDestination zawiera adres, który nie odwołuje się do działającej usługi i służy do symulowania awarii sieci podczas wysyłania komunikatów do tego punktu końcowego.

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

2. Zdefiniuj filtry służące do kierowania komunikatów do docelowych punktów końcowych.  W tym przykładzie filtr MatchAll jest używany do dopasowania wszystkich komunikatów odebranych przez usługę routingu.

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. Zdefiniuj listę punktów końcowych kopii zapasowych, która zawiera punkty końcowe, do których komunikat jest wysyłany w przypadku awarii sieci lub komunikacji podczas wysyłania do podstawowego docelowego punktu końcowego. W poniższym przykładzie zdefiniowano listę kopii zapasowych, która zawiera jeden punkt końcowy; na liście kopii zapasowych można jednak określić wiele punktów końcowych.

     Jeśli lista kopii zapasowych zawiera wiele punktów końcowych, gdy wystąpi awaria sieci lub komunikacji, usługa routingu próbuje wysłać komunikat do pierwszego punktu końcowego na liście. Jeśli podczas wysyłania do tego punktu końcowego wystąpi awaria sieci lub komunikacji, usługa routingu podejmie próbę wysłania komunikatu do następnego punktu końcowego znajdującego się na liście. Usługa kontynuuje Wysyłanie komunikatu do każdego punktu końcowego na liście punktów końcowych kopii zapasowej do momentu jego pomyślnego wysłania, wszystkie punkty końcowe kopii zapasowej zwracają błąd sieciowy lub związany z komunikacją, a komunikat jest wysyłany, a punkt końcowy zwraca niesieć. błąd niezwiązany z komunikacją.

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. Zdefiniuj tabelę filtrów, która kojarzy filtr z punktem końcowym deadDestination oraz listą punktów końcowych kopii zapasowych.  Usługa routingu najpierw próbuje wysłać komunikat do docelowego punktu końcowego skojarzonego z filtrem. Ponieważ deadDestination zawiera adres, który nie odwołuje się do działającej usługi, spowoduje to błąd sieciowy. Następnie usługa routingu próbuje wysłać komunikat do punktu końcowego określonego w backupEndpointList.

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

5. Aby oszacować komunikaty przychodzące względem filtru zawartego w tabeli filtrów, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu.  Poniższy przykład demonstruje kojarzenie "filterTable1" z punktami końcowymi usługi.

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

Poniżej znajduje się kompletna lista plików konfiguracyjnych:

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
