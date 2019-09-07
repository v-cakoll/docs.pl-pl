---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399547"
---
# <a name="servicetimeouts"></a><span data-ttu-id="641ef-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="641ef-101">\<serviceTimeouts></span></span>
<span data-ttu-id="641ef-102">Określa limit czasu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="641ef-102">Specifies the timeout for a service.</span></span>  
  
<span data-ttu-id="641ef-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="641ef-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="641ef-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="641ef-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="641ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="641ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="641ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="641ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="641ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="641ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="641ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<przekroczenie limitu czasu >**</span><span class="sxs-lookup"><span data-stu-id="641ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641ef-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="641ef-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="641ef-110">Typ</span><span class="sxs-lookup"><span data-stu-id="641ef-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641ef-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="641ef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="641ef-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="641ef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641ef-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="641ef-113">Attributes</span></span>  
  
|<span data-ttu-id="641ef-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="641ef-114">Attribute</span></span>|<span data-ttu-id="641ef-115">Opis</span><span class="sxs-lookup"><span data-stu-id="641ef-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="641ef-116"><xref:System.TimeSpan> Wartość, która określa przedział czasu, przez który transakcja musi przepływać z klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="641ef-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="641ef-117">Wartość domyślna to "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="641ef-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641ef-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="641ef-118">Child Elements</span></span>  
 <span data-ttu-id="641ef-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="641ef-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="641ef-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="641ef-120">Parent Elements</span></span>  
  
|<span data-ttu-id="641ef-121">Element</span><span class="sxs-lookup"><span data-stu-id="641ef-121">Element</span></span>|<span data-ttu-id="641ef-122">Opis</span><span class="sxs-lookup"><span data-stu-id="641ef-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="641ef-123">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="641ef-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="641ef-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="641ef-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="641ef-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="641ef-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
