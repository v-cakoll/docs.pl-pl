---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 2103c32112b6c5554d7b510f486d4cbb1349f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747956"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="ccaa8-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="ccaa8-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="ccaa8-103">Określa usługę debugowania dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ccaa8-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="ccaa8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccaa8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccaa8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ccaa8-105">\<behaviors></span></span>  
<span data-ttu-id="ccaa8-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ccaa8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ccaa8-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ccaa8-107">\<behavior></span></span>  
<span data-ttu-id="ccaa8-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="ccaa8-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccaa8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccaa8-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="ccaa8-110">Typ</span><span class="sxs-lookup"><span data-stu-id="ccaa8-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccaa8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ccaa8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ccaa8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccaa8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ccaa8-113">Attributes</span></span>  
  
|<span data-ttu-id="ccaa8-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ccaa8-114">Attribute</span></span>|<span data-ttu-id="ccaa8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ccaa8-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="ccaa8-116">Wartość, która określa, czy obiekty klienta wywołania zwrotnego wrócić informacje o zarządzanym wyjątku w błędach SOAP do usługi.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="ccaa8-117">Jeśli ustawisz ten atrybut `true` programowo, można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="ccaa8-118">**Uwaga:** zwraca informacje o zarządzanym wyjątku do klientów mogą stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="ccaa8-119">Jest to spowodowane szczegóły wyjątku ujawnienie informacji o implementacji usługi wewnętrznego, które mogą być używane przez nieautoryzowanych klientów.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccaa8-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ccaa8-120">Child Elements</span></span>  
 <span data-ttu-id="ccaa8-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccaa8-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ccaa8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ccaa8-123">Element</span><span class="sxs-lookup"><span data-stu-id="ccaa8-123">Element</span></span>|<span data-ttu-id="ccaa8-124">Opis</span><span class="sxs-lookup"><span data-stu-id="ccaa8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccaa8-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ccaa8-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ccaa8-126">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ccaa8-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccaa8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccaa8-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
