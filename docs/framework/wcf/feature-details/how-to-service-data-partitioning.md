---
title: 'Instrukcje: Partycjonowanie danych usługi'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300388"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="f9bf4-102">Instrukcje: Partycjonowanie danych usługi</span><span class="sxs-lookup"><span data-stu-id="f9bf4-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="f9bf4-103">W tym temacie przedstawiono podstawowe kroki wymagane do partycji wiadomości na wiele wystąpień tej samej usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="f9bf4-104">Partycjonowanie danych usługi jest zazwyczaj używany w przypadku konieczności skalowania usługi w celu zapewnienia lepszej jakości usługi, lub gdy potrzebujesz do obsługi żądań od innych klientów w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="f9bf4-105">Na przykład wiadomości od wysokiej wartości lub klientów "Złota" może być konieczne do przetworzenia na wyższy priorytet niż wiadomości od standardowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="f9bf4-106">W tym przykładzie komunikaty są kierowane do jednej z dwóch wystąpień usługi regularCalc.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="f9bf4-107">Oba wystąpienia usługi są identyczne; Jednak usługa reprezentowane przez wiadomości procesy punktu końcowego calculator1 odebrała od klientów o wysokiej wartości, punkt końcowy Kalkulator 2 przetwarzania wiadomości od innych klientów</span><span class="sxs-lookup"><span data-stu-id="f9bf4-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="f9bf4-108">Wiadomości wysłanych z klienta nie ma unikatowe dane, który może służyć do identyfikowania wystąpienia usługi, które komunikat powinien być kierowane do.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="f9bf4-109">Aby zezwolić na każdym kliencie do kierowania danych do określonego miejsca docelowego usługi wdrażamy dwa punkty końcowe usługi, które będą używane do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9bf4-110">Chociaż w tym przykładzie użyto określonych punktów końcowych do partycjonowania danych, to może być również wykonywane przy użyciu informacji zawartych w wiadomości takich jak dane w nagłówku lub w treści.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="f9bf4-111">Partycjonowanie danych usługi implementacji</span><span class="sxs-lookup"><span data-stu-id="f9bf4-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="f9bf4-112">Tworzenie podstawowej konfiguracji usługa routingu przez określenie punktów końcowych usługi udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="f9bf4-113">W poniższym przykładzie zdefiniowano dwa punkty końcowe, które będą używane w celu odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="f9bf4-114">Definiuje również punkty końcowe klienta, które są używane do wysyłania komunikatów do regularCalc wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="f9bf4-115">Zdefiniuj filtry używane do przesyłania wiadomości do docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="f9bf4-116">Na przykład filtr Nazwapunktukoncowego jest używany do określenia, które punkt końcowy usługi komunikat.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="f9bf4-117">W poniższym przykładzie zdefiniowano niezbędne sekcji routingu i filtry.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="f9bf4-118">Definiowanie tabeli filtru każdy filtr zostanie skojarzony z punktem końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="f9bf4-119">W tym przykładzie będą kierowane komunikat zgodnie z określonego punktu końcowego, który został odebrany przez.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="f9bf4-120">Ponieważ komunikat może wyłącznie odpowiadać jednej z dwóch możliwych filtrów, nie ma potrzeby używania priorytet filtru do kontrolowania kolejności, w które filtry są oceniane.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="f9bf4-121">Poniżej definiuje tabelę filtru i dodaje zdefiniowane wcześniej filtry.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="f9bf4-122">Aby ocenić komunikaty przychodzące filtry zawarte w tabeli, należy skojarzyć tabelę filtru z punktami końcowymi usługi za pomocą zachowania routingu.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="f9bf4-123">W poniższym przykładzie pokazano kojarzenie "filterTable1" z punktami końcowymi usługi:</span><span class="sxs-lookup"><span data-stu-id="f9bf4-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f9bf4-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9bf4-124">Example</span></span>  
 <span data-ttu-id="f9bf4-125">Poniżej znajduje się pełna lista pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f9bf4-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9bf4-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9bf4-126">See also</span></span>

- [<span data-ttu-id="f9bf4-127">Usługi routingu</span><span class="sxs-lookup"><span data-stu-id="f9bf4-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
