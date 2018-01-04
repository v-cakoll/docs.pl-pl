---
title: "&lt;Thread_UseAllCpuGroups&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c574d6f5598616776e891ab282c703ce20bc6960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="ea690-102">&lt;Thread_UseAllCpuGroups&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="ea690-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="ea690-103">Określa, czy środowisko uruchomieniowe dystrybuuje zarządzanych wątków we wszystkich grupach procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="ea690-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="ea690-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ea690-104">\<configuration></span></span>  
<span data-ttu-id="ea690-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="ea690-105">\<runtime></span></span>  
<span data-ttu-id="ea690-106">< Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="ea690-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea690-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea690-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea690-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ea690-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea690-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ea690-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea690-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ea690-110">Attributes</span></span>  
  
|<span data-ttu-id="ea690-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ea690-111">Attribute</span></span>|<span data-ttu-id="ea690-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ea690-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ea690-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ea690-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea690-114">Określa, czy środowisko uruchomieniowe dystrybuuje zarządzanych wątków we wszystkich grupach procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="ea690-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ea690-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ea690-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ea690-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ea690-116">Value</span></span>|<span data-ttu-id="ea690-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ea690-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ea690-118">Środowisko uruchomieniowe nie rozpowszechniają zarządzanych wątków wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="ea690-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="ea690-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ea690-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ea690-120">Środowisko uruchomieniowe dystrybuuje zarządzanych wątków wieloma grupami procesorów, jeśli komputer ma wiele grup procesora CPU i [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="ea690-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea690-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ea690-121">Child Elements</span></span>  
 <span data-ttu-id="ea690-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="ea690-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea690-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ea690-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ea690-124">Element</span><span class="sxs-lookup"><span data-stu-id="ea690-124">Element</span></span>|<span data-ttu-id="ea690-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ea690-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ea690-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ea690-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ea690-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ea690-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea690-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea690-128">Remarks</span></span>  
 <span data-ttu-id="ea690-129">Gdy komputer ma wiele grup procesora CPU, włączenie tego elementu powoduje środowiska uruchomieniowego do dystrybucji zarządzanych wątków we wszystkich grupach procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="ea690-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="ea690-130">Aby użyć tej funkcji, należy również włączyć [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, który rozszerza wyrzucanie elementów bezużytecznych do wszystkich grup procesorów i uwzględnia wszystkie rdzenie podczas tworzenia i równoważenie stosów.</span><span class="sxs-lookup"><span data-stu-id="ea690-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="ea690-131">Włączanie [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element wymaga włączenia [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ea690-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="ea690-132">Jeśli te elementy nie są włączone, włączanie `<Thread_UseAllCpuGroups>` element nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="ea690-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea690-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea690-133">Example</span></span>  
 <span data-ttu-id="ea690-134">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="ea690-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea690-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea690-135">See Also</span></span>  
 [<span data-ttu-id="ea690-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ea690-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ea690-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ea690-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ea690-138">\<Gccpugroup — > — Element</span><span class="sxs-lookup"><span data-stu-id="ea690-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
