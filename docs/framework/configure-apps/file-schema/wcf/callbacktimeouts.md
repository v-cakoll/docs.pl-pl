---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e666bac0be772e417f140e1482649f82ea70e2f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173644"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="3a8fa-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="3a8fa-101">\<callbackTimeouts></span></span>
<span data-ttu-id="3a8fa-102">Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3a8fa-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="3a8fa-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3a8fa-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a8fa-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3a8fa-104">\<behaviors></span></span>  
<span data-ttu-id="3a8fa-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3a8fa-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="3a8fa-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3a8fa-106">\<behavior></span></span>  
<span data-ttu-id="3a8fa-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="3a8fa-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a8fa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a8fa-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="3a8fa-109">Typ</span><span class="sxs-lookup"><span data-stu-id="3a8fa-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a8fa-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a8fa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a8fa-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a8fa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a8fa-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a8fa-112">Attributes</span></span>  
  
|<span data-ttu-id="3a8fa-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a8fa-113">Attribute</span></span>|<span data-ttu-id="3a8fa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3a8fa-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="3a8fa-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="3a8fa-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="3a8fa-116">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="3a8fa-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a8fa-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a8fa-117">Child Elements</span></span>  
 <span data-ttu-id="3a8fa-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3a8fa-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a8fa-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a8fa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3a8fa-120">Element</span><span class="sxs-lookup"><span data-stu-id="3a8fa-120">Element</span></span>|<span data-ttu-id="3a8fa-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3a8fa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a8fa-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3a8fa-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3a8fa-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3a8fa-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a8fa-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a8fa-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
