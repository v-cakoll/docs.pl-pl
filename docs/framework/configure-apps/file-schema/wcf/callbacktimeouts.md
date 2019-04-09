---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e666bac0be772e417f140e1482649f82ea70e2f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173644"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="ad1bb-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="ad1bb-101">\<callbackTimeouts></span></span>
<span data-ttu-id="ad1bb-102">Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="ad1bb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad1bb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad1bb-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ad1bb-104">\<behaviors></span></span>  
<span data-ttu-id="ad1bb-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ad1bb-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="ad1bb-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ad1bb-106">\<behavior></span></span>  
<span data-ttu-id="ad1bb-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="ad1bb-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1bb-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad1bb-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="ad1bb-109">Typ</span><span class="sxs-lookup"><span data-stu-id="ad1bb-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad1bb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ad1bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ad1bb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad1bb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ad1bb-112">Attributes</span></span>  
  
|<span data-ttu-id="ad1bb-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ad1bb-113">Attribute</span></span>|<span data-ttu-id="ad1bb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ad1bb-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="ad1bb-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="ad1bb-116">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="ad1bb-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad1bb-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ad1bb-117">Child Elements</span></span>  
 <span data-ttu-id="ad1bb-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad1bb-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ad1bb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ad1bb-120">Element</span><span class="sxs-lookup"><span data-stu-id="ad1bb-120">Element</span></span>|<span data-ttu-id="ad1bb-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ad1bb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad1bb-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ad1bb-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ad1bb-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad1bb-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad1bb-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
