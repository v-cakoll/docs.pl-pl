---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399413"
---
# <a name="transactedbatching"></a><span data-ttu-id="8ea5a-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="8ea5a-101">\<transactedBatching></span></span>

<span data-ttu-id="8ea5a-102">Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="8ea5a-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ea5a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ea5a-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8ea5a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8ea5a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8ea5a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8ea5a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8ea5a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="8ea5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8ea5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="8ea5a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactedBatching >**</span><span class="sxs-lookup"><span data-stu-id="8ea5a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="8ea5a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ea5a-109">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ea5a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ea5a-110">Attributes and Elements</span></span>

<span data-ttu-id="8ea5a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ea5a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ea5a-112">Attributes</span></span>

|<span data-ttu-id="8ea5a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8ea5a-113">Attribute</span></span>|<span data-ttu-id="8ea5a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8ea5a-114">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="8ea5a-115">Liczba całkowita określająca maksymalną liczbę operacji odbioru, które mogą być przetwarzane wsadowo w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="8ea5a-116">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-116">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8ea5a-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ea5a-117">Child Elements</span></span>

<span data-ttu-id="8ea5a-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ea5a-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ea5a-119">Parent Elements</span></span>

|<span data-ttu-id="8ea5a-120">Element</span><span class="sxs-lookup"><span data-stu-id="8ea5a-120">Element</span></span>|<span data-ttu-id="8ea5a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8ea5a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ea5a-122">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="8ea5a-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8ea5a-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-123">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ea5a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ea5a-124">Remarks</span></span>

<span data-ttu-id="8ea5a-125">Transport, który jest skonfigurowany z przetwarzaniem wsadowym transakcji, próbuje wsadowo wykonać kilka operacji odbioru w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="8ea5a-126">Dzięki temu można uniknąć stosunkowo wysokiego kosztu tworzenia transakcji i zatwierdzania jej w każdej operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="8ea5a-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ea5a-127">Example</span></span>

<span data-ttu-id="8ea5a-128">Poniższy przykład pokazuje, jak dodać działanie transakcyjnego przetwarzania wsadowego do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ea5a-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ea5a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ea5a-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
