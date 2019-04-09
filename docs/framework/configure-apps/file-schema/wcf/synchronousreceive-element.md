---
title: <synchronousReceive> — element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166546"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="69b53-102">\<synchronousReceive > element</span><span class="sxs-lookup"><span data-stu-id="69b53-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="69b53-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="69b53-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="69b53-104">Nie ma żadnych atrybutów lub elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="69b53-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="69b53-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69b53-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="69b53-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="69b53-106">\<behaviors></span></span>  
<span data-ttu-id="69b53-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="69b53-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="69b53-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="69b53-108">\<behavior></span></span>  
<span data-ttu-id="69b53-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="69b53-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b53-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="69b53-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69b53-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69b53-111">Attributes and Elements</span></span>  
 <span data-ttu-id="69b53-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69b53-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69b53-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69b53-113">Attributes</span></span>  
 <span data-ttu-id="69b53-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="69b53-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69b53-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69b53-115">Child Elements</span></span>  
 <span data-ttu-id="69b53-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="69b53-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69b53-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69b53-117">Parent Elements</span></span>  
  
|<span data-ttu-id="69b53-118">Element</span><span class="sxs-lookup"><span data-stu-id="69b53-118">Element</span></span>|<span data-ttu-id="69b53-119">Opis</span><span class="sxs-lookup"><span data-stu-id="69b53-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69b53-120">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="69b53-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="69b53-121">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="69b53-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69b53-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69b53-122">Remarks</span></span>  
 <span data-ttu-id="69b53-123">Użyj tego zachowania, aby nakazać odbiornik kanału do użycia przez synchroniczny otrzymywać zamiast domyślnej, asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="69b53-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="69b53-124">Windows Communication Foundation (WCF) wystawia nowy wątek pompy dla każdego kanału akceptowane.</span><span class="sxs-lookup"><span data-stu-id="69b53-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="69b53-125">W przypadku wielu kanałów, istnieje możliwość korzystającym z wątków.</span><span class="sxs-lookup"><span data-stu-id="69b53-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b53-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69b53-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
