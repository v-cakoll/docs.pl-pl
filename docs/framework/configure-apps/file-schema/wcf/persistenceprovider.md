---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dc8dea0ddd1ea074c08952e3e2ebfef2d12f7183
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099290"
---
# <a name="persistenceprovider"></a><span data-ttu-id="4b0a0-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="4b0a0-101">\<persistenceProvider></span></span>
<span data-ttu-id="4b0a0-102">Określa typ implementacji dostawcy stanów stałych do użycia, jak również limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="4b0a0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b0a0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b0a0-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="4b0a0-104">\<behaviors></span></span>  
<span data-ttu-id="4b0a0-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4b0a0-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="4b0a0-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4b0a0-106">\<behavior></span></span>  
<span data-ttu-id="4b0a0-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="4b0a0-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0a0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b0a0-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b0a0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b0a0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4b0a0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b0a0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b0a0-111">Attributes</span></span>  
  
|<span data-ttu-id="4b0a0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4b0a0-112">Attribute</span></span>|<span data-ttu-id="4b0a0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4b0a0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b0a0-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="4b0a0-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="4b0a0-115">A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="4b0a0-116">Wartość domyślna to "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="4b0a0-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="4b0a0-117">— typ</span><span class="sxs-lookup"><span data-stu-id="4b0a0-117">type</span></span>|<span data-ttu-id="4b0a0-118">Ciąg, który określa typ fabryki dostawcy trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b0a0-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b0a0-119">Child Elements</span></span>  
 <span data-ttu-id="4b0a0-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b0a0-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b0a0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4b0a0-122">Element</span><span class="sxs-lookup"><span data-stu-id="4b0a0-122">Element</span></span>|<span data-ttu-id="4b0a0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4b0a0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b0a0-124">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4b0a0-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4b0a0-125">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b0a0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b0a0-126">Remarks</span></span>  
 <span data-ttu-id="4b0a0-127">Ten element określa dostawcy stanów trwałych, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="4b0a0-128">Należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b0a0-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0a0-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b0a0-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
