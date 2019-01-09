---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: ba02977a7df44931ae195040949e9a8eb0c141b5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152024"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="7c3fe-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="7c3fe-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="7c3fe-103">Określa typ implementacji dostawcy stanów stałych do użycia, jak również limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="7c3fe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7c3fe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7c3fe-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7c3fe-105">\<behaviors></span></span>  
<span data-ttu-id="7c3fe-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7c3fe-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7c3fe-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7c3fe-107">\<behavior></span></span>  
<span data-ttu-id="7c3fe-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="7c3fe-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c3fe-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c3fe-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c3fe-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c3fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c3fe-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c3fe-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c3fe-112">Attributes</span></span>  
  
|<span data-ttu-id="7c3fe-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7c3fe-113">Attribute</span></span>|<span data-ttu-id="7c3fe-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7c3fe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c3fe-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="7c3fe-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="7c3fe-116">A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="7c3fe-117">Wartość domyślna to "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="7c3fe-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="7c3fe-118">— typ</span><span class="sxs-lookup"><span data-stu-id="7c3fe-118">type</span></span>|<span data-ttu-id="7c3fe-119">Ciąg, który określa typ fabryki dostawcy trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c3fe-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c3fe-120">Child Elements</span></span>  
 <span data-ttu-id="7c3fe-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c3fe-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c3fe-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7c3fe-123">Element</span><span class="sxs-lookup"><span data-stu-id="7c3fe-123">Element</span></span>|<span data-ttu-id="7c3fe-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7c3fe-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c3fe-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7c3fe-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7c3fe-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c3fe-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c3fe-127">Remarks</span></span>  
 <span data-ttu-id="7c3fe-128">Ten element określa dostawcy stanów trwałych, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="7c3fe-129">Należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="7c3fe-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c3fe-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c3fe-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
