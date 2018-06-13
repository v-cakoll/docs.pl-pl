---
title: '&lt;synchronousReceive&gt;, element'
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753264"
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="fcc53-102">&lt;synchronousReceive&gt;, element</span><span class="sxs-lookup"><span data-stu-id="fcc53-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="fcc53-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="fcc53-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="fcc53-104">Nie ma żadnych atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fcc53-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="fcc53-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fcc53-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fcc53-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="fcc53-106">\<behaviors></span></span>  
<span data-ttu-id="fcc53-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="fcc53-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="fcc53-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="fcc53-108">\<behavior></span></span>  
<span data-ttu-id="fcc53-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="fcc53-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc53-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcc53-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcc53-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fcc53-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fcc53-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fcc53-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcc53-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fcc53-113">Attributes</span></span>  
 <span data-ttu-id="fcc53-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="fcc53-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fcc53-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fcc53-115">Child Elements</span></span>  
 <span data-ttu-id="fcc53-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="fcc53-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcc53-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fcc53-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fcc53-118">Element</span><span class="sxs-lookup"><span data-stu-id="fcc53-118">Element</span></span>|<span data-ttu-id="fcc53-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fcc53-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcc53-120">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="fcc53-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fcc53-121">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fcc53-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcc53-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fcc53-122">Remarks</span></span>  
 <span data-ttu-id="fcc53-123">Umożliwia to zachowanie poinstruować odbiornik kanału do użycia synchronicznego odbierania zamiast domyślnego, asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="fcc53-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="fcc53-124">Windows Communication Foundation (WCF) wystawia nowego wątku pompa dla poszczególnych zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="fcc53-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="fcc53-125">Jeśli istnieje wiele kanałów, istnieje możliwość wyczerpaniu wątków.</span><span class="sxs-lookup"><span data-stu-id="fcc53-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc53-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcc53-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
