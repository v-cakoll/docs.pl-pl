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
# <a name="how-to-error-handling"></a><span data-ttu-id="4057d-102">Instrukcje: obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="4057d-102">How To: Error Handling</span></span>

<span data-ttu-id="4057d-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu korzystającej z obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="4057d-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="4057d-104">W tym przykładzie komunikaty są kierowane do docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4057d-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="4057d-105">Jeśli nie można dostarczyć komunikatu z powodu niepowodzenia sieci lub komunikacji (<xref:System.ServiceModel.CommunicationException>), komunikat jest ponownie wysyłany do alternatywnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4057d-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="4057d-106">Aby symulować awarię sieci, docelowy punkt końcowy użyty w tym przykładzie zawiera nieprawidłowy adres.</span><span class="sxs-lookup"><span data-stu-id="4057d-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="4057d-107">Komunikaty kierowane do tego punktu końcowego nie powiodą się, ponieważ żadna usługa nie nasłuchuje na określonym adresie.</span><span class="sxs-lookup"><span data-stu-id="4057d-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="4057d-108">Chociaż w przykładzie zawartym w tym temacie nie omówiono jawnie ustawień limitu czasu, należy wziąć pod uwagę podczas korzystania z obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="4057d-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="4057d-109">Po napotkaniu błędów zostanie wykryte dodatkowe opóźnienie, zanim klient otrzyma odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4057d-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="4057d-110">Wynika to z faktu, że błąd jest odbierany w usłudze routingu, a następnie próbuje wysłać komunikat do punktu końcowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="4057d-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="4057d-111">Jeśli wartość limitu czasu skojarzona z punktami końcowymi podstawowego i docelowego kopii zapasowej jest duża, klient może wystąpić z długim opóźnieniem, ponieważ komunikat przejdzie do trybu failover w wielu punktach końcowych na liście kopii zapasowych przed pomyślnym wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="4057d-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="4057d-112">Ponieważ usługa routingu może napotkać maksymalne opóźnienie równe sumie wartości limitu czasu dla wszystkich punktów końcowych skojarzonych z filtrem, zalecamy odpowiednio zwiększyć oczekiwany limit czasu na kliencie.</span><span class="sxs-lookup"><span data-stu-id="4057d-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="4057d-113">Zaimplementuj obsługę błędów</span><span class="sxs-lookup"><span data-stu-id="4057d-113">Implement Error Handling</span></span>

1. <span data-ttu-id="4057d-114">Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi uwidoczniony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4057d-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="4057d-115">W poniższym przykładzie zdefiniowano pojedynczy punkt końcowy usługi, który jest używany do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4057d-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="4057d-116">Definiuje również punkty końcowe klienta, które są używane do wysyłania wiadomości; deadDestination i realDestination.</span><span class="sxs-lookup"><span data-stu-id="4057d-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="4057d-117">Punkt końcowy deadDestination zawiera adres, który nie odwołuje się do działającej usługi i służy do symulowania awarii sieci podczas wysyłania komunikatów do tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4057d-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

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

2. <span data-ttu-id="4057d-118">Zdefiniuj filtry służące do kierowania komunikatów do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4057d-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="4057d-119">W tym przykładzie filtr MatchAll jest używany do dopasowania wszystkich komunikatów odebranych przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="4057d-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="4057d-120">Zdefiniuj listę punktów końcowych kopii zapasowych, która zawiera punkty końcowe, do których komunikat jest wysyłany w przypadku awarii sieci lub komunikacji podczas wysyłania do podstawowego docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4057d-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="4057d-121">W poniższym przykładzie zdefiniowano listę kopii zapasowych, która zawiera jeden punkt końcowy; na liście kopii zapasowych można jednak określić wiele punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4057d-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="4057d-122">Jeśli lista kopii zapasowych zawiera wiele punktów końcowych, gdy wystąpi awaria sieci lub komunikacji, usługa routingu próbuje wysłać komunikat do pierwszego punktu końcowego na liście.</span><span class="sxs-lookup"><span data-stu-id="4057d-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="4057d-123">Jeśli podczas wysyłania do tego punktu końcowego wystąpi awaria sieci lub komunikacji, usługa routingu podejmie próbę wysłania komunikatu do następnego punktu końcowego znajdującego się na liście.</span><span class="sxs-lookup"><span data-stu-id="4057d-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="4057d-124">Usługa kontynuuje Wysyłanie komunikatu do każdego punktu końcowego na liście punktów końcowych kopii zapasowej do momentu jego pomyślnego wysłania, wszystkie punkty końcowe kopii zapasowej zwracają błąd sieciowy lub związany z komunikacją, a komunikat jest wysyłany, a punkt końcowy zwraca niesieć. błąd niezwiązany z komunikacją.</span><span class="sxs-lookup"><span data-stu-id="4057d-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="4057d-125">Zdefiniuj tabelę filtrów, która kojarzy filtr z punktem końcowym deadDestination oraz listą punktów końcowych kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="4057d-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="4057d-126">Usługa routingu najpierw próbuje wysłać komunikat do docelowego punktu końcowego skojarzonego z filtrem.</span><span class="sxs-lookup"><span data-stu-id="4057d-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="4057d-127">Ponieważ deadDestination zawiera adres, który nie odwołuje się do działającej usługi, spowoduje to błąd sieciowy.</span><span class="sxs-lookup"><span data-stu-id="4057d-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="4057d-128">Następnie usługa routingu próbuje wysłać komunikat do punktu końcowego określonego w backupEndpointList.</span><span class="sxs-lookup"><span data-stu-id="4057d-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

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

5. <span data-ttu-id="4057d-129">Aby oszacować komunikaty przychodzące względem filtru zawartego w tabeli filtrów, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="4057d-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="4057d-130">Poniższy przykład demonstruje kojarzenie "filterTable1" z punktami końcowymi usługi.</span><span class="sxs-lookup"><span data-stu-id="4057d-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

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

## <a name="example"></a><span data-ttu-id="4057d-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="4057d-131">Example</span></span>

<span data-ttu-id="4057d-132">Poniżej znajduje się kompletna lista plików konfiguracyjnych:</span><span class="sxs-lookup"><span data-stu-id="4057d-132">The following is a complete listing of the configuration file:</span></span>

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
