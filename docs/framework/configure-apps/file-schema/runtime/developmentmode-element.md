---
title: "&lt;developmentmode —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4573c3a5e0cf64996f2a4e109736d966b754494a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="1ad74-102">&lt;developmentmode —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1ad74-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="1ad74-103">Określa, czy środowisko uruchomieniowe wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1ad74-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="1ad74-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1ad74-104">\<configuration></span></span>  
<span data-ttu-id="1ad74-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="1ad74-105">\<runtime></span></span>  
<span data-ttu-id="1ad74-106">\<developmentmode — ></span><span class="sxs-lookup"><span data-stu-id="1ad74-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad74-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ad74-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ad74-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1ad74-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1ad74-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1ad74-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ad74-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1ad74-110">Attributes</span></span>  
  
|<span data-ttu-id="1ad74-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1ad74-111">Attribute</span></span>|<span data-ttu-id="1ad74-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad74-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ad74-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="1ad74-113">**developerInstallation**</span></span>|<span data-ttu-id="1ad74-114">Określa, czy środowisko uruchomieniowe wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1ad74-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="1ad74-115">developerInstallation atrybutu</span><span class="sxs-lookup"><span data-stu-id="1ad74-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="1ad74-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="1ad74-116">Value</span></span>|<span data-ttu-id="1ad74-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad74-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ad74-118">**wartość true**</span><span class="sxs-lookup"><span data-stu-id="1ad74-118">**true**</span></span>|<span data-ttu-id="1ad74-119">Wyszukiwanie zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1ad74-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="1ad74-120">**wartość false**</span><span class="sxs-lookup"><span data-stu-id="1ad74-120">**false**</span></span>|<span data-ttu-id="1ad74-121">Nie wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1ad74-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="1ad74-122">Jest to wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="1ad74-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ad74-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1ad74-123">Child Elements</span></span>  
 <span data-ttu-id="1ad74-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="1ad74-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ad74-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1ad74-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1ad74-126">Element</span><span class="sxs-lookup"><span data-stu-id="1ad74-126">Element</span></span>|<span data-ttu-id="1ad74-127">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad74-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1ad74-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ad74-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1ad74-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1ad74-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ad74-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ad74-130">Remarks</span></span>  
 <span data-ttu-id="1ad74-131">Tego ustawienia należy używać tylko w czasie opracowywania.</span><span class="sxs-lookup"><span data-stu-id="1ad74-131">Use this setting only at development time.</span></span> <span data-ttu-id="1ad74-132">Środowisko uruchomieniowe nie sprawdza wersje zestawów o silnych nazwach w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1ad74-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="1ad74-133">Po prostu używa pierwszego zestawu znalezione.</span><span class="sxs-lookup"><span data-stu-id="1ad74-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ad74-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ad74-134">Example</span></span>  
 <span data-ttu-id="1ad74-135">Poniższy przykład pokazuje, jak spowodować środowiska uruchomieniowego do wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1ad74-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ad74-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ad74-136">See Also</span></span>  
 [<span data-ttu-id="1ad74-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1ad74-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1ad74-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1ad74-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1ad74-139">Porady: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="1ad74-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
