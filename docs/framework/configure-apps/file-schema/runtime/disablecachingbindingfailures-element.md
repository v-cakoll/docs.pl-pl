---
title: "&lt;disablecachingbindingfailures —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd86bc2f58bc216f741c32a51925d3f4f8ef47df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a><span data-ttu-id="e8f63-102">&lt;disablecachingbindingfailures —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="e8f63-102">&lt;disableCachingBindingFailures&gt; Element</span></span>
<span data-ttu-id="e8f63-103">Określa, czy wyłączyć buforowanie powiązanie błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="e8f63-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="e8f63-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="e8f63-104">\<configuration> Element</span></span>  
<span data-ttu-id="e8f63-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="e8f63-105">\<runtime> Element</span></span>  
<span data-ttu-id="e8f63-106">\<disablecachingbindingfailures — ></span><span class="sxs-lookup"><span data-stu-id="e8f63-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f63-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8f63-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8f63-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8f63-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e8f63-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8f63-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8f63-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8f63-110">Attributes</span></span>  
  
|<span data-ttu-id="e8f63-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8f63-111">Attribute</span></span>|<span data-ttu-id="e8f63-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f63-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8f63-113">włączone</span><span class="sxs-lookup"><span data-stu-id="e8f63-113">enabled</span></span>|<span data-ttu-id="e8f63-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="e8f63-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e8f63-115">Określa, czy wyłączyć buforowanie powiązanie błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="e8f63-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e8f63-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="e8f63-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e8f63-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="e8f63-117">Value</span></span>|<span data-ttu-id="e8f63-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f63-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8f63-119">0</span><span class="sxs-lookup"><span data-stu-id="e8f63-119">0</span></span>|<span data-ttu-id="e8f63-120">Nie wyłączaj buforowanie powiązania błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="e8f63-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="e8f63-121">Jest to domyślne zachowanie wiązania w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e8f63-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="e8f63-122">1</span><span class="sxs-lookup"><span data-stu-id="e8f63-122">1</span></span>|<span data-ttu-id="e8f63-123">Wyłącz buforowanie powiązania błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="e8f63-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="e8f63-124">To ustawienie umożliwia przywrócenie zachowania wiązania programu .NET Framework w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="e8f63-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8f63-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8f63-125">Child Elements</span></span>  
 <span data-ttu-id="e8f63-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="e8f63-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8f63-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8f63-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e8f63-128">Element</span><span class="sxs-lookup"><span data-stu-id="e8f63-128">Element</span></span>|<span data-ttu-id="e8f63-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f63-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e8f63-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8f63-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e8f63-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e8f63-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f63-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8f63-132">Remarks</span></span>  
 <span data-ttu-id="e8f63-133">Domyślnym zachowaniem podczas ładowania zestawów w programie .NET Framework w wersji 2.0, jest w pamięci podręcznej wszystkie błędy ładowania i powiązania.</span><span class="sxs-lookup"><span data-stu-id="e8f63-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="e8f63-134">Oznacza to jeśli próba załadowania zestawu nie powiedzie się, kolejnych żądań wysyłanych do załadowania tego samego zestawu nie bezpośrednio, bez próba zlokalizować zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8f63-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="e8f63-135">Ten element wyłącza to zachowanie domyślne dla powiązania błędów występujących, ponieważ nie można odnaleźć zestawu w ścieżce sondowania.</span><span class="sxs-lookup"><span data-stu-id="e8f63-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="e8f63-136">Te błędy throw <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="e8f63-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="e8f63-137">Niektóre powiązania błędy ładowania tego elementu nie podlegają i zawsze są buforowane.</span><span class="sxs-lookup"><span data-stu-id="e8f63-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="e8f63-138">Te wystąpienia, ponieważ zestaw został znaleziony, ale nie można załadować.</span><span class="sxs-lookup"><span data-stu-id="e8f63-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="e8f63-139">Generują one <xref:System.BadImageFormatException> lub <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="e8f63-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="e8f63-140">Poniższa lista zawiera kilka przykładów tych błędów.</span><span class="sxs-lookup"><span data-stu-id="e8f63-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="e8f63-141">Jeśli próba załadowania pliku nie jest prawidłowym zestawem, kolejne próby ładowania zestawu zakończy się niepowodzeniem, nawet jeśli nieprawidłowego pliku jest zastępowany poprawny zestaw.</span><span class="sxs-lookup"><span data-stu-id="e8f63-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="e8f63-142">Próba załadowania zestawu, który jest zablokowany przez system plików, kolejne próby ładowania zestawu zakończy się niepowodzeniem nawet po wydaniu zestaw przez system plików.</span><span class="sxs-lookup"><span data-stu-id="e8f63-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="e8f63-143">Jeśli wersji co najmniej jednego zestawu, który próbujesz załadować znajduje się w ścieżce sondowania, ale żądanej wersji nie jest między nimi, kolejnych prób załadować tej wersji zakończy się niepowodzeniem, nawet jeśli poprawna wersja jest przenoszony do ścieżki próbkowania.</span><span class="sxs-lookup"><span data-stu-id="e8f63-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f63-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8f63-144">Example</span></span>  
 <span data-ttu-id="e8f63-145">Poniższy przykład pokazuje, jak wyłączenie buforowania zestawu powiązania błędów występujących, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="e8f63-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8f63-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8f63-146">See Also</span></span>  
 [<span data-ttu-id="e8f63-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e8f63-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="e8f63-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8f63-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e8f63-149">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e8f63-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
