---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399413"
---
# \<transactedBatching>

<span data-ttu-id="a5dd2-101">Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="a5dd2-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5dd2-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5dd2-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5dd2-103">Attributes and Elements</span></span>

<span data-ttu-id="a5dd2-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5dd2-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5dd2-105">Attributes</span></span>

|<span data-ttu-id="a5dd2-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a5dd2-106">Attribute</span></span>|<span data-ttu-id="a5dd2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a5dd2-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="a5dd2-108">Liczba całkowita określająca maksymalną liczbę operacji odbioru, które mogą być przetwarzane wsadowo w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="a5dd2-109">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a5dd2-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5dd2-110">Child Elements</span></span>

<span data-ttu-id="a5dd2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5dd2-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5dd2-112">Parent Elements</span></span>

|<span data-ttu-id="a5dd2-113">Element</span><span class="sxs-lookup"><span data-stu-id="a5dd2-113">Element</span></span>|<span data-ttu-id="a5dd2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a5dd2-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a5dd2-115">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5dd2-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5dd2-116">Remarks</span></span>

<span data-ttu-id="a5dd2-117">Transport, który jest skonfigurowany z przetwarzaniem wsadowym transakcji, próbuje wsadowo wykonać kilka operacji odbioru w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="a5dd2-118">Dzięki temu można uniknąć stosunkowo wysokiego kosztu tworzenia transakcji i zatwierdzania jej w każdej operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="a5dd2-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5dd2-119">Example</span></span>

<span data-ttu-id="a5dd2-120">Poniższy przykład pokazuje, jak dodać działanie transakcyjnego przetwarzania wsadowego do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a5dd2-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a5dd2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5dd2-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
