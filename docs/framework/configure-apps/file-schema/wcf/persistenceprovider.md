---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 4fc9e1332effc51e183a84cf2d3653357277d2ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934139"
---
# <a name="persistenceprovider"></a><span data-ttu-id="1f1a8-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="1f1a8-101">\<persistenceProvider></span></span>
<span data-ttu-id="1f1a8-102">Określa typ implementacji dostawcy trwałości, a także limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="1f1a8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1f1a8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1f1a8-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="1f1a8-104">\<behaviors></span></span>  
<span data-ttu-id="1f1a8-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1f1a8-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1f1a8-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="1f1a8-106">\<behavior></span></span>  
<span data-ttu-id="1f1a8-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="1f1a8-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1a8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f1a8-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f1a8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f1a8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1f1a8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f1a8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f1a8-111">Attributes</span></span>  
  
|<span data-ttu-id="1f1a8-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1f1a8-112">Attribute</span></span>|<span data-ttu-id="1f1a8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1f1a8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f1a8-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="1f1a8-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="1f1a8-115"><xref:System.TimeSpan> Wartość określająca limit czasu używany na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="1f1a8-116">Wartość domyślna to "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="1f1a8-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="1f1a8-117">— typ</span><span class="sxs-lookup"><span data-stu-id="1f1a8-117">type</span></span>|<span data-ttu-id="1f1a8-118">Ciąg określający typ fabryki dostawcy trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f1a8-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f1a8-119">Child Elements</span></span>  
 <span data-ttu-id="1f1a8-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f1a8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f1a8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1f1a8-122">Element</span><span class="sxs-lookup"><span data-stu-id="1f1a8-122">Element</span></span>|<span data-ttu-id="1f1a8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="1f1a8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f1a8-124">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="1f1a8-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1f1a8-125">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f1a8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f1a8-126">Remarks</span></span>  
 <span data-ttu-id="1f1a8-127">Ten element określa dostawcę trwałości, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="1f1a8-128">Powinna być używana razem z `wsHttpContextBinding` informacjami o stanie, które przechodzą w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f1a8-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1a8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f1a8-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
