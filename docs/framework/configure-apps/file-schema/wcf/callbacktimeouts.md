---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e86b69b7d633fd99728936070e94da964e16de58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="ce045-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="ce045-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="ce045-103">Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ce045-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="ce045-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ce045-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ce045-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ce045-105">\<behaviors></span></span>  
<span data-ttu-id="ce045-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ce045-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ce045-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ce045-107">\<behavior></span></span>  
<span data-ttu-id="ce045-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="ce045-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce045-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce045-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="ce045-110">Typ</span><span class="sxs-lookup"><span data-stu-id="ce045-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce045-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce045-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ce045-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce045-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce045-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce045-113">Attributes</span></span>  
  
|<span data-ttu-id="ce045-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ce045-114">Attribute</span></span>|<span data-ttu-id="ce045-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ce045-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="ce045-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="ce045-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="ce045-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="ce045-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce045-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce045-118">Child Elements</span></span>  
 <span data-ttu-id="ce045-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="ce045-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce045-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce045-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ce045-121">Element</span><span class="sxs-lookup"><span data-stu-id="ce045-121">Element</span></span>|<span data-ttu-id="ce045-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ce045-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce045-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ce045-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ce045-124">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ce045-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce045-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce045-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
