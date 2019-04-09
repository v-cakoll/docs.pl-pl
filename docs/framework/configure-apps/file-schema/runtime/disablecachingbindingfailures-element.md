---
title: <disableCachingBindingFailures> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4893adaf528f1a9ef8fc8eab8027406fd8520cc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159279"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="a543c-102">\<disableCachingBindingFailures> Element</span><span class="sxs-lookup"><span data-stu-id="a543c-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="a543c-103">Określa, czy należy wyłączyć buforowanie powiązania błędy, które występują, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="a543c-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="a543c-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="a543c-104">\<configuration> Element</span></span>  
<span data-ttu-id="a543c-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="a543c-105">\<runtime> Element</span></span>  
<span data-ttu-id="a543c-106">\<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="a543c-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a543c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a543c-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a543c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a543c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a543c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a543c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a543c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a543c-110">Attributes</span></span>  
  
|<span data-ttu-id="a543c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a543c-111">Attribute</span></span>|<span data-ttu-id="a543c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a543c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a543c-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="a543c-113">enabled</span></span>|<span data-ttu-id="a543c-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a543c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a543c-115">Określa, czy należy wyłączyć buforowanie powiązania błędy, które występują, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="a543c-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a543c-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="a543c-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="a543c-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="a543c-117">Value</span></span>|<span data-ttu-id="a543c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a543c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a543c-119">0</span><span class="sxs-lookup"><span data-stu-id="a543c-119">0</span></span>|<span data-ttu-id="a543c-120">Nie należy wyłączać buforowanie powiązania błędy, które występują, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="a543c-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="a543c-121">Jest to domyślne zachowanie powiązania, począwszy od programu .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="a543c-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="a543c-122">1</span><span class="sxs-lookup"><span data-stu-id="a543c-122">1</span></span>|<span data-ttu-id="a543c-123">Wyłącz buforowanie powiązania błędy, które występują, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="a543c-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="a543c-124">To ustawienie zostanie przywrócony zachowanie wiązania programu .NET Framework w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="a543c-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a543c-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a543c-125">Child Elements</span></span>  
 <span data-ttu-id="a543c-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="a543c-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a543c-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a543c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a543c-128">Element</span><span class="sxs-lookup"><span data-stu-id="a543c-128">Element</span></span>|<span data-ttu-id="a543c-129">Opis</span><span class="sxs-lookup"><span data-stu-id="a543c-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a543c-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a543c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a543c-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a543c-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a543c-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a543c-132">Remarks</span></span>  
 <span data-ttu-id="a543c-133">Począwszy od programu .NET Framework w wersji 2.0, domyślne zachowanie ładowania zestawów jest wszystkie powiązania i podczas ładowania błędów w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a543c-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="a543c-134">Oznacza to jeśli próba załadowania zestawu zakończy się niepowodzeniem, kolejne żądania do tego samego zestawu obciążenia nie natychmiast, bez próby zlokalizowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="a543c-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="a543c-135">Ten element wyłącza tego domyślne zachowanie dla powiązania błędy, które występują, ponieważ nie można odnaleźć zestawu w ścieżce badania.</span><span class="sxs-lookup"><span data-stu-id="a543c-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="a543c-136">Te błędy throw <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="a543c-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="a543c-137">Niektóre wiązania błędów ładowania nie dotyczy tego elementu i zawsze są buforowane.</span><span class="sxs-lookup"><span data-stu-id="a543c-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="a543c-138">Te błędy występują, ponieważ zestaw został znaleziony, ale nie można go załadować.</span><span class="sxs-lookup"><span data-stu-id="a543c-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="a543c-139">Rzuć <xref:System.BadImageFormatException> lub <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="a543c-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="a543c-140">Poniższa lista zawiera kilka przykładów tych błędów.</span><span class="sxs-lookup"><span data-stu-id="a543c-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="a543c-141">Jeśli użytkownik podejmie próbę załadowania pliku nie jest prawidłowym zestawem, kolejne próby załadowania zestawu zakończy się niepowodzeniem, nawet wtedy, gdy nieprawidłowego pliku zostaje zastąpiona opcją poprawny zestaw.</span><span class="sxs-lookup"><span data-stu-id="a543c-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="a543c-142">Jeśli użytkownik podejmie próbę załadowania zestawu, który jest zablokowany przez system plików, kolejne próby załadowania zestawu zakończy się niepowodzeniem nawet po opublikowaniu zestawu w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="a543c-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="a543c-143">Co najmniej wersji zestawu, który próbujesz załadować znajduje się w ścieżce badania, ale określonej wersji, którego zażądano nie znajduje się wśród nich, kolejne próby załadowania tej wersji zakończy się niepowodzeniem nawet wtedy, gdy poprawnej wersji jest przenoszony do badania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a543c-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a543c-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="a543c-144">Example</span></span>  
 <span data-ttu-id="a543c-145">Poniższy przykład pokazuje, jak wyłączyć buforowanie niepowodzenia powiązań zestawów, które występują, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="a543c-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a543c-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a543c-146">See also</span></span>

- [<span data-ttu-id="a543c-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a543c-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a543c-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a543c-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a543c-149">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a543c-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
