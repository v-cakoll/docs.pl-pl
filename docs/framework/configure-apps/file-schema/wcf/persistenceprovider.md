---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 8deca5b4bec4808ac9add201db0c936764fddcb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602224"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="d2838-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="d2838-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="d2838-103">Określa typ implementacji dostawcy stanów stałych do użycia, jak również limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="d2838-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="d2838-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2838-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2838-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d2838-105">\<behaviors></span></span>  
<span data-ttu-id="d2838-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d2838-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d2838-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d2838-107">\<behavior></span></span>  
<span data-ttu-id="d2838-108">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="d2838-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2838-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2838-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2838-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2838-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2838-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2838-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2838-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2838-112">Attributes</span></span>  
  
|<span data-ttu-id="d2838-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2838-113">Attribute</span></span>|<span data-ttu-id="d2838-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d2838-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2838-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="d2838-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="d2838-116">A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania.</span><span class="sxs-lookup"><span data-stu-id="d2838-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="d2838-117">Wartość domyślna to "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="d2838-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="d2838-118">— typ</span><span class="sxs-lookup"><span data-stu-id="d2838-118">type</span></span>|<span data-ttu-id="d2838-119">Ciąg, który określa typ fabryki dostawcy trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="d2838-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2838-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2838-120">Child Elements</span></span>  
 <span data-ttu-id="d2838-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="d2838-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2838-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2838-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d2838-123">Element</span><span class="sxs-lookup"><span data-stu-id="d2838-123">Element</span></span>|<span data-ttu-id="d2838-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d2838-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2838-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d2838-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d2838-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="d2838-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2838-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2838-127">Remarks</span></span>  
 <span data-ttu-id="d2838-128">Ten element określa dostawcy stanów trwałych, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="d2838-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="d2838-129">Należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2838-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2838-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2838-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
