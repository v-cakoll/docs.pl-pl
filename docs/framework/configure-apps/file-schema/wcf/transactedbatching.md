---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 43415d9eac5e61f42006aecb3248dec9811eb3e6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366464"
---
# <a name="transactedbatching"></a><span data-ttu-id="4fe02-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="4fe02-101">\<transactedBatching></span></span>

<span data-ttu-id="4fe02-102">Określa, czy transakcja tworzenia plików wsadowych jest obsługiwana dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="4fe02-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="4fe02-103">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="4fe02-103">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="4fe02-104">\<zachowania > \\</span><span class="sxs-lookup"><span data-stu-id="4fe02-104">\<behaviors>\\</span></span>
<span data-ttu-id="4fe02-105">\<endpointBehaviors>\\</span><span class="sxs-lookup"><span data-stu-id="4fe02-105">\<endpointBehaviors>\\</span></span>
<span data-ttu-id="4fe02-106">\<zachowanie > \\</span><span class="sxs-lookup"><span data-stu-id="4fe02-106">\<behavior>\\</span></span>
<span data-ttu-id="4fe02-107">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="4fe02-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="4fe02-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fe02-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4fe02-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4fe02-109">Attributes and Elements</span></span>

<span data-ttu-id="4fe02-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4fe02-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4fe02-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4fe02-111">Attributes</span></span>

|<span data-ttu-id="4fe02-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4fe02-112">Attribute</span></span>|<span data-ttu-id="4fe02-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4fe02-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="4fe02-114">Liczba całkowita określająca maksymalną liczbę operacji pobrania, które można zebrać razem w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="4fe02-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="4fe02-115">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="4fe02-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4fe02-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4fe02-116">Child Elements</span></span>

<span data-ttu-id="4fe02-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="4fe02-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4fe02-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4fe02-118">Parent Elements</span></span>

|<span data-ttu-id="4fe02-119">Element</span><span class="sxs-lookup"><span data-stu-id="4fe02-119">Element</span></span>|<span data-ttu-id="4fe02-120">Opis</span><span class="sxs-lookup"><span data-stu-id="4fe02-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4fe02-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4fe02-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4fe02-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4fe02-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4fe02-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fe02-123">Remarks</span></span>

<span data-ttu-id="4fe02-124">Transportu, który jest skonfigurowany z transakcją dzielenia na partie prób partii kilka otrzymują operacji w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="4fe02-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="4fe02-125">W ten sposób stosunkowo wysokie koszty tworzenia transakcji i zatwierdzania w każdej odbierania jest unikać operacji.</span><span class="sxs-lookup"><span data-stu-id="4fe02-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="4fe02-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="4fe02-126">Example</span></span>

<span data-ttu-id="4fe02-127">Poniższy przykład pokazuje, jak dodanie transakcyjne zachowania łączenia we wsady do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4fe02-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4fe02-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fe02-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
