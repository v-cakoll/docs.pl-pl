---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400571"
---
# <a name="callbackdebug"></a><span data-ttu-id="09c55-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="09c55-101">\<callbackDebug></span></span>
<span data-ttu-id="09c55-102">Określa debugowanie usługi dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="09c55-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
<span data-ttu-id="09c55-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="09c55-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09c55-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="09c55-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="09c55-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="09c55-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="09c55-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="09c55-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="09c55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="09c55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="09c55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackDebug >**</span><span class="sxs-lookup"><span data-stu-id="09c55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c55-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="09c55-109">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="09c55-110">Typ</span><span class="sxs-lookup"><span data-stu-id="09c55-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09c55-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="09c55-111">Attributes and Elements</span></span>  
 <span data-ttu-id="09c55-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="09c55-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09c55-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="09c55-113">Attributes</span></span>  
  
|<span data-ttu-id="09c55-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="09c55-114">Attribute</span></span>|<span data-ttu-id="09c55-115">Opis</span><span class="sxs-lookup"><span data-stu-id="09c55-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="09c55-116">Wartość określająca, czy obiekty wywołania zwrotnego klienta zwracają informacje o zarządzanym wyjątku w błędach protokołu SOAP z powrotem do usługi.</span><span class="sxs-lookup"><span data-stu-id="09c55-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="09c55-117">Jeśli ten atrybut zostanie ustawiony na `true` programowo, można włączyć przepływ informacji o zarządzanym wyjątku w obiekcie wywołania zwrotnego klienta z powrotem do usługi na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="09c55-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="09c55-118">**Ostrzeżenie**  Zwrócenie informacji o wyjątku zarządzanym do klientów może stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="09c55-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="09c55-119">Wynika to z faktu, że szczegóły wyjątku ujawniają informacje o implementacji wewnętrznej usługi, która może być używana przez nieautoryzowanych klientów.</span><span class="sxs-lookup"><span data-stu-id="09c55-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09c55-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="09c55-120">Child Elements</span></span>  
 <span data-ttu-id="09c55-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="09c55-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09c55-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="09c55-122">Parent Elements</span></span>  
  
|<span data-ttu-id="09c55-123">Element</span><span class="sxs-lookup"><span data-stu-id="09c55-123">Element</span></span>|<span data-ttu-id="09c55-124">Opis</span><span class="sxs-lookup"><span data-stu-id="09c55-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09c55-125">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="09c55-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="09c55-126">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="09c55-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09c55-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09c55-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
