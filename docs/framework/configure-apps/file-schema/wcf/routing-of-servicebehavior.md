---
title: <routing> dla <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934198"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="9ef9a-102">\<> \<routingu ></span><span class="sxs-lookup"><span data-stu-id="9ef9a-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="9ef9a-103">Zapewnia dostęp do usługi routingu w czasie wykonywania w celu umożliwienia dynamicznej modyfikacji konfiguracji routingu.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="9ef9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9ef9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9ef9a-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="9ef9a-105">\<behaviors></span></span>  
<span data-ttu-id="9ef9a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9ef9a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9ef9a-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="9ef9a-107">\<behavior></span></span>  
<span data-ttu-id="9ef9a-108">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="9ef9a-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef9a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ef9a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ef9a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ef9a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ef9a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ef9a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ef9a-112">Attributes</span></span>  
  
|<span data-ttu-id="9ef9a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9ef9a-113">Attribute</span></span>|<span data-ttu-id="9ef9a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9ef9a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ef9a-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="9ef9a-115">filterTable</span></span>|<span data-ttu-id="9ef9a-116">Ciąg określający nazwę tabeli routingu zawierającej filtry, które mają być oceniane przez usługę routingu.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="9ef9a-117">Ta wartość musi być zgodna `name` z atrybutem [ \<>](filtertable.md) [ \<](filtertables.md) filtrowania elementu w sekcji > filterTables.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-117">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="9ef9a-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="9ef9a-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="9ef9a-119">Wartość logiczna określająca, czy filtr będzie przebadał zarówno treść komunikatu, jak i nagłówek, czy tylko nagłówek.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="9ef9a-120">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-120">The default is `true`.</span></span>|  
|<span data-ttu-id="9ef9a-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="9ef9a-121">soapProcessingEnabled</span></span>|<span data-ttu-id="9ef9a-122">Wartość logiczna określająca, czy należy wykonać przetwarzanie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ef9a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ef9a-123">Child Elements</span></span>  
 <span data-ttu-id="9ef9a-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ef9a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ef9a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9ef9a-126">Element</span><span class="sxs-lookup"><span data-stu-id="9ef9a-126">Element</span></span>|<span data-ttu-id="9ef9a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="9ef9a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ef9a-128">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="9ef9a-128">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9ef9a-129">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ef9a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ef9a-130">Remarks</span></span>  
 <span data-ttu-id="9ef9a-131">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji włącza Routing dla usługi.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="9ef9a-132">Możesz określić rzeczywistą tabelę routingu, która ma być używana przez usługę w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="9ef9a-133">Za pomocą tej sekcji konfiguracji można zmienić ustawienia routingu na bieżąco po zmianie wzorca wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="9ef9a-134">W środowisku uruchomieniowym można zarejestrować własne rozszerzenie routingu z nowymi ustawieniami routingu, a usługa routingu rozpocznie korzystanie z zaktualizowanych informacji o konfiguracji dla nowych komunikatów i sesji przy jednoczesnym pozostawieniu komunikatów/sesji w locie przy użyciu dowolnych reguł Umieść po rozpoczęciu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="9ef9a-135">Umożliwia to bezpieczne dla sesji ponowne odtwarzanie usługi routingu podczas środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9ef9a-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
