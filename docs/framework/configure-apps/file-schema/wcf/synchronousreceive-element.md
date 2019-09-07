---
title: <synchronousReceive>, element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399494"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="bc635-102">\<synchronousReceive, element ></span><span class="sxs-lookup"><span data-stu-id="bc635-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="bc635-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania w przypadku otrzymywania wiadomości w usłudze lub aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="bc635-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="bc635-104">Nie ma żadnych atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="bc635-104">It does not have any attributes or child elements.</span></span>  
  
<span data-ttu-id="bc635-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc635-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc635-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc635-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc635-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc635-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bc635-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc635-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bc635-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bc635-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bc635-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<synchronousReceive >**</span><span class="sxs-lookup"><span data-stu-id="bc635-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc635-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc635-111">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc635-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bc635-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bc635-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bc635-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc635-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc635-114">Attributes</span></span>  
 <span data-ttu-id="bc635-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="bc635-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc635-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc635-116">Child Elements</span></span>  
 <span data-ttu-id="bc635-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="bc635-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc635-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc635-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bc635-119">Element</span><span class="sxs-lookup"><span data-stu-id="bc635-119">Element</span></span>|<span data-ttu-id="bc635-120">Opis</span><span class="sxs-lookup"><span data-stu-id="bc635-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc635-121">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="bc635-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bc635-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="bc635-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc635-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc635-123">Remarks</span></span>  
 <span data-ttu-id="bc635-124">Użyj tego zachowania, aby nakazać odbiornikowi kanału użycie synchronicznego odbioru zamiast domyślnego, asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="bc635-124">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="bc635-125">Windows Communication Foundation (WCF) wystawia nowy wątek do pompy dla każdego zaakceptowanego kanału.</span><span class="sxs-lookup"><span data-stu-id="bc635-125">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="bc635-126">Jeśli istnieje wiele kanałów, istnieje możliwość uruchomienia poza wątkiem.</span><span class="sxs-lookup"><span data-stu-id="bc635-126">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc635-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc635-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
