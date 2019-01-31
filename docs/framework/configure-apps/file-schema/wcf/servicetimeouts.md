---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: b67ea137e6c116d00a8a098b9c0df99430114dc5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267290"
---
# <a name="servicetimeouts"></a><span data-ttu-id="eee4c-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="eee4c-101">\<serviceTimeouts></span></span>
<span data-ttu-id="eee4c-102">Określa limit czasu usługi.</span><span class="sxs-lookup"><span data-stu-id="eee4c-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="eee4c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eee4c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eee4c-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="eee4c-104">\<behaviors></span></span>  
<span data-ttu-id="eee4c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="eee4c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="eee4c-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="eee4c-106">\<behavior></span></span>  
<span data-ttu-id="eee4c-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="eee4c-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee4c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="eee4c-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="eee4c-109">Typ</span><span class="sxs-lookup"><span data-stu-id="eee4c-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eee4c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eee4c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eee4c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eee4c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eee4c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eee4c-112">Attributes</span></span>  
  
|<span data-ttu-id="eee4c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eee4c-113">Attribute</span></span>|<span data-ttu-id="eee4c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="eee4c-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="eee4c-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu transakcji musi przepływać od klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="eee4c-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="eee4c-116">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="eee4c-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eee4c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eee4c-117">Child Elements</span></span>  
 <span data-ttu-id="eee4c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="eee4c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eee4c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eee4c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eee4c-120">Element</span><span class="sxs-lookup"><span data-stu-id="eee4c-120">Element</span></span>|<span data-ttu-id="eee4c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="eee4c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee4c-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="eee4c-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="eee4c-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="eee4c-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eee4c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eee4c-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
