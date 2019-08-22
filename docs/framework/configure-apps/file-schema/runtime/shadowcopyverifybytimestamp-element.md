---
title: <shadowCopyVerifyByTimestamp>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3ea57364832553d16c7e34fc887b1c9f821602
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663450"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="3ebd4-102">\<shadowCopyVerifyByTimestamp, element ></span><span class="sxs-lookup"><span data-stu-id="3ebd4-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="3ebd4-103">Określa, czy kopiowanie w tle używa domyślnego zachowania uruchamiania wprowadzonego w .NET Framework 4, czy przywraca zachowanie uruchamiania wcześniejszych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3ebd4-104">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3ebd4-104">\<configuration> Element</span></span>  
<span data-ttu-id="3ebd4-105">\<Element > środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3ebd4-105">\<runtime> Element</span></span>  
<span data-ttu-id="3ebd4-106">\<shadowCopyVerifyByTimestamp, element ></span><span class="sxs-lookup"><span data-stu-id="3ebd4-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ebd4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ebd4-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ebd4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ebd4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3ebd4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ebd4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ebd4-110">Attributes</span></span>  
  
|<span data-ttu-id="3ebd4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ebd4-111">Attribute</span></span>|<span data-ttu-id="3ebd4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3ebd4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ebd4-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="3ebd4-113">enabled</span></span>|<span data-ttu-id="3ebd4-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3ebd4-115">Określa, czy domeny aplikacji używające kopiowania w tle porównują sygnatury czasowe zestawów podczas uruchamiania, aby określić, czy zestaw został zaktualizowany przed skopiowaniem zestawu w tle.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3ebd4-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="3ebd4-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="3ebd4-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="3ebd4-117">Value</span></span>|<span data-ttu-id="3ebd4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="3ebd4-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ebd4-119">true</span><span class="sxs-lookup"><span data-stu-id="3ebd4-119">true</span></span>|<span data-ttu-id="3ebd4-120">Podczas uruchamiania program kopiuje tylko te zestawy, które zostały zaktualizowane od czasu ostatniego skopiowania do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="3ebd4-121">Jest to wartość domyślna dla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="3ebd4-122">false</span><span class="sxs-lookup"><span data-stu-id="3ebd4-122">false</span></span>|<span data-ttu-id="3ebd4-123">Przywraca zachowanie uruchamiania poprzednich wersji .NET Framework, które było skopiowane wszystkie pliki podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ebd4-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ebd4-124">Child Elements</span></span>  
 <span data-ttu-id="3ebd4-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ebd4-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ebd4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3ebd4-127">Element</span><span class="sxs-lookup"><span data-stu-id="3ebd4-127">Element</span></span>|<span data-ttu-id="3ebd4-128">Opis</span><span class="sxs-lookup"><span data-stu-id="3ebd4-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3ebd4-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3ebd4-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ebd4-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ebd4-131">Remarks</span></span>  
 <span data-ttu-id="3ebd4-132">Począwszy od .NET Framework 4, zestawy są kopiowane w tle, tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ostatniego skopiowania do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="3ebd4-133">Skraca to czas uruchamiania dla wielu aplikacji używających kopiowania w tle, zgodnie z opisem w obszarze [kopiowania w tle](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3ebd4-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="3ebd4-134">W przypadku aplikacji z wysoką wartością procentową i częstotliwością aktualizacji zestawu mogą nie być korzystne zmiany w zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="3ebd4-135">W takim przypadku można użyć tego elementu, aby przywrócić zachowanie poprzednich wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ebd4-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ebd4-136">Example</span></span>  
 <span data-ttu-id="3ebd4-137">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie podczas uruchamiania kopiowania w tle w .NET Framework 4 i przywrócić zachowanie uruchamiania poprzednich wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ebd4-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ebd4-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ebd4-138">See also</span></span>

- [<span data-ttu-id="3ebd4-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3ebd4-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3ebd4-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3ebd4-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3ebd4-141">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="3ebd4-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
