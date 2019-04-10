---
title: 'Instrukcje: Obsługa błędów'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3752e358230b76d8984fa8e6a2ded43ad0eb2c6c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334994"
---
# <a name="how-to-error-handling"></a><span data-ttu-id="78d88-102">Instrukcje: Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="78d88-102">How To: Error Handling</span></span>
<span data-ttu-id="78d88-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, który używa obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="78d88-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="78d88-104">W tym przykładzie komunikaty są kierowane do docelowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78d88-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="78d88-105">Jeśli nie można dostarczyć komunikatu z powodu błędu związanego z komunikacji lub sieci (<xref:System.ServiceModel.CommunicationException>), wiadomości jest wysyłane ponownie do alternatywnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78d88-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78d88-106">Symulowanie awarii sieci, docelowy punkt końcowy, w tym przykładzie zawiera nieprawidłowy adres.</span><span class="sxs-lookup"><span data-stu-id="78d88-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="78d88-107">Wiadomości kierowane do tego niepowodzenia punktu końcowego jako żadna usługa nasłuchuje na określonym adresie.</span><span class="sxs-lookup"><span data-stu-id="78d88-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78d88-108">Podczas przykład zawarte w tym temacie nie omówiono jawnie ustawienia limitu czasu, należy wykonać je pod uwagę podczas korzystania z obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="78d88-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="78d88-109">Gdy wystąpią błędy, nastąpi dodatkowych opóźnień, napotkano zanim klient otrzyma odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="78d88-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="78d88-110">Jest to spowodowane jest błąd w usługa routingu, który próbuje wysłać wiadomość do kopii zapasowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78d88-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="78d88-111">Jeśli wartości limitu czasu skojarzony z podstawowego i zapasowego docelowych punktów końcowych są duże, klienta mogą wystąpić znaczne opóźnienie, jak komunikat przechodzi w trybie Failover wiele punktów końcowych na liście kopii zapasowej przed wysłaniem pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="78d88-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="78d88-112">Ponieważ usługa routingu z tym może wystąpić opóźnienie maksymalna równa sumie wartość limitu czasu dla wszystkich punktów końcowych skojarzonych z filtrem, zaleca się odpowiednio zwiększyć oczekiwanego limit czasu po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="78d88-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="78d88-113">Implementowanie obsługi błędów</span><span class="sxs-lookup"><span data-stu-id="78d88-113">Implement Error Handling</span></span>  
  
1. <span data-ttu-id="78d88-114">Tworzenie podstawowej konfiguracji usługa routingu, określając punkt końcowy usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="78d88-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="78d88-115">Poniższy przykład definiuje pojedynczą usługę punktu końcowego, na który jest używany do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="78d88-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="78d88-116">Umożliwia on również definiowanie punktów końcowych klienta, które są używane do wysyłania wiadomości; deadDestination i realDestination.</span><span class="sxs-lookup"><span data-stu-id="78d88-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="78d88-117">Punkt końcowy deadDestination zawiera adres który nie odwołuje się do uruchomionej usługi i jest używana do symulacji awarii sieci, podczas wysyłania komunikatów do tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78d88-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
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
  
2. <span data-ttu-id="78d88-118">Zdefiniuj filtry używane do przesyłania wiadomości do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="78d88-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="78d88-119">Na przykład filtr MatchAll jest używany do dopasowywania wszystkich komunikatów odebranych przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="78d88-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3. <span data-ttu-id="78d88-120">Zdefiniuj listę kopii zapasowych punktu końcowego, która zawiera punkty końcowe, które wiadomość jest wysyłana do awarii sieci lub komunikacji podczas wysyłania do docelowego podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78d88-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="78d88-121">W poniższym przykładzie zdefiniowano listę kopii zapasowych, która zawiera jeden punkt końcowy; jednak można określić wiele punktów końcowych na liście kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="78d88-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="78d88-122">Jeśli lista kopii zapasowych zawiera wiele punktów końcowych, gdy sieć lub usługa routingu wystąpi awaria łączności próbuje wysłać wiadomość do pierwszego punktu końcowego na liście.</span><span class="sxs-lookup"><span data-stu-id="78d88-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="78d88-123">Jeśli wystąpi awaria sieci lub komunikacji przy wysyłaniu do tego punktu końcowego, usługa routingu próbuje wysłać wiadomość do następnego punktu końcowego znajdujących się na liście.</span><span class="sxs-lookup"><span data-stu-id="78d88-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="78d88-124">Usługa będzie wysyłania komunikatu do każdego punktu końcowego na liście punktów końcowych kopii zapasowej, dopóki pomyślnie wysłania komunikatu, wszystkie punkty końcowe kopii zapasowej zwracają sieci lub w przypadku błąd związany z komunikacji lub komunikat jest wysyłany i poza siecią, zwracany przez punkt końcowy Błąd dotyczące komunikacji.</span><span class="sxs-lookup"><span data-stu-id="78d88-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4. <span data-ttu-id="78d88-125">Definiowanie tabeli filtru, które kojarzy filtr z punktu końcowego deadDestination i listy kopii zapasowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78d88-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="78d88-126">Usługa routingu najpierw próbuje wysłać wiadomość do docelowego punktu końcowego skojarzone z filtrem.</span><span class="sxs-lookup"><span data-stu-id="78d88-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="78d88-127">Ponieważ deadDestination zawiera adres który nie odwołuje się do czynnej usługi, powoduje to błąd sieci.</span><span class="sxs-lookup"><span data-stu-id="78d88-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="78d88-128">Następnie usługa routingu próbuje wysłać wiadomość do punktu końcowego określonego w backupEndpointlist.</span><span class="sxs-lookup"><span data-stu-id="78d88-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
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
  
5. <span data-ttu-id="78d88-129">Aby ocenić komunikaty przychodzące za filtr zawartych w tabeli filtru, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="78d88-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="78d88-130">W poniższym przykładzie pokazano kojarzenie "filterTable1" z punktami końcowymi usługi.</span><span class="sxs-lookup"><span data-stu-id="78d88-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="78d88-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="78d88-131">Example</span></span>  
 <span data-ttu-id="78d88-132">Poniżej przedstawiono pełną listę pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="78d88-132">Following is a complete listing of the configuration file.</span></span>  
  
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
