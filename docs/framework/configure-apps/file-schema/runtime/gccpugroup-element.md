---
title: '&lt;Gccpugroup —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25d083b730117a791fb8ab550b36f7b2e6c5f5be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613716"
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="24d27-102">&lt;Gccpugroup —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="24d27-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="24d27-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup CPU.</span><span class="sxs-lookup"><span data-stu-id="24d27-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="24d27-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="24d27-104">\<configuration></span></span>  
<span data-ttu-id="24d27-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="24d27-105">\<runtime></span></span>  
<span data-ttu-id="24d27-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="24d27-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d27-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="24d27-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24d27-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24d27-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24d27-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24d27-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24d27-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24d27-110">Attributes</span></span>  
  
|<span data-ttu-id="24d27-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24d27-111">Attribute</span></span>|<span data-ttu-id="24d27-112">Opis</span><span class="sxs-lookup"><span data-stu-id="24d27-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="24d27-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="24d27-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="24d27-114">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup CPU.</span><span class="sxs-lookup"><span data-stu-id="24d27-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="24d27-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="24d27-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="24d27-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="24d27-116">Value</span></span>|<span data-ttu-id="24d27-117">Opis</span><span class="sxs-lookup"><span data-stu-id="24d27-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="24d27-118">Wyrzucanie elementów bezużytecznych nie obsługuje wiele grup CPU.</span><span class="sxs-lookup"><span data-stu-id="24d27-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="24d27-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="24d27-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="24d27-120">Wyrzucanie elementów bezużytecznych obsługuje wiele grup CPU, jeśli serwer wyrzucania elementów bezużytecznych jest włączona.</span><span class="sxs-lookup"><span data-stu-id="24d27-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24d27-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24d27-121">Child Elements</span></span>  
 <span data-ttu-id="24d27-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="24d27-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24d27-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24d27-123">Parent Elements</span></span>  
  
|<span data-ttu-id="24d27-124">Element</span><span class="sxs-lookup"><span data-stu-id="24d27-124">Element</span></span>|<span data-ttu-id="24d27-125">Opis</span><span class="sxs-lookup"><span data-stu-id="24d27-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="24d27-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24d27-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="24d27-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="24d27-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24d27-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24d27-128">Remarks</span></span>  
 <span data-ttu-id="24d27-129">Kiedy komputer posiada wiele grup CPU i serwer wyrzucania elementów bezużytecznych jest włączona (zobacz [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucania elementów bezużytecznych we wszystkich grupach CPU i przyjmuje wszystkich rdzeni do konto podczas tworzenia i równoważenie stosów.</span><span class="sxs-lookup"><span data-stu-id="24d27-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24d27-130">Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="24d27-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="24d27-131">Aby włączyć środowisko uruchomieniowe do dystrybucji wątki użytkownika we wszystkich grupach procesorów, należy również włączyć [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="24d27-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d27-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="24d27-132">Example</span></span>  
 <span data-ttu-id="24d27-133">Poniższy przykład pokazuje, jak włączyć wyrzucania elementów bezużytecznych dla wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="24d27-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24d27-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24d27-134">See Also</span></span>  
- [<span data-ttu-id="24d27-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="24d27-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="24d27-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="24d27-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="24d27-137">Instrukcje: Wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="24d27-137">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
- [<span data-ttu-id="24d27-138">Wyrzucanie elementów bezużytecznych stacji roboczych i serwera</span><span class="sxs-lookup"><span data-stu-id="24d27-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
