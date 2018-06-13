---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 48da0351d162a2143a26cc5b9eaa05b731358639
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749569"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="61ed3-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="61ed3-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="61ed3-103">Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="61ed3-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="61ed3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="61ed3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="61ed3-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="61ed3-105">\<behaviors></span></span>  
<span data-ttu-id="61ed3-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="61ed3-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="61ed3-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="61ed3-107">\<behavior></span></span>  
<span data-ttu-id="61ed3-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="61ed3-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ed3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="61ed3-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="61ed3-110">Typ</span><span class="sxs-lookup"><span data-stu-id="61ed3-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61ed3-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61ed3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61ed3-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61ed3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61ed3-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61ed3-113">Attributes</span></span>  
  
|<span data-ttu-id="61ed3-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61ed3-114">Attribute</span></span>|<span data-ttu-id="61ed3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="61ed3-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="61ed3-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="61ed3-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="61ed3-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="61ed3-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61ed3-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61ed3-118">Child Elements</span></span>  
 <span data-ttu-id="61ed3-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="61ed3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61ed3-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61ed3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="61ed3-121">Element</span><span class="sxs-lookup"><span data-stu-id="61ed3-121">Element</span></span>|<span data-ttu-id="61ed3-122">Opis</span><span class="sxs-lookup"><span data-stu-id="61ed3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61ed3-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="61ed3-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="61ed3-124">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="61ed3-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61ed3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61ed3-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
