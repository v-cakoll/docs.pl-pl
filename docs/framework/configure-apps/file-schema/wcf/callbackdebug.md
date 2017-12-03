---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bb730a00358f771408ff0431ff2ab77623354a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="52387-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="52387-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="52387-103">Określa usługę debugowania dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] obiektu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="52387-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="52387-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="52387-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="52387-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="52387-105">\<behaviors></span></span>  
<span data-ttu-id="52387-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="52387-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="52387-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="52387-107">\<behavior></span></span>  
<span data-ttu-id="52387-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="52387-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52387-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="52387-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="52387-110">Typ</span><span class="sxs-lookup"><span data-stu-id="52387-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52387-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="52387-111">Attributes and Elements</span></span>  
 <span data-ttu-id="52387-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="52387-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52387-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="52387-113">Attributes</span></span>  
  
|<span data-ttu-id="52387-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="52387-114">Attribute</span></span>|<span data-ttu-id="52387-115">Opis</span><span class="sxs-lookup"><span data-stu-id="52387-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="52387-116">Wartość, która określa, czy obiekty klienta wywołania zwrotnego wrócić informacje o zarządzanym wyjątku w błędach SOAP do usługi.</span><span class="sxs-lookup"><span data-stu-id="52387-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="52387-117">Jeśli ustawisz ten atrybut `true` programowo, można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania.</span><span class="sxs-lookup"><span data-stu-id="52387-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="52387-118">**Uwaga:** zwraca informacje o zarządzanym wyjątku do klientów mogą stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="52387-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="52387-119">Jest to spowodowane szczegóły wyjątku ujawnienie informacji o implementacji usługi wewnętrznego, które mogą być używane przez nieautoryzowanych klientów.</span><span class="sxs-lookup"><span data-stu-id="52387-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52387-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52387-120">Child Elements</span></span>  
 <span data-ttu-id="52387-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="52387-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52387-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52387-122">Parent Elements</span></span>  
  
|<span data-ttu-id="52387-123">Element</span><span class="sxs-lookup"><span data-stu-id="52387-123">Element</span></span>|<span data-ttu-id="52387-124">Opis</span><span class="sxs-lookup"><span data-stu-id="52387-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52387-125">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="52387-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="52387-126">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="52387-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52387-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52387-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
