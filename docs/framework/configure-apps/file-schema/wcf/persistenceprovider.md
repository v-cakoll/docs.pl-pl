---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 447384ef34c1ca2c7e641f0ba0d3d3718139e579
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="bd117-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="bd117-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="bd117-103">Określa typ do użycia implementacja dostawcy trwałości, jak również limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="bd117-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="bd117-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bd117-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd117-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bd117-105">\<behaviors></span></span>  
<span data-ttu-id="bd117-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bd117-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bd117-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bd117-107">\<behavior></span></span>  
<span data-ttu-id="bd117-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="bd117-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd117-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd117-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd117-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bd117-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd117-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bd117-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd117-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd117-112">Attributes</span></span>  
  
|<span data-ttu-id="bd117-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bd117-113">Attribute</span></span>|<span data-ttu-id="bd117-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bd117-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd117-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="bd117-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="bd117-116">A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania.</span><span class="sxs-lookup"><span data-stu-id="bd117-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="bd117-117">Wartość domyślna to "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="bd117-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="bd117-118">— typ</span><span class="sxs-lookup"><span data-stu-id="bd117-118">type</span></span>|<span data-ttu-id="bd117-119">Ciąg określający typ fabryki dostawców trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="bd117-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd117-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bd117-120">Child Elements</span></span>  
 <span data-ttu-id="bd117-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="bd117-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd117-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bd117-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bd117-123">Element</span><span class="sxs-lookup"><span data-stu-id="bd117-123">Element</span></span>|<span data-ttu-id="bd117-124">Opis</span><span class="sxs-lookup"><span data-stu-id="bd117-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd117-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bd117-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bd117-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="bd117-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd117-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd117-127">Remarks</span></span>  
 <span data-ttu-id="bd117-128">Ten element określa dostawcy trwałości, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="bd117-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="bd117-129">Tej opcji należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="bd117-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd117-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd117-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
