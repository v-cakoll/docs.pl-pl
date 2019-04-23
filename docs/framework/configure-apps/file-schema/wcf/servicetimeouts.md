---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075525"
---
# <a name="servicetimeouts"></a><span data-ttu-id="3f9aa-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="3f9aa-101">\<serviceTimeouts></span></span>
<span data-ttu-id="3f9aa-102">Określa limit czasu usługi.</span><span class="sxs-lookup"><span data-stu-id="3f9aa-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="3f9aa-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f9aa-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f9aa-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3f9aa-104">\<behaviors></span></span>  
<span data-ttu-id="3f9aa-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3f9aa-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3f9aa-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3f9aa-106">\<behavior></span></span>  
<span data-ttu-id="3f9aa-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="3f9aa-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9aa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f9aa-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="3f9aa-109">Typ</span><span class="sxs-lookup"><span data-stu-id="3f9aa-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f9aa-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f9aa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3f9aa-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f9aa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f9aa-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f9aa-112">Attributes</span></span>  
  
|<span data-ttu-id="3f9aa-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3f9aa-113">Attribute</span></span>|<span data-ttu-id="3f9aa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3f9aa-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="3f9aa-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu transakcji musi przepływać od klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="3f9aa-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="3f9aa-116">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="3f9aa-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f9aa-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f9aa-117">Child Elements</span></span>  
 <span data-ttu-id="3f9aa-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3f9aa-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f9aa-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f9aa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3f9aa-120">Element</span><span class="sxs-lookup"><span data-stu-id="3f9aa-120">Element</span></span>|<span data-ttu-id="3f9aa-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3f9aa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f9aa-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3f9aa-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3f9aa-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="3f9aa-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f9aa-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f9aa-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
