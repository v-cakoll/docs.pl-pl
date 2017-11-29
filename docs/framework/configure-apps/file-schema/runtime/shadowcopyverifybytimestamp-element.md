---
title: "&lt;shadowCopyVerifyByTimestamp&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 261962819e9b2b37682a13bffb53d2912a660566
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="37ac6-102">&lt;shadowCopyVerifyByTimestamp&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="37ac6-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="37ac6-103">Określa, czy kopiowanie w tle używa domyślne zachowanie uruchamiania wprowadzone w systemie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], lub wraca do zachowania uruchamiania wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37ac6-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="37ac6-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="37ac6-104">\<configuration> Element</span></span>  
<span data-ttu-id="37ac6-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="37ac6-105">\<runtime> Element</span></span>  
<span data-ttu-id="37ac6-106">\<shadowCopyVerifyByTimestamp > — Element</span><span class="sxs-lookup"><span data-stu-id="37ac6-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ac6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="37ac6-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37ac6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37ac6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37ac6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37ac6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ac6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37ac6-110">Attributes</span></span>  
  
|<span data-ttu-id="37ac6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37ac6-111">Attribute</span></span>|<span data-ttu-id="37ac6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="37ac6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37ac6-113">włączone</span><span class="sxs-lookup"><span data-stu-id="37ac6-113">enabled</span></span>|<span data-ttu-id="37ac6-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="37ac6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="37ac6-115">Określa, czy domeny aplikacji, które używają kopiowanie w tle porównania sygnatury czasowe zestawów podczas uruchamiania, aby określić, czy zestaw został zaktualizowany przed Kopiowanie zestawów w tle.</span><span class="sxs-lookup"><span data-stu-id="37ac6-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="37ac6-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="37ac6-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="37ac6-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="37ac6-117">Value</span></span>|<span data-ttu-id="37ac6-118">Opis</span><span class="sxs-lookup"><span data-stu-id="37ac6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37ac6-119">true</span><span class="sxs-lookup"><span data-stu-id="37ac6-119">true</span></span>|<span data-ttu-id="37ac6-120">Podczas uruchamiania kopiuje tylko zestawy, które zostały zaktualizowane od czasu ostatniego zostały one kopiowane do katalogu kopii w tle.</span><span class="sxs-lookup"><span data-stu-id="37ac6-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="37ac6-121">Jest to wartość domyślna dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37ac6-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="37ac6-122">false</span><span class="sxs-lookup"><span data-stu-id="37ac6-122">false</span></span>|<span data-ttu-id="37ac6-123">Przywraca zachowanie uruchamiania poprzednich wersji programu .NET Framework, na który został do skopiowania wszystkich plików podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="37ac6-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37ac6-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37ac6-124">Child Elements</span></span>  
 <span data-ttu-id="37ac6-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="37ac6-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37ac6-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37ac6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="37ac6-127">Element</span><span class="sxs-lookup"><span data-stu-id="37ac6-127">Element</span></span>|<span data-ttu-id="37ac6-128">Opis</span><span class="sxs-lookup"><span data-stu-id="37ac6-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="37ac6-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37ac6-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="37ac6-130">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="37ac6-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ac6-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37ac6-131">Remarks</span></span>  
 <span data-ttu-id="37ac6-132">Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], zestawy są kopie tylko wtedy, gdy ich sygnatury czasowe wskazują, że zostały zmienione od czasu ostatniego zostały one kopiowane do katalogu kopii w tle w tle.</span><span class="sxs-lookup"><span data-stu-id="37ac6-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="37ac6-133">Zwiększa to czasy uruchamiania dla wielu aplikacji, które używają kopiowanie w tle, zgodnie z opisem w [Kopiowanie zestawów w tle](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="37ac6-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="37ac6-134">Aplikacje, które mają wysoki procent i częstotliwość aktualizacji zestawu nie mogą korzystać z tej zmiany w zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="37ac6-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="37ac6-135">W takim przypadku służy tego elementu. Aby przywrócić zachowanie z poprzednich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37ac6-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37ac6-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="37ac6-136">Example</span></span>  
 <span data-ttu-id="37ac6-137">Poniższy przykład pokazuje, jak można wyłączyć domyślnego zachowania uruchamiania kopiowanie w tle w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i przywrócenie zachowania uruchamiania poprzednich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37ac6-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37ac6-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37ac6-138">See Also</span></span>  
 [<span data-ttu-id="37ac6-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="37ac6-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="37ac6-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="37ac6-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="37ac6-141">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="37ac6-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
