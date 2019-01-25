---
title: '&lt;Thread_UseAllCpuGroups&gt; Element'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80f67502c61df13b17cfb3b75564d710e5fad2f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579944"
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="ba8ed-102">&lt;Thread_UseAllCpuGroups&gt; Element</span><span class="sxs-lookup"><span data-stu-id="ba8ed-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="ba8ed-103">Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="ba8ed-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ba8ed-104">\<configuration></span></span>  
<span data-ttu-id="ba8ed-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="ba8ed-105">\<runtime></span></span>  
<span data-ttu-id="ba8ed-106"><Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="ba8ed-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba8ed-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba8ed-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba8ed-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba8ed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ba8ed-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba8ed-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba8ed-110">Attributes</span></span>  
  
|<span data-ttu-id="ba8ed-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ba8ed-111">Attribute</span></span>|<span data-ttu-id="ba8ed-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ba8ed-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ba8ed-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ba8ed-114">Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ba8ed-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ba8ed-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ba8ed-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ba8ed-116">Value</span></span>|<span data-ttu-id="ba8ed-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ba8ed-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ba8ed-118">Środowisko uruchomieniowe nie rozkłada zarządzanych wątków w obrębie wielu grup CPU.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="ba8ed-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ba8ed-120">Środowisko uruchomieniowe rozprowadza wątki zarządzane WE wiele grup CPU, jeśli komputer ma wiele grup CPU i [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba8ed-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba8ed-121">Child Elements</span></span>  
 <span data-ttu-id="ba8ed-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba8ed-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba8ed-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ba8ed-124">Element</span><span class="sxs-lookup"><span data-stu-id="ba8ed-124">Element</span></span>|<span data-ttu-id="ba8ed-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ba8ed-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ba8ed-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ba8ed-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba8ed-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba8ed-128">Remarks</span></span>  
 <span data-ttu-id="ba8ed-129">Kiedy komputer posiada wiele grup CPU, włączenie tego elementu powoduje dystrybucję zarządzanych wątków we wszystkich grupach CPU środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="ba8ed-130">Aby użyć tej funkcji, należy również włączyć [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, który rozszerza wyrzucania elementów bezużytecznych na wszystkich grupach CPU i uwzględnia wszystkich rdzeni podczas tworzenia i równoważenie stosów.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="ba8ed-131">Włączanie [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element wymaga Włączanie [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="ba8ed-132">Jeśli te elementy nie są włączone, umożliwiając `<Thread_UseAllCpuGroups>` element nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba8ed-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba8ed-133">Example</span></span>  
 <span data-ttu-id="ba8ed-134">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="ba8ed-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba8ed-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba8ed-135">See also</span></span>
- [<span data-ttu-id="ba8ed-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ba8ed-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ba8ed-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ba8ed-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ba8ed-138">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="ba8ed-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
