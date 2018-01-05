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
ms.workload: dotnet
ms.openlocfilehash: a5b0fe57bb6a4604c86e63a154e3af5542672912
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-error-handling"></a><span data-ttu-id="871b4-102">Porady: Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="871b4-102">How To: Error Handling</span></span>
<span data-ttu-id="871b4-103">W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia konfiguracji routingu, która używa obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="871b4-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="871b4-104">W tym przykładzie wiadomości są kierowane do docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="871b4-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="871b4-105">Jeśli nie można dostarczyć komunikatu z powodu sieci lub błąd związany z łączności (<xref:System.ServiceModel.CommunicationException>), wiadomość jest ponowne wysłanie do punktu końcowego alternatywny.</span><span class="sxs-lookup"><span data-stu-id="871b4-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="871b4-106">Do symulacji awarii sieci, w tym przykładzie docelowego punktu końcowego zawiera niepoprawny adres.</span><span class="sxs-lookup"><span data-stu-id="871b4-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="871b4-107">Komunikaty kierowane do tego punktu końcowego niepowodzenie jako usługa nie nasłuchuje na określony adres.</span><span class="sxs-lookup"><span data-stu-id="871b4-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="871b4-108">Gdy przykład zawarte w tym temacie nie omówiono jawnie ustawienia limitu czasu, należy wykonać je pod uwagę przy użyciu obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="871b4-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="871b4-109">Gdy zostaną napotkane błędy, można dodatkowym opóźnieniem napotkał zanim klient odbierze odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="871b4-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="871b4-110">Jest to spowodowane odebraniu błąd usługi routingu, która podejmuje próbę wysłania wiadomości do zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="871b4-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="871b4-111">Jeśli wartości limitu czasu skojarzony z punktów końcowych podstawowego i zapasowego docelowej są duże, klient może duże opóźnienie jak wiadomość awaryjnie wiele punktów końcowych na liście kopii zapasowej przed wysłaniem pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="871b4-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="871b4-112">Ponieważ usługa routingu mogą napotkać Maksymalne opóźnienie równa sumie wartość limitu czasu dla wszystkich punktów końcowych skojarzonych z filtrem, zaleca się odpowiednio zwiększyć oczekiwanego limit czasu po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="871b4-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="871b4-113">Implementowanie obsługi błędów</span><span class="sxs-lookup"><span data-stu-id="871b4-113">Implement Error Handling</span></span>  
  
1.  <span data-ttu-id="871b4-114">Utwórz podstawową konfigurację usługi routingu, określając punkt końcowy usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="871b4-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="871b4-115">W poniższym przykładzie zdefiniowano pojedynczego punktu końcowego, który jest używany do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="871b4-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="871b4-116">Definiuje punkty końcowe klienta, które są używane do wysyłania wiadomości. deadDestination i realDestination.</span><span class="sxs-lookup"><span data-stu-id="871b4-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="871b4-117">Punkt końcowy deadDestination zawiera adres, który nie odwołuje się do uruchomionej usługi i jest używany do symulacji awarii sieci, podczas wysyłania komunikatów do tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="871b4-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
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
  
2.  <span data-ttu-id="871b4-118">Zdefiniuj filtry używane do przesyłania wiadomości do punktów końcowych docelowego.</span><span class="sxs-lookup"><span data-stu-id="871b4-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="871b4-119">Na przykład filtr MatchAll służy do dopasowania wszystkich komunikatów odebranych przez usługę Routing.</span><span class="sxs-lookup"><span data-stu-id="871b4-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  <span data-ttu-id="871b4-120">Zdefiniuj listę zapasowego punktu końcowego, która zawiera punkty końcowe, które jest wysyłany komunikat do awarii sieci lub komunikacji podczas wysyłania do głównej docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="871b4-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="871b4-121">W poniższym przykładzie zdefiniowano listy kopii zapasowych, który zawiera jeden punkt końcowy; Jednak w listy kopii zapasowych można określić wiele punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="871b4-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="871b4-122">Jeśli listy kopii zapasowych zawiera wiele punktów końcowych, gdy sieć lub usługa routingu wystąpi awaria łączności próbuje wysłać wiadomość na pierwszym punktem końcowym na liście.</span><span class="sxs-lookup"><span data-stu-id="871b4-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="871b4-123">Jeśli wystąpi błąd sieci lub komunikacji przy wysyłaniu do tego punktu końcowego, usługa routingu próbuje wysłać wiadomość do następnego punktu końcowego zawarte na liście.</span><span class="sxs-lookup"><span data-stu-id="871b4-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="871b4-124">Usługa będzie wysyłanie komunikatu do każdego punktu końcowego na liście zapasowego punktu końcowego, aż pomyślnie wiadomości jest, wszystkie punkty końcowe kopii zapasowej zwracać sieci lub błąd związany z komunikacji, lub wysłać wiadomości i punktu końcowego zwraca poza siecią, Błąd dotyczące komunikacji.</span><span class="sxs-lookup"><span data-stu-id="871b4-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  <span data-ttu-id="871b4-125">Zdefiniuj filtr tabeli, które kojarzy filtr z punktem końcowym deadDestination i listy zapasowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="871b4-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="871b4-126">Usługa routingu najpierw próbuje wysłać wiadomość do docelowego punktu końcowego skojarzone z filtrem.</span><span class="sxs-lookup"><span data-stu-id="871b4-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="871b4-127">Ponieważ deadDestination zawiera adres, który odwołuje się do uruchomionej usługi, powoduje to błędu sieci.</span><span class="sxs-lookup"><span data-stu-id="871b4-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="871b4-128">Usługa routingu podejmuje próbę wysłania wiadomości do punktu końcowego określona w backupEndpointlist.</span><span class="sxs-lookup"><span data-stu-id="871b4-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
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
  
5.  <span data-ttu-id="871b4-129">Aby ocenić wiadomości przychodzących za filtr zawartych w tabeli filtru, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="871b4-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="871b4-130">W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="871b4-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="871b4-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="871b4-131">Example</span></span>  
 <span data-ttu-id="871b4-132">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="871b4-132">Following is a complete listing of the configuration file.</span></span>  
  
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
