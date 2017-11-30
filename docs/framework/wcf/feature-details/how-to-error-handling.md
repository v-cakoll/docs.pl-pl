---
title: "Porady: Obsługa błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5bcab65eb98684820a84968f15ba80de3c5b60de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-error-handling"></a>Porady: Obsługa błędów
W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia konfiguracji routingu, która używa obsługi błędów. W tym przykładzie wiadomości są kierowane do docelowego punktu końcowego. Jeśli nie można dostarczyć komunikatu z powodu sieci lub błąd związany z łączności (<xref:System.ServiceModel.CommunicationException>), wiadomość jest ponowne wysłanie do punktu końcowego alternatywny.  
  
> [!NOTE]
>  Do symulacji awarii sieci, w tym przykładzie docelowego punktu końcowego zawiera niepoprawny adres. Komunikaty kierowane do tego punktu końcowego niepowodzenie jako usługa nie nasłuchuje na określony adres.  
  
> [!NOTE]
>  Gdy przykład zawarte w tym temacie nie omówiono jawnie ustawienia limitu czasu, należy wykonać je pod uwagę przy użyciu obsługi błędów. Gdy zostaną napotkane błędy, można dodatkowym opóźnieniem napotkał zanim klient odbierze odpowiedzi. Jest to spowodowane odebraniu błąd usługi routingu, która podejmuje próbę wysłania wiadomości do zapasowego punktu końcowego. Jeśli wartości limitu czasu skojarzony z punktów końcowych podstawowego i zapasowego docelowej są duże, klient może duże opóźnienie jak wiadomość awaryjnie wiele punktów końcowych na liście kopii zapasowej przed wysłaniem pomyślnie.  
>   
>  Ponieważ usługa routingu mogą napotkać Maksymalne opóźnienie równa sumie wartość limitu czasu dla wszystkich punktów końcowych skojarzonych z filtrem, zaleca się odpowiednio zwiększyć oczekiwanego limit czasu po stronie klienta.  
  
### <a name="implement-error-handling"></a>Implementowanie obsługi błędów  
  
1.  Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi udostępniane przez usługę. W poniższym przykładzie zdefiniowano pojedynczego punktu końcowego, który jest używany do odbierania wiadomości. Definiuje punkty końcowe klienta, które są używane do wysyłania wiadomości. deadDestination i realDestination. Punkt końcowy deadDestination zawiera adres, który nie odwołuje się do uruchomionej usługi i jest używany do symulacji awarii sieci, podczas wysyłania komunikatów do tego punktu końcowego.  
  
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
  
2.  Zdefiniuj filtry używane do przesyłania wiadomości do punktów końcowych docelowego.  Na przykład filtr MatchAll służy do dopasowania wszystkich komunikatów odebranych przez usługę Routing.  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  Zdefiniuj listę zapasowego punktu końcowego, która zawiera punkty końcowe, które jest wysyłany komunikat do awarii sieci lub komunikacji podczas wysyłania do głównej docelowego punktu końcowego. W poniższym przykładzie zdefiniowano listy kopii zapasowych, który zawiera jeden punkt końcowy; Jednak w listy kopii zapasowych można określić wiele punktów końcowych.  
  
     Jeśli listy kopii zapasowych zawiera wiele punktów końcowych, gdy sieć lub usługa routingu wystąpi awaria łączności próbuje wysłać wiadomość na pierwszym punktem końcowym na liście. Jeśli wystąpi błąd sieci lub komunikacji przy wysyłaniu do tego punktu końcowego, usługa routingu próbuje wysłać wiadomość do następnego punktu końcowego zawarte na liście. Usługa będzie wysyłanie komunikatu do każdego punktu końcowego na liście zapasowego punktu końcowego, aż pomyślnie wiadomości jest, wszystkie punkty końcowe kopii zapasowej zwracać sieci lub błąd związany z komunikacji, lub wysłać wiadomości i punktu końcowego zwraca poza siecią, Błąd dotyczące komunikacji.  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  Zdefiniuj filtr tabeli, które kojarzy filtr z punktem końcowym deadDestination i listy zapasowego punktu końcowego.  Usługa routingu najpierw próbuje wysłać wiadomość do docelowego punktu końcowego skojarzone z filtrem. Ponieważ deadDestination zawiera adres, który odwołuje się do uruchomionej usługi, powoduje to błędu sieci. Usługa routingu podejmuje próbę wysłania wiadomości do punktu końcowego określona w backupEndpointlist.  
  
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
  
5.  Aby ocenić wiadomości przychodzących za filtr zawartych w tabeli filtru, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu.  W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktów końcowych usługi.  
  
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
 Poniżej znajduje się pełna lista pliku konfiguracji.  
  
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
            <!-- Add an entrty that maps the MatchAllMessageFilter to the dead destination -->  
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
