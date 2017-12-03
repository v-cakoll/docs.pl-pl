---
title: '&lt;synchronousReceive&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 79d78517b62e4476106ff1ed7978c770a17caf2a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="d036b-102">&lt;synchronousReceive&gt;, element</span><span class="sxs-lookup"><span data-stu-id="d036b-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="d036b-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="d036b-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="d036b-104">Nie ma żadnych atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d036b-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="d036b-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d036b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d036b-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d036b-106">\<behaviors></span></span>  
<span data-ttu-id="d036b-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d036b-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="d036b-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d036b-108">\<behavior></span></span>  
<span data-ttu-id="d036b-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="d036b-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d036b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d036b-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d036b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d036b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d036b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d036b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d036b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d036b-113">Attributes</span></span>  
 <span data-ttu-id="d036b-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d036b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d036b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d036b-115">Child Elements</span></span>  
 <span data-ttu-id="d036b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="d036b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d036b-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d036b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d036b-118">Element</span><span class="sxs-lookup"><span data-stu-id="d036b-118">Element</span></span>|<span data-ttu-id="d036b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d036b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d036b-120">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d036b-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d036b-121">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d036b-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d036b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d036b-122">Remarks</span></span>  
 <span data-ttu-id="d036b-123">Umożliwia to zachowanie poinstruować odbiornik kanału do użycia synchronicznego odbierania zamiast domyślnego, asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="d036b-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="d036b-124">wystawia nowego wątku pompa dla poszczególnych zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="d036b-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="d036b-125">Jeśli istnieje wiele kanałów, istnieje możliwość wyczerpaniu wątków.</span><span class="sxs-lookup"><span data-stu-id="d036b-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d036b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d036b-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
