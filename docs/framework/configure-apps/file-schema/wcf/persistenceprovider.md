---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400074"
---
# <a name="persistenceprovider"></a><span data-ttu-id="ef073-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="ef073-101">\<persistenceProvider></span></span>
<span data-ttu-id="ef073-102">Określa typ implementacji dostawcy trwałości, a także limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="ef073-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
<span data-ttu-id="ef073-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ef073-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ef073-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ef073-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ef073-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ef073-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ef073-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ef073-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ef073-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ef073-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ef073-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistenceProvider >**</span><span class="sxs-lookup"><span data-stu-id="ef073-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef073-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef073-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef073-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ef073-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ef073-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ef073-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef073-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ef073-112">Attributes</span></span>  
  
|<span data-ttu-id="ef073-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ef073-113">Attribute</span></span>|<span data-ttu-id="ef073-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ef073-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef073-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="ef073-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="ef073-116"><xref:System.TimeSpan> Wartość określająca limit czasu używany na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="ef073-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="ef073-117">Wartość domyślna to "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="ef073-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="ef073-118">— typ</span><span class="sxs-lookup"><span data-stu-id="ef073-118">type</span></span>|<span data-ttu-id="ef073-119">Ciąg określający typ fabryki dostawcy trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="ef073-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef073-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ef073-120">Child Elements</span></span>  
 <span data-ttu-id="ef073-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="ef073-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef073-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ef073-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ef073-123">Element</span><span class="sxs-lookup"><span data-stu-id="ef073-123">Element</span></span>|<span data-ttu-id="ef073-124">Opis</span><span class="sxs-lookup"><span data-stu-id="ef073-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef073-125">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="ef073-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ef073-126">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="ef073-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef073-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef073-127">Remarks</span></span>  
 <span data-ttu-id="ef073-128">Ten element określa dostawcę trwałości, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="ef073-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="ef073-129">Powinna być używana razem z `wsHttpContextBinding` informacjami o stanie, które przechodzą w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="ef073-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef073-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef073-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
