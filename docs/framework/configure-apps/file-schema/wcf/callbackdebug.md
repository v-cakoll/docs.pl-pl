---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926309"
---
# <a name="callbackdebug"></a><span data-ttu-id="5b8f2-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="5b8f2-101">\<callbackDebug></span></span>
<span data-ttu-id="5b8f2-102">Określa debugowanie usługi dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5b8f2-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="5b8f2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5b8f2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b8f2-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="5b8f2-104">\<behaviors></span></span>  
<span data-ttu-id="5b8f2-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5b8f2-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="5b8f2-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="5b8f2-106">\<behavior></span></span>  
<span data-ttu-id="5b8f2-107">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="5b8f2-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b8f2-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b8f2-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="5b8f2-109">Typ</span><span class="sxs-lookup"><span data-stu-id="5b8f2-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b8f2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5b8f2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5b8f2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b8f2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5b8f2-112">Attributes</span></span>  
  
|<span data-ttu-id="5b8f2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5b8f2-113">Attribute</span></span>|<span data-ttu-id="5b8f2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5b8f2-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="5b8f2-115">Wartość określająca, czy obiekty wywołania zwrotnego klienta zwracają informacje o zarządzanym wyjątku w błędach protokołu SOAP z powrotem do usługi.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="5b8f2-116">Jeśli ten atrybut zostanie ustawiony na `true` programowo, można włączyć przepływ informacji o zarządzanym wyjątku w obiekcie wywołania zwrotnego klienta z powrotem do usługi na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="5b8f2-117">**Ostrzeżenie**  Zwrócenie informacji o wyjątku zarządzanym do klientów może stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="5b8f2-118">Wynika to z faktu, że szczegóły wyjątku ujawniają informacje o implementacji wewnętrznej usługi, która może być używana przez nieautoryzowanych klientów.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b8f2-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5b8f2-119">Child Elements</span></span>  
 <span data-ttu-id="5b8f2-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b8f2-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5b8f2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5b8f2-122">Element</span><span class="sxs-lookup"><span data-stu-id="5b8f2-122">Element</span></span>|<span data-ttu-id="5b8f2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="5b8f2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b8f2-124">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="5b8f2-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5b8f2-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5b8f2-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b8f2-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b8f2-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
