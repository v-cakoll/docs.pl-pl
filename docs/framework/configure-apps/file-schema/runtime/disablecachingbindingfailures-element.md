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
ms.openlocfilehash: 23633cb282b8e59b4df4bcc2cd38717d805a207e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117495"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="bf41b-102">\<disableCachingBindingFailures> Element</span><span class="sxs-lookup"><span data-stu-id="bf41b-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="bf41b-103">Określa, czy należy wyłączyć buforowanie niepowodzeń powiązań, które wystąpiły, ponieważ nie można odnaleźć zestawu przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="bf41b-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="bf41b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf41b-104">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf41b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf41b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bf41b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf41b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf41b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf41b-107">Attributes</span></span>  
  
|<span data-ttu-id="bf41b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf41b-108">Attribute</span></span>|<span data-ttu-id="bf41b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bf41b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf41b-110">enabled</span><span class="sxs-lookup"><span data-stu-id="bf41b-110">enabled</span></span>|<span data-ttu-id="bf41b-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="bf41b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf41b-112">Określa, czy należy wyłączyć buforowanie niepowodzeń powiązań, które wystąpiły, ponieważ nie można odnaleźć zestawu przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="bf41b-112">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bf41b-113">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="bf41b-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="bf41b-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="bf41b-114">Value</span></span>|<span data-ttu-id="bf41b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="bf41b-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf41b-116">0</span><span class="sxs-lookup"><span data-stu-id="bf41b-116">0</span></span>|<span data-ttu-id="bf41b-117">Nie należy wyłączać buforowania niepowodzeń powiązań, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="bf41b-117">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="bf41b-118">Jest to domyślne zachowanie dotyczące powiązań rozpoczynające się od .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="bf41b-118">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="bf41b-119">1</span><span class="sxs-lookup"><span data-stu-id="bf41b-119">1</span></span>|<span data-ttu-id="bf41b-120">Wyłącz buforowanie niepowodzeń powiązań, ponieważ zestaw nie został odnaleziony przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="bf41b-120">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="bf41b-121">To ustawienie przywraca zachowanie powiązania .NET Framework w wersji 1,1.</span><span class="sxs-lookup"><span data-stu-id="bf41b-121">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf41b-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf41b-122">Child Elements</span></span>  
 <span data-ttu-id="bf41b-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf41b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf41b-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf41b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bf41b-125">Element</span><span class="sxs-lookup"><span data-stu-id="bf41b-125">Element</span></span>|<span data-ttu-id="bf41b-126">Opis</span><span class="sxs-lookup"><span data-stu-id="bf41b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf41b-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf41b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bf41b-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bf41b-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf41b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf41b-129">Remarks</span></span>  
 <span data-ttu-id="bf41b-130">Począwszy od .NET Framework w wersji 2,0, domyślnym zachowaniem ładowania zestawów jest buforowanie wszystkich błędów powiązań i ładowania.</span><span class="sxs-lookup"><span data-stu-id="bf41b-130">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="bf41b-131">Oznacza to, że jeśli próba załadowania zestawu nie powiedzie się, kolejne żądania załadowania tego samego zestawu kończą się niepowodzeniem, bez próby zlokalizowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="bf41b-131">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="bf41b-132">Ten element wyłącza zachowanie domyślne dla niepowodzeń powiązań, które występują, ponieważ nie można odnaleźć zestawu w ścieżce sondowania.</span><span class="sxs-lookup"><span data-stu-id="bf41b-132">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="bf41b-133">Te błędy są wyrzucane <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="bf41b-133">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="bf41b-134">Ten element nie ma wpływ na pewne błędy powiązań i ładowania i są zawsze buforowane.</span><span class="sxs-lookup"><span data-stu-id="bf41b-134">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="bf41b-135">Te błędy występują, ponieważ zestaw został znaleziony, ale nie można go załadować.</span><span class="sxs-lookup"><span data-stu-id="bf41b-135">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="bf41b-136">Zgłaszają <xref:System.BadImageFormatException> lub <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="bf41b-136">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="bf41b-137">Poniższa lista zawiera kilka przykładów takich niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="bf41b-137">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="bf41b-138">Jeśli próba załadowania pliku nie jest prawidłowym zestawem, kolejne próby załadowania zestawu zakończą się niepowodzeniem, nawet jeśli zły plik zostanie zastąpiony właściwym zestawem.</span><span class="sxs-lookup"><span data-stu-id="bf41b-138">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="bf41b-139">W przypadku próby załadowania zestawu, który jest zablokowany przez system plików, kolejne próby załadowania zestawu zakończą się niepowodzeniem nawet po wydaniu zestawu przez system plików.</span><span class="sxs-lookup"><span data-stu-id="bf41b-139">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="bf41b-140">Jeśli co najmniej jedna wersja zestawu, który próbujesz załadować, znajduje się w ścieżce sondowania, ale określona wersja, której żądasz, nie należy do nich, kolejne próby załadowania tej wersji będą kończyć się niepowodzeniem, nawet jeśli poprawna wersja zostanie przeniesiona do ścieżki sondowania.</span><span class="sxs-lookup"><span data-stu-id="bf41b-140">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf41b-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf41b-141">Example</span></span>  
 <span data-ttu-id="bf41b-142">Poniższy przykład pokazuje, jak wyłączyć buforowanie niepowodzeń powiązań zestawów, które występują, ponieważ nie znaleziono zestawu przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="bf41b-142">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf41b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf41b-143">See also</span></span>

- [<span data-ttu-id="bf41b-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bf41b-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf41b-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bf41b-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bf41b-146">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bf41b-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
