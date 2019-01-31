---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 62ce1bc179c7215d4988e4c6bda08025c3d3e5de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286315"
---
# <a name="callbackdebug"></a><span data-ttu-id="a7d74-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="a7d74-101">\<callbackDebug></span></span>
<span data-ttu-id="a7d74-102">Określa usługę debugowania dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7d74-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="a7d74-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7d74-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7d74-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="a7d74-104">\<behaviors></span></span>  
<span data-ttu-id="a7d74-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a7d74-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="a7d74-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="a7d74-106">\<behavior></span></span>  
<span data-ttu-id="a7d74-107">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="a7d74-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d74-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7d74-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="a7d74-109">Typ</span><span class="sxs-lookup"><span data-stu-id="a7d74-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7d74-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a7d74-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7d74-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a7d74-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7d74-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a7d74-112">Attributes</span></span>  
  
|<span data-ttu-id="a7d74-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7d74-113">Attribute</span></span>|<span data-ttu-id="a7d74-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a7d74-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="a7d74-115">Wartość, która określa, czy obiekty klienta wywołania zwrotnego zwracają informacje o zarządzanym wyjątku w błędach SOAP powrót do usługi.</span><span class="sxs-lookup"><span data-stu-id="a7d74-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="a7d74-116">Jeśli ten atrybut jest ustawiony `true` programowo, można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania.</span><span class="sxs-lookup"><span data-stu-id="a7d74-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="a7d74-117">**Uwaga:**  Zwracanie informacje o zarządzanym wyjątku do klientów może stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="a7d74-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="a7d74-118">Jest to spowodowane szczegóły wyjątku ujawniać informacje o implementacji usługi wewnętrznej, która mogłaby być używana przez nieautoryzowane klientów.</span><span class="sxs-lookup"><span data-stu-id="a7d74-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7d74-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a7d74-119">Child Elements</span></span>  
 <span data-ttu-id="a7d74-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="a7d74-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7d74-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a7d74-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a7d74-122">Element</span><span class="sxs-lookup"><span data-stu-id="a7d74-122">Element</span></span>|<span data-ttu-id="a7d74-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a7d74-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7d74-124">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="a7d74-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a7d74-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a7d74-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7d74-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7d74-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
