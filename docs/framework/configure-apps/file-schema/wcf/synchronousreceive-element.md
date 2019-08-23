---
title: <synchronousReceive>, element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938964"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="efd3b-102">\<synchronousReceive, element ></span><span class="sxs-lookup"><span data-stu-id="efd3b-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="efd3b-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania w przypadku otrzymywania wiadomości w usłudze lub aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="efd3b-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="efd3b-104">Nie ma żadnych atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="efd3b-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="efd3b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="efd3b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="efd3b-106">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="efd3b-106">\<behaviors></span></span>  
<span data-ttu-id="efd3b-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="efd3b-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="efd3b-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="efd3b-108">\<behavior></span></span>  
<span data-ttu-id="efd3b-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="efd3b-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd3b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="efd3b-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efd3b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="efd3b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="efd3b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="efd3b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efd3b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="efd3b-113">Attributes</span></span>  
 <span data-ttu-id="efd3b-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="efd3b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="efd3b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="efd3b-115">Child Elements</span></span>  
 <span data-ttu-id="efd3b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="efd3b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efd3b-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="efd3b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="efd3b-118">Element</span><span class="sxs-lookup"><span data-stu-id="efd3b-118">Element</span></span>|<span data-ttu-id="efd3b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="efd3b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efd3b-120">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="efd3b-120">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="efd3b-121">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="efd3b-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efd3b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efd3b-122">Remarks</span></span>  
 <span data-ttu-id="efd3b-123">Użyj tego zachowania, aby nakazać odbiornikowi kanału użycie synchronicznego odbioru zamiast domyślnego, asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="efd3b-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="efd3b-124">Windows Communication Foundation (WCF) wystawia nowy wątek do pompy dla każdego zaakceptowanego kanału.</span><span class="sxs-lookup"><span data-stu-id="efd3b-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="efd3b-125">Jeśli istnieje wiele kanałów, istnieje możliwość uruchomienia poza wątkiem.</span><span class="sxs-lookup"><span data-stu-id="efd3b-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd3b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efd3b-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
