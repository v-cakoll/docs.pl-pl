---
title: "Instrukcje: Partycjonowanie danych usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 7104aa2fee49a21dab7fcc8392a9d4bb291203fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="35da0-102">Instrukcje: Partycjonowanie danych usługi</span><span class="sxs-lookup"><span data-stu-id="35da0-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="35da0-103">W tym temacie przedstawiono podstawowe czynności wymagane do partycji komunikaty w wielu wystąpieniach tej samej usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="35da0-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="35da0-104">Partycjonowanie danych usługi jest zwykle używany w przypadku konieczności zmiany skali usługi w celu zapewnienia lepszej jakości usługi lub gdy potrzebne do obsługi żądań od innych klientów w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="35da0-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="35da0-105">Na przykład wiadomości z wysokiej wartości lub klientów "Złota" może być konieczne przetworzenie na wyższy priorytet niż komunikatów standardowych klienta.</span><span class="sxs-lookup"><span data-stu-id="35da0-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="35da0-106">W tym przykładzie wiadomości są kierowane do jednej z dwóch wystąpień usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="35da0-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="35da0-107">Oba wystąpienia usługi są identyczne; Jednak usługa reprezentowany przez calculator1 punktu końcowego przetwarzania wiadomości odebrała od wysokiej wartości klientów, punkt końcowy Kalkulator 2 procesy wiadomości z innych klientów</span><span class="sxs-lookup"><span data-stu-id="35da0-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="35da0-108">Wiadomości wysłanych z klienta nie ma unikatowe dane, który może służyć do identyfikowania którego wiadomości powinny być kierowane do wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="35da0-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="35da0-109">Aby umożliwić każdego klienta na przesyłanie danych do określonego miejsca docelowego usługi wprowadzimy dwa punkty końcowe usługi, które będą używane do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35da0-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35da0-110">Gdy w tym przykładzie użyto określonych punktów końcowych do danych partycji, można to również osiągnąć, korzystając z informacji zawartych w wiadomości takich jak dane w nagłówku lub w treści.</span><span class="sxs-lookup"><span data-stu-id="35da0-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="35da0-111">Partycjonowanie danych usługi implementacji</span><span class="sxs-lookup"><span data-stu-id="35da0-111">Implement Service Data Partitioning</span></span>  
  
1.  <span data-ttu-id="35da0-112">Utwórz podstawową konfigurację usługi routingu, podając punktów końcowych usług udostępnianych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="35da0-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="35da0-113">W poniższym przykładzie zdefiniowano dwa punkty końcowe, które będą używane do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35da0-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="35da0-114">Definiuje punkty końcowe klienta, które są używane do wysyłania komunikatów do regularCalc wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="35da0-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2.  <span data-ttu-id="35da0-115">Zdefiniuj filtry używane do przesyłania wiadomości do punktów końcowych docelowego.</span><span class="sxs-lookup"><span data-stu-id="35da0-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="35da0-116">Na przykład filtr EndpointName służy do określania, które punkt końcowy usługi odebrał wiadomość.</span><span class="sxs-lookup"><span data-stu-id="35da0-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="35da0-117">W poniższym przykładzie zdefiniowano niezbędne sekcji routingu i filtry.</span><span class="sxs-lookup"><span data-stu-id="35da0-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3.  <span data-ttu-id="35da0-118">Zdefiniuj filtr tabeli, które kojarzy każdego filtru z punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="35da0-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="35da0-119">W tym przykładzie zostaną przesłane wiadomości na podstawie określonych w punkcie końcowym, które zostało przesłane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="35da0-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="35da0-120">Ponieważ komunikat może dopasować tylko jeden z dwóch możliwych filtrów, nie istnieje potrzeba do sterowania do zlecenia w filtrach, które są oceniane przy użyciu priorytet filtru.</span><span class="sxs-lookup"><span data-stu-id="35da0-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="35da0-121">Następujące definiuje tabeli filtrów i dodaje filtry zdefiniowanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="35da0-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="35da0-122">Aby ocenić wiadomości przychodzących filtry zawarte w tabeli, należy skojarzyć tabeli filtrów z punktów końcowych usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="35da0-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="35da0-123">W poniższym przykładzie pokazano kojarzenia "filterTable1" z punktów końcowych usługi:</span><span class="sxs-lookup"><span data-stu-id="35da0-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="35da0-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="35da0-124">Example</span></span>  
 <span data-ttu-id="35da0-125">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35da0-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35da0-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35da0-126">See Also</span></span>  
 [<span data-ttu-id="35da0-127">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="35da0-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
