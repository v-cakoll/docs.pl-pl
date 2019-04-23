---
title: <synchronousReceive>, element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166546"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="f48e7-102">\<synchronousReceive > element</span><span class="sxs-lookup"><span data-stu-id="f48e7-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="f48e7-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="f48e7-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="f48e7-104">Nie ma żadnych atrybutów lub elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f48e7-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="f48e7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f48e7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f48e7-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="f48e7-106">\<behaviors></span></span>  
<span data-ttu-id="f48e7-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f48e7-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="f48e7-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="f48e7-108">\<behavior></span></span>  
<span data-ttu-id="f48e7-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="f48e7-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f48e7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f48e7-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f48e7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f48e7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f48e7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f48e7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f48e7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f48e7-113">Attributes</span></span>  
 <span data-ttu-id="f48e7-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="f48e7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f48e7-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f48e7-115">Child Elements</span></span>  
 <span data-ttu-id="f48e7-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f48e7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f48e7-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f48e7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f48e7-118">Element</span><span class="sxs-lookup"><span data-stu-id="f48e7-118">Element</span></span>|<span data-ttu-id="f48e7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f48e7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f48e7-120">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="f48e7-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f48e7-121">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f48e7-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f48e7-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f48e7-122">Remarks</span></span>  
 <span data-ttu-id="f48e7-123">Użyj tego zachowania, aby nakazać odbiornik kanału do użycia przez synchroniczny otrzymywać zamiast domyślnej, asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="f48e7-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="f48e7-124">Windows Communication Foundation (WCF) wystawia nowy wątek pompy dla każdego kanału akceptowane.</span><span class="sxs-lookup"><span data-stu-id="f48e7-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="f48e7-125">W przypadku wielu kanałów, istnieje możliwość korzystającym z wątków.</span><span class="sxs-lookup"><span data-stu-id="f48e7-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48e7-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f48e7-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
