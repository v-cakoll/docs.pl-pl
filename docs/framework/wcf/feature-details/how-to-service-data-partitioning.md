---
title: 'Instrukcje: Partycjonowanie danych usługi'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 49aefd88d73732a139a79f8c53d5beca44d4d4ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947874"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="92fc8-102">Instrukcje: Partycjonowanie danych usługi</span><span class="sxs-lookup"><span data-stu-id="92fc8-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="92fc8-103">W tym temacie przedstawiono podstawowe kroki wymagane do dzielenia komunikatów między wiele wystąpień tej samej usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="92fc8-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="92fc8-104">Partycjonowanie danych usługi jest zwykle używane, gdy konieczne jest skalowanie usługi w celu zapewnienia lepszej jakości usług lub w przypadku konieczności obsługi żądań od różnych klientów w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="92fc8-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="92fc8-105">Na przykład komunikaty z klientów o wysokiej wartości lub "Gold" mogą wymagać przetworzenia na wyższym priorytecie niż komunikaty od standardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="92fc8-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="92fc8-106">W tym przykładzie komunikaty są kierowane do jednego z dwóch wystąpień usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="92fc8-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="92fc8-107">Oba wystąpienia usługi są identyczne; Jednak usługa reprezentowana przez punkt końcowy calculator1 przetwarza wiadomości odebrane od klientów o dużej wartości, punkt końcowy kalkulatora 2 przetwarza komunikaty od innych klientów</span><span class="sxs-lookup"><span data-stu-id="92fc8-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="92fc8-108">Komunikat wysłany z klienta nie zawiera żadnych unikatowych danych, których można użyć do zidentyfikowania wystąpienia usługi, do którego wiadomość powinna być kierowana.</span><span class="sxs-lookup"><span data-stu-id="92fc8-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="92fc8-109">Aby umożliwić każdemu klientowi kierowanie danych do określonej usługi docelowej, zostaną zaimplementowane dwa punkty końcowe usługi, które będą używane do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="92fc8-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92fc8-110">Chociaż w tym przykładzie użyto określonych punktów końcowych do partycjonowania danych, można to również zrobić przy użyciu informacji zawartych w komunikacie, na przykład nagłówka lub danych treści.</span><span class="sxs-lookup"><span data-stu-id="92fc8-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="92fc8-111">Implementowanie partycjonowania danych usługi</span><span class="sxs-lookup"><span data-stu-id="92fc8-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="92fc8-112">Utwórz podstawową konfigurację usługi routingu, określając punkty końcowe usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="92fc8-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="92fc8-113">W poniższym przykładzie zdefiniowano dwa punkty końcowe, które będą używane do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="92fc8-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="92fc8-114">Definiuje również punkty końcowe klienta, które są używane do wysyłania komunikatów do wystąpień usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="92fc8-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="92fc8-115">Zdefiniuj filtry służące do kierowania komunikatów do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="92fc8-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="92fc8-116">W tym przykładzie filtr EndpointName służy do określenia, który punkt końcowy usługi odebrał komunikat.</span><span class="sxs-lookup"><span data-stu-id="92fc8-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="92fc8-117">W poniższym przykładzie zdefiniowano niezbędną sekcję routingu i filtry.</span><span class="sxs-lookup"><span data-stu-id="92fc8-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="92fc8-118">Zdefiniuj tabelę filtrów, która kojarzy każdy filtr z punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="92fc8-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="92fc8-119">W tym przykładzie komunikat zostanie rozesłany na podstawie określonego punktu końcowego, który został odebrany.</span><span class="sxs-lookup"><span data-stu-id="92fc8-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="92fc8-120">Ponieważ komunikat może pasować tylko do jednego z dwóch możliwych filtrów, nie ma potrzeby używania priorytetu filtru do kontrolowania kolejności, w której są oceniane filtry.</span><span class="sxs-lookup"><span data-stu-id="92fc8-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="92fc8-121">Poniższy schemat definiuje tabelę filtrów i dodaje filtry zdefiniowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="92fc8-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="92fc8-122">Aby oszacować komunikaty przychodzące względem filtrów zawartych w tabeli, należy skojarzyć tabelę filtru z punktami końcowymi usługi przy użyciu zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="92fc8-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="92fc8-123">Poniższy przykład demonstruje kojarzenie "filterTable1" z punktami końcowymi usługi:</span><span class="sxs-lookup"><span data-stu-id="92fc8-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="92fc8-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="92fc8-124">Example</span></span>  
 <span data-ttu-id="92fc8-125">Poniżej znajduje się kompletna lista plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="92fc8-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92fc8-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92fc8-126">See also</span></span>

- [<span data-ttu-id="92fc8-127">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="92fc8-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
