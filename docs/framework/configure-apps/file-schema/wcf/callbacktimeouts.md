---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: d57a888a19e684ac13632c1ab2476e304667c3e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919664"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="390c9-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="390c9-101">\<callbackTimeouts></span></span>
<span data-ttu-id="390c9-102">Określa wartość limitu czasu podczas przepływu transakcji z serwera, aby client.in scenariusz dwustronnego kontraktu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="390c9-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="390c9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="390c9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="390c9-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="390c9-104">\<behaviors></span></span>  
<span data-ttu-id="390c9-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="390c9-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="390c9-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="390c9-106">\<behavior></span></span>  
<span data-ttu-id="390c9-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="390c9-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390c9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="390c9-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="390c9-109">Typ</span><span class="sxs-lookup"><span data-stu-id="390c9-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="390c9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="390c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="390c9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="390c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="390c9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="390c9-112">Attributes</span></span>  
  
|<span data-ttu-id="390c9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="390c9-113">Attribute</span></span>|<span data-ttu-id="390c9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="390c9-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="390c9-115"><xref:System.TimeSpan> Wartość, która określa przedział czasu, w którym transakcje muszą zostać ukończone lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="390c9-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="390c9-116">Wartość domyślna to "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="390c9-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="390c9-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="390c9-117">Child Elements</span></span>  
 <span data-ttu-id="390c9-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="390c9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="390c9-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="390c9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="390c9-120">Element</span><span class="sxs-lookup"><span data-stu-id="390c9-120">Element</span></span>|<span data-ttu-id="390c9-121">Opis</span><span class="sxs-lookup"><span data-stu-id="390c9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="390c9-122">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="390c9-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="390c9-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="390c9-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="390c9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="390c9-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
