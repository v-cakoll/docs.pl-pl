---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 269500324ad1beaa0b519fa17d251ee942276faa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269071"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="47893-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="47893-101">\<callbackTimeouts></span></span>
<span data-ttu-id="47893-102">Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="47893-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="47893-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="47893-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="47893-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="47893-104">\<behaviors></span></span>  
<span data-ttu-id="47893-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="47893-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="47893-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="47893-106">\<behavior></span></span>  
<span data-ttu-id="47893-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="47893-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47893-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="47893-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="47893-109">Typ</span><span class="sxs-lookup"><span data-stu-id="47893-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47893-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47893-110">Attributes and Elements</span></span>  
 <span data-ttu-id="47893-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47893-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47893-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47893-112">Attributes</span></span>  
  
|<span data-ttu-id="47893-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47893-113">Attribute</span></span>|<span data-ttu-id="47893-114">Opis</span><span class="sxs-lookup"><span data-stu-id="47893-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="47893-115">A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="47893-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="47893-116">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="47893-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47893-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47893-117">Child Elements</span></span>  
 <span data-ttu-id="47893-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="47893-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47893-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47893-119">Parent Elements</span></span>  
  
|<span data-ttu-id="47893-120">Element</span><span class="sxs-lookup"><span data-stu-id="47893-120">Element</span></span>|<span data-ttu-id="47893-121">Opis</span><span class="sxs-lookup"><span data-stu-id="47893-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47893-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="47893-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="47893-123">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="47893-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47893-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47893-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
