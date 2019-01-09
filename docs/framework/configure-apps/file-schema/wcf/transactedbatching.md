---
title: '&lt;transactedBatching&gt;'
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: f56751ea3f8bdc9ecbeff57db835e5fc2edbb73e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148451"
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="063c4-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="063c4-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="063c4-103">Określa, czy transakcja tworzenia plików wsadowych jest obsługiwana dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="063c4-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="063c4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="063c4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="063c4-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="063c4-105">\<behaviors></span></span>  
<span data-ttu-id="063c4-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="063c4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="063c4-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="063c4-107">\<behavior></span></span>  
<span data-ttu-id="063c4-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="063c4-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="063c4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="063c4-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="063c4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="063c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="063c4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="063c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="063c4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="063c4-112">Attributes</span></span>  
  
|<span data-ttu-id="063c4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="063c4-113">Attribute</span></span>|<span data-ttu-id="063c4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="063c4-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="063c4-115">Liczba całkowita określająca maksymalną liczbę operacji pobrania, które można zebrać razem w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="063c4-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="063c4-116">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="063c4-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="063c4-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="063c4-117">Child Elements</span></span>  
 <span data-ttu-id="063c4-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="063c4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="063c4-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="063c4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="063c4-120">Element</span><span class="sxs-lookup"><span data-stu-id="063c4-120">Element</span></span>|<span data-ttu-id="063c4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="063c4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="063c4-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="063c4-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="063c4-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="063c4-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="063c4-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="063c4-124">Remarks</span></span>  
 <span data-ttu-id="063c4-125">Transportu, który jest skonfigurowany z transakcją dzielenia na partie prób partii kilka otrzymują operacji w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="063c4-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="063c4-126">W ten sposób stosunkowo wysokie koszty tworzenia transakcji i zatwierdzania w każdej odbierania jest unikać operacji.</span><span class="sxs-lookup"><span data-stu-id="063c4-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="063c4-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="063c4-127">Example</span></span>  
 <span data-ttu-id="063c4-128">Poniższy przykład pokazuje, jak dodanie transakcyjne zachowania łączenia we wsady do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="063c4-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
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
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->
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
  
## <a name="see-also"></a><span data-ttu-id="063c4-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="063c4-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
