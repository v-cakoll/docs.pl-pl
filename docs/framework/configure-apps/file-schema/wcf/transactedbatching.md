---
title: '&lt;transactedBatching&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fc5d5cc77fcb227efd36106f1f8cb31efad24cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="7ae03-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="7ae03-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="7ae03-103">Określa, czy transakcja tworzenia plików wsadowych jest obsługiwane dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="7ae03-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="7ae03-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7ae03-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ae03-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7ae03-105">\<behaviors></span></span>  
<span data-ttu-id="7ae03-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7ae03-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7ae03-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7ae03-107">\<behavior></span></span>  
<span data-ttu-id="7ae03-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="7ae03-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ae03-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ae03-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ae03-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ae03-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7ae03-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7ae03-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ae03-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ae03-112">Attributes</span></span>  
  
|<span data-ttu-id="7ae03-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7ae03-113">Attribute</span></span>|<span data-ttu-id="7ae03-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7ae03-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="7ae03-115">Liczba całkowita określająca maksymalną liczbę operacji pobrania, które można zebrać razem w jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="7ae03-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="7ae03-116">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="7ae03-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ae03-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ae03-117">Child Elements</span></span>  
 <span data-ttu-id="7ae03-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ae03-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ae03-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ae03-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7ae03-120">Element</span><span class="sxs-lookup"><span data-stu-id="7ae03-120">Element</span></span>|<span data-ttu-id="7ae03-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7ae03-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ae03-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7ae03-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7ae03-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7ae03-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ae03-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ae03-124">Remarks</span></span>  
 <span data-ttu-id="7ae03-125">Transport, który jest skonfigurowany przy użyciu transakcji przetwarzanie wsadowe próby partii kilka odbierać operacje jako jedna transakcja.</span><span class="sxs-lookup"><span data-stu-id="7ae03-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="7ae03-126">W ten sposób stosunkowo wysokich kosztów transakcji tworzenia i zatwierdzania w każdym odbierania uniknąć operacji.</span><span class="sxs-lookup"><span data-stu-id="7ae03-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ae03-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ae03-127">Example</span></span>  
 <span data-ttu-id="7ae03-128">Poniższy przykład przedstawia sposób dodawania zachowanie transakcyjnego łączenia we wsady do usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7ae03-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="7ae03-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ae03-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
