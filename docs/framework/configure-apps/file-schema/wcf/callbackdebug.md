---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 1aa292a3fe06af9cf1dbc53ebf5bbdf9841be8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687378"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="4af19-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="4af19-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="4af19-103">Określa usługę debugowania dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4af19-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="4af19-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4af19-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4af19-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="4af19-105">\<behaviors></span></span>  
<span data-ttu-id="4af19-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4af19-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4af19-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4af19-107">\<behavior></span></span>  
<span data-ttu-id="4af19-108">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="4af19-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af19-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4af19-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="4af19-110">Typ</span><span class="sxs-lookup"><span data-stu-id="4af19-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4af19-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4af19-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4af19-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4af19-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4af19-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4af19-113">Attributes</span></span>  
  
|<span data-ttu-id="4af19-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4af19-114">Attribute</span></span>|<span data-ttu-id="4af19-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4af19-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="4af19-116">Wartość, która określa, czy obiekty klienta wywołania zwrotnego zwracają informacje o zarządzanym wyjątku w błędach SOAP powrót do usługi.</span><span class="sxs-lookup"><span data-stu-id="4af19-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="4af19-117">Jeśli ten atrybut jest ustawiony `true` programowo, można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania.</span><span class="sxs-lookup"><span data-stu-id="4af19-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="4af19-118">**Uwaga:**  Zwracanie informacje o zarządzanym wyjątku do klientów może stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="4af19-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="4af19-119">Jest to spowodowane szczegóły wyjątku ujawniać informacje o implementacji usługi wewnętrznej, która mogłaby być używana przez nieautoryzowane klientów.</span><span class="sxs-lookup"><span data-stu-id="4af19-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4af19-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4af19-120">Child Elements</span></span>  
 <span data-ttu-id="4af19-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="4af19-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4af19-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4af19-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4af19-123">Element</span><span class="sxs-lookup"><span data-stu-id="4af19-123">Element</span></span>|<span data-ttu-id="4af19-124">Opis</span><span class="sxs-lookup"><span data-stu-id="4af19-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4af19-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4af19-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4af19-126">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4af19-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4af19-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4af19-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
