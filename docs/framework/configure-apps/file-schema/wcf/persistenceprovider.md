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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b506b8ef14246ee954adb0a16102f4bb208106b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="83607-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="83607-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="83607-103">Określa typ do użycia implementacja dostawcy trwałości, jak również limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="83607-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="83607-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="83607-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="83607-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="83607-105">\<behaviors></span></span>  
<span data-ttu-id="83607-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="83607-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="83607-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="83607-107">\<behavior></span></span>  
<span data-ttu-id="83607-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="83607-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83607-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="83607-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83607-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83607-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83607-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83607-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83607-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83607-112">Attributes</span></span>  
  
|<span data-ttu-id="83607-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="83607-113">Attribute</span></span>|<span data-ttu-id="83607-114">Opis</span><span class="sxs-lookup"><span data-stu-id="83607-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83607-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="83607-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="83607-116">A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania.</span><span class="sxs-lookup"><span data-stu-id="83607-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="83607-117">Wartość domyślna to "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="83607-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="83607-118">— typ</span><span class="sxs-lookup"><span data-stu-id="83607-118">type</span></span>|<span data-ttu-id="83607-119">Ciąg określający typ fabryki dostawców trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="83607-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83607-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83607-120">Child Elements</span></span>  
 <span data-ttu-id="83607-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="83607-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83607-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83607-122">Parent Elements</span></span>  
  
|<span data-ttu-id="83607-123">Element</span><span class="sxs-lookup"><span data-stu-id="83607-123">Element</span></span>|<span data-ttu-id="83607-124">Opis</span><span class="sxs-lookup"><span data-stu-id="83607-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83607-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="83607-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="83607-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="83607-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83607-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83607-127">Remarks</span></span>  
 <span data-ttu-id="83607-128">Ten element określa dostawcy trwałości, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="83607-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="83607-129">Tej opcji należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="83607-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83607-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83607-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
