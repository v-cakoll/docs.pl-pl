---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 01932fe2b7b7e699311e2c65ec8adaf0aef82dc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557906"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="fb274-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="fb274-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="fb274-103">Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="fb274-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="fb274-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fb274-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb274-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="fb274-105">\<behaviors></span></span>  
<span data-ttu-id="fb274-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="fb274-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="fb274-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="fb274-107">\<behavior></span></span>  
<span data-ttu-id="fb274-108">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="fb274-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb274-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb274-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="fb274-110">Typ</span><span class="sxs-lookup"><span data-stu-id="fb274-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb274-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb274-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fb274-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb274-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb274-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb274-113">Attributes</span></span>  
  
|<span data-ttu-id="fb274-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb274-114">Attribute</span></span>|<span data-ttu-id="fb274-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fb274-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="fb274-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="fb274-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="fb274-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="fb274-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb274-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb274-118">Child Elements</span></span>  
 <span data-ttu-id="fb274-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb274-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb274-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb274-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fb274-121">Element</span><span class="sxs-lookup"><span data-stu-id="fb274-121">Element</span></span>|<span data-ttu-id="fb274-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fb274-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb274-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="fb274-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fb274-124">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fb274-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb274-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb274-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
