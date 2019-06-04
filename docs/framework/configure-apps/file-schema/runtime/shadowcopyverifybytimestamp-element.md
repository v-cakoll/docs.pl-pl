---
title: <shadowCopyVerifyByTimestamp>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4187d266d82783ebb72073c1da92faff95352884
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489381"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="ac9a6-102">\<shadowCopyVerifyByTimestamp > Element</span><span class="sxs-lookup"><span data-stu-id="ac9a6-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="ac9a6-103">Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzone w .NET Framework 4 lub powraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ac9a6-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="ac9a6-104">\<configuration> Element</span></span>  
<span data-ttu-id="ac9a6-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="ac9a6-105">\<runtime> Element</span></span>  
<span data-ttu-id="ac9a6-106">\<shadowCopyVerifyByTimestamp > Element</span><span class="sxs-lookup"><span data-stu-id="ac9a6-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac9a6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac9a6-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac9a6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ac9a6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ac9a6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac9a6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac9a6-110">Attributes</span></span>  
  
|<span data-ttu-id="ac9a6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ac9a6-111">Attribute</span></span>|<span data-ttu-id="ac9a6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ac9a6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac9a6-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="ac9a6-113">enabled</span></span>|<span data-ttu-id="ac9a6-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac9a6-115">Określa, czy domen aplikacji, które używają kopiowania w tle porównania sygnatury czasowe zestawów podczas uruchamiania, aby ustalić, czy zestaw został zaktualizowany przed Kopiowanie zestawów w tle.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ac9a6-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ac9a6-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="ac9a6-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="ac9a6-117">Value</span></span>|<span data-ttu-id="ac9a6-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ac9a6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac9a6-119">true</span><span class="sxs-lookup"><span data-stu-id="ac9a6-119">true</span></span>|<span data-ttu-id="ac9a6-120">Podczas uruchamiania kopiuje tylko zestawy, które zostały zaktualizowane, ponieważ ich ostatniego zostały skopiowane do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="ac9a6-121">Jest to wartość domyślna dla programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="ac9a6-122">false</span><span class="sxs-lookup"><span data-stu-id="ac9a6-122">false</span></span>|<span data-ttu-id="ac9a6-123">Zostanie przywrócony zachowanie uruchamiania poprzednich wersji programu .NET Framework, który został do skopiowania wszystkich plików podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac9a6-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ac9a6-124">Child Elements</span></span>  
 <span data-ttu-id="ac9a6-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac9a6-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ac9a6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ac9a6-127">Element</span><span class="sxs-lookup"><span data-stu-id="ac9a6-127">Element</span></span>|<span data-ttu-id="ac9a6-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ac9a6-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac9a6-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ac9a6-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac9a6-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac9a6-131">Remarks</span></span>  
 <span data-ttu-id="ac9a6-132">Począwszy od programu .NET Framework 4, zestawy są kopie w tle woluminów tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ich ostatniego zostały skopiowane do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="ac9a6-133">Poprawia czasy uruchamiania wielu aplikacji, które używają kopiowania w tle, zgodnie z opisem w [Kopiowanie zestawów w tle](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ac9a6-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="ac9a6-134">Aplikacje, które mają wysoki procent i częstotliwość aktualizacji zestawu nie mogą korzystać z tej zmiany w zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="ac9a6-135">W takim przypadku można użyć tego elementu, aby przywrócić zachowanie z poprzednich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac9a6-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac9a6-136">Example</span></span>  
 <span data-ttu-id="ac9a6-137">Poniższy przykład pokazuje, jak wyłączyć domyślne zachowanie uruchamiania w tle kopiowania w programie .NET Framework 4 i powrócić do zachowania uruchamiania poprzednich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac9a6-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac9a6-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac9a6-138">See also</span></span>

- [<span data-ttu-id="ac9a6-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ac9a6-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ac9a6-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ac9a6-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ac9a6-141">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="ac9a6-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
