---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918678"
---
# <a name="transactedbatching"></a><span data-ttu-id="f5bae-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="f5bae-101">\<transactedBatching></span></span>

<span data-ttu-id="f5bae-102">Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="f5bae-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="f5bae-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f5bae-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="f5bae-104">\<zachowania > </span><span class="sxs-lookup"><span data-stu-id="f5bae-104">\<behaviors></span></span>\
<span data-ttu-id="f5bae-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f5bae-105">\<endpointBehaviors></span></span>\
<span data-ttu-id="f5bae-106">\<zachowanie > </span><span class="sxs-lookup"><span data-stu-id="f5bae-106">\<behavior></span></span>\
<span data-ttu-id="f5bae-107">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="f5bae-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="f5bae-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5bae-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5bae-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f5bae-109">Attributes and Elements</span></span>

<span data-ttu-id="f5bae-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f5bae-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5bae-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f5bae-111">Attributes</span></span>

|<span data-ttu-id="f5bae-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f5bae-112">Attribute</span></span>|<span data-ttu-id="f5bae-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f5bae-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="f5bae-114">Liczba całkowita określająca maksymalną liczbę operacji odbioru, które mogą być przetwarzane wsadowo w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f5bae-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="f5bae-115">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="f5bae-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f5bae-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f5bae-116">Child Elements</span></span>

<span data-ttu-id="f5bae-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="f5bae-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5bae-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f5bae-118">Parent Elements</span></span>

|<span data-ttu-id="f5bae-119">Element</span><span class="sxs-lookup"><span data-stu-id="f5bae-119">Element</span></span>|<span data-ttu-id="f5bae-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f5bae-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5bae-121">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="f5bae-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f5bae-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f5bae-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5bae-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5bae-123">Remarks</span></span>

<span data-ttu-id="f5bae-124">Transport, który jest skonfigurowany z przetwarzaniem wsadowym transakcji, próbuje wsadowo wykonać kilka operacji odbioru w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f5bae-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="f5bae-125">Dzięki temu można uniknąć stosunkowo wysokiego kosztu tworzenia transakcji i zatwierdzania jej w każdej operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="f5bae-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="f5bae-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5bae-126">Example</span></span>

<span data-ttu-id="f5bae-127">Poniższy przykład pokazuje, jak dodać działanie transakcyjnego przetwarzania wsadowego do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5bae-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a><span data-ttu-id="f5bae-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5bae-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
