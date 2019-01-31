---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 1e8ce41a27bd328c861f2f376a89c57bcd035389
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281297"
---
# <a name="transactedbatching"></a><span data-ttu-id="7eab0-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="7eab0-101">\<transactedBatching></span></span>
<span data-ttu-id="7eab0-102">Określa, czy transakcja tworzenia plików wsadowych jest obsługiwana dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="7eab0-102">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="7eab0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7eab0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7eab0-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7eab0-104">\<behaviors></span></span>  
<span data-ttu-id="7eab0-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7eab0-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="7eab0-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7eab0-106">\<behavior></span></span>  
<span data-ttu-id="7eab0-107">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="7eab0-107">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eab0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7eab0-108">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eab0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7eab0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7eab0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7eab0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eab0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7eab0-111">Attributes</span></span>  
  
|<span data-ttu-id="7eab0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7eab0-112">Attribute</span></span>|<span data-ttu-id="7eab0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7eab0-113">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="7eab0-114">Liczba całkowita określająca maksymalną liczbę operacji pobrania, które można zebrać razem w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="7eab0-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="7eab0-115">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="7eab0-115">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eab0-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7eab0-116">Child Elements</span></span>  
 <span data-ttu-id="7eab0-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="7eab0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7eab0-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7eab0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7eab0-119">Element</span><span class="sxs-lookup"><span data-stu-id="7eab0-119">Element</span></span>|<span data-ttu-id="7eab0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7eab0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eab0-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7eab0-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7eab0-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7eab0-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eab0-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7eab0-123">Remarks</span></span>  
 <span data-ttu-id="7eab0-124">Transportu, który jest skonfigurowany z transakcją dzielenia na partie prób partii kilka otrzymują operacji w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="7eab0-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="7eab0-125">W ten sposób stosunkowo wysokie koszty tworzenia transakcji i zatwierdzania w każdej odbierania jest unikać operacji.</span><span class="sxs-lookup"><span data-stu-id="7eab0-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eab0-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="7eab0-126">Example</span></span>  
 <span data-ttu-id="7eab0-127">Poniższy przykład pokazuje, jak dodanie transakcyjne zachowania łączenia we wsady do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7eab0-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7eab0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7eab0-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
