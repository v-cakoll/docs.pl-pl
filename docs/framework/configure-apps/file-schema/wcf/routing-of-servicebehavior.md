---
title: <routing> dla <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397731"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="11c44-102">\<> \<routingu ></span><span class="sxs-lookup"><span data-stu-id="11c44-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="11c44-103">Zapewnia dostęp do usługi routingu w czasie wykonywania w celu umożliwienia dynamicznej modyfikacji konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="11c44-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
<span data-ttu-id="11c44-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="11c44-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="11c44-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="11c44-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="11c44-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="11c44-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="11c44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="11c44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="11c44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="11c44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="11c44-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> routingu**</span><span class="sxs-lookup"><span data-stu-id="11c44-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c44-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="11c44-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11c44-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11c44-111">Attributes and Elements</span></span>  
 <span data-ttu-id="11c44-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="11c44-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11c44-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11c44-113">Attributes</span></span>  
  
|<span data-ttu-id="11c44-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="11c44-114">Attribute</span></span>|<span data-ttu-id="11c44-115">Opis</span><span class="sxs-lookup"><span data-stu-id="11c44-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11c44-116">filterTable</span><span class="sxs-lookup"><span data-stu-id="11c44-116">filterTable</span></span>|<span data-ttu-id="11c44-117">Ciąg określający nazwę tabeli routingu zawierającej filtry, które mają być oceniane przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="11c44-117">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="11c44-118">Ta wartość musi być zgodna `name` z atrybutem [ \<>](filtertable.md) [ \<](filtertables.md) filtrowania elementu w sekcji > filterTables.</span><span class="sxs-lookup"><span data-stu-id="11c44-118">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="11c44-119">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="11c44-119">routeOnHeaderOnly</span></span>|<span data-ttu-id="11c44-120">Wartość logiczna określająca, czy filtr będzie przebadał zarówno treść komunikatu, jak i nagłówek, czy tylko nagłówek.</span><span class="sxs-lookup"><span data-stu-id="11c44-120">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="11c44-121">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="11c44-121">The default is `true`.</span></span>|  
|<span data-ttu-id="11c44-122">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="11c44-122">soapProcessingEnabled</span></span>|<span data-ttu-id="11c44-123">Wartość logiczna określająca, czy należy wykonać przetwarzanie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="11c44-123">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11c44-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11c44-124">Child Elements</span></span>  
 <span data-ttu-id="11c44-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="11c44-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11c44-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11c44-126">Parent Elements</span></span>  
  
|<span data-ttu-id="11c44-127">Element</span><span class="sxs-lookup"><span data-stu-id="11c44-127">Element</span></span>|<span data-ttu-id="11c44-128">Opis</span><span class="sxs-lookup"><span data-stu-id="11c44-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11c44-129">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="11c44-129">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="11c44-130">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="11c44-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11c44-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11c44-131">Remarks</span></span>  
 <span data-ttu-id="11c44-132">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji włącza Routing dla usługi.</span><span class="sxs-lookup"><span data-stu-id="11c44-132">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="11c44-133">Możesz określić rzeczywistą tabelę routingu, która ma być używana przez usługę w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="11c44-133">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="11c44-134">Za pomocą tej sekcji konfiguracji można zmienić ustawienia routingu na bieżąco po zmianie wzorca wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="11c44-134">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="11c44-135">W środowisku uruchomieniowym można zarejestrować własne rozszerzenie routingu z nowymi ustawieniami routingu, a usługa routingu rozpocznie korzystanie z zaktualizowanych informacji o konfiguracji dla nowych komunikatów i sesji przy jednoczesnym pozostawieniu komunikatów/sesji w locie przy użyciu dowolnych reguł Umieść po rozpoczęciu pracy.</span><span class="sxs-lookup"><span data-stu-id="11c44-135">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="11c44-136">Umożliwia to bezpieczne dla sesji ponowne odtwarzanie usługi routingu podczas środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="11c44-136">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
