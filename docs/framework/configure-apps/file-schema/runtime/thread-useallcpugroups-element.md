---
title: <Thread_UseAllCpuGroups> Element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 236953cc1a430a1dd2a2fbb633c7ef06e6ba200f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230840"
---
# <a name="threaduseallcpugroups-element"></a><span data-ttu-id="f29b7-102">\<Thread_UseAllCpuGroups> Element</span><span class="sxs-lookup"><span data-stu-id="f29b7-102">\<Thread_UseAllCpuGroups> Element</span></span>
<span data-ttu-id="f29b7-103">Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="f29b7-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="f29b7-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f29b7-104">\<configuration></span></span>  
<span data-ttu-id="f29b7-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="f29b7-105">\<runtime></span></span>  
<span data-ttu-id="f29b7-106"><Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="f29b7-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f29b7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f29b7-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f29b7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f29b7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f29b7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f29b7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f29b7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f29b7-110">Attributes</span></span>  
  
|<span data-ttu-id="f29b7-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f29b7-111">Attribute</span></span>|<span data-ttu-id="f29b7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f29b7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f29b7-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f29b7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f29b7-114">Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="f29b7-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f29b7-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="f29b7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f29b7-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="f29b7-116">Value</span></span>|<span data-ttu-id="f29b7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f29b7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f29b7-118">Środowisko uruchomieniowe nie rozkłada zarządzanych wątków w obrębie wielu grup CPU.</span><span class="sxs-lookup"><span data-stu-id="f29b7-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="f29b7-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="f29b7-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f29b7-120">Środowisko uruchomieniowe rozprowadza wątki zarządzane WE wiele grup CPU, jeśli komputer ma wiele grup CPU i [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="f29b7-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f29b7-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f29b7-121">Child Elements</span></span>  
 <span data-ttu-id="f29b7-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="f29b7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f29b7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f29b7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f29b7-124">Element</span><span class="sxs-lookup"><span data-stu-id="f29b7-124">Element</span></span>|<span data-ttu-id="f29b7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f29b7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f29b7-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f29b7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f29b7-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f29b7-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f29b7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f29b7-128">Remarks</span></span>  
 <span data-ttu-id="f29b7-129">Kiedy komputer posiada wiele grup CPU, włączenie tego elementu powoduje dystrybucję zarządzanych wątków we wszystkich grupach CPU środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="f29b7-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="f29b7-130">Aby użyć tej funkcji, należy również włączyć [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, który rozszerza wyrzucania elementów bezużytecznych na wszystkich grupach CPU i uwzględnia wszystkich rdzeni podczas tworzenia i równoważenie stosów.</span><span class="sxs-lookup"><span data-stu-id="f29b7-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="f29b7-131">Włączanie [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element wymaga Włączanie [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f29b7-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="f29b7-132">Jeśli te elementy nie są włączone, umożliwiając `<Thread_UseAllCpuGroups>` element nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="f29b7-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f29b7-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f29b7-133">Example</span></span>  
 <span data-ttu-id="f29b7-134">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="f29b7-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f29b7-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f29b7-135">See also</span></span>

- [<span data-ttu-id="f29b7-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f29b7-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f29b7-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f29b7-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f29b7-138">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="f29b7-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
