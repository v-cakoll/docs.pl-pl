---
title: '&lt;Gccpugroup —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="b364c-102">&lt;Gccpugroup —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="b364c-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="b364c-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="b364c-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="b364c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b364c-104">\<configuration></span></span>  
<span data-ttu-id="b364c-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="b364c-105">\<runtime></span></span>  
<span data-ttu-id="b364c-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="b364c-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b364c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b364c-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b364c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b364c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b364c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b364c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b364c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b364c-110">Attributes</span></span>  
  
|<span data-ttu-id="b364c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b364c-111">Attribute</span></span>|<span data-ttu-id="b364c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b364c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b364c-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b364c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b364c-114">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="b364c-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b364c-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="b364c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b364c-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b364c-116">Value</span></span>|<span data-ttu-id="b364c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b364c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b364c-118">Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="b364c-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="b364c-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b364c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b364c-120">Wyrzucanie elementów bezużytecznych obsługuje wiele grup Procesora, jeśli włączono odzyskiwanie pamięci na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b364c-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b364c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b364c-121">Child Elements</span></span>  
 <span data-ttu-id="b364c-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b364c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b364c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b364c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b364c-124">Element</span><span class="sxs-lookup"><span data-stu-id="b364c-124">Element</span></span>|<span data-ttu-id="b364c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b364c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b364c-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b364c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b364c-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b364c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b364c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b364c-128">Remarks</span></span>  
 <span data-ttu-id="b364c-129">Gdy komputer ma wiele grup procesora CPU i odzyskiwanie pamięci na serwerze jest włączone (zobacz [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU i pobiera wszystkie rdzenie do konto podczas tworzenia i równoważenie stosów.</span><span class="sxs-lookup"><span data-stu-id="b364c-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b364c-130">Ten element dotyczy tylko pamięci kolekcji wątków.</span><span class="sxs-lookup"><span data-stu-id="b364c-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="b364c-131">Aby włączyć środowisko uruchomieniowe do dystrybucji użytkownika wątki we wszystkich grupach Procesora, należy również włączyć [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b364c-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b364c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b364c-132">Example</span></span>  
 <span data-ttu-id="b364c-133">Poniższy przykład przedstawia sposób włączania wyrzucanie elementów bezużytecznych do wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="b364c-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b364c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b364c-134">See Also</span></span>  
 [<span data-ttu-id="b364c-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b364c-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="b364c-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b364c-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b364c-137">Porady: wyłączanie współbieżne odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="b364c-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="b364c-138">Wyrzucanie elementów bezużytecznych stacji roboczej i serwera</span><span class="sxs-lookup"><span data-stu-id="b364c-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
