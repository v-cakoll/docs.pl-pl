---
title: '&lt;developmentmode —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 982bc04e362f82760226b1cd2b8b3febe9cc7107
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612052"
---
# <a name="ltdevelopmentmodegt-element"></a><span data-ttu-id="0104a-102">&lt;developmentmode —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="0104a-102">&lt;developmentMode&gt; Element</span></span>
<span data-ttu-id="0104a-103">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0104a-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="0104a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0104a-104">\<configuration></span></span>  
<span data-ttu-id="0104a-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="0104a-105">\<runtime></span></span>  
<span data-ttu-id="0104a-106">\<developmentmode — ></span><span class="sxs-lookup"><span data-stu-id="0104a-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0104a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0104a-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0104a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0104a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0104a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0104a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0104a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0104a-110">Attributes</span></span>  
  
|<span data-ttu-id="0104a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0104a-111">Attribute</span></span>|<span data-ttu-id="0104a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0104a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0104a-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="0104a-113">**developerInstallation**</span></span>|<span data-ttu-id="0104a-114">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0104a-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="0104a-115">developerInstallation atrybutu</span><span class="sxs-lookup"><span data-stu-id="0104a-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="0104a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="0104a-116">Value</span></span>|<span data-ttu-id="0104a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0104a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0104a-118">**true**</span><span class="sxs-lookup"><span data-stu-id="0104a-118">**true**</span></span>|<span data-ttu-id="0104a-119">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0104a-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="0104a-120">**false**</span><span class="sxs-lookup"><span data-stu-id="0104a-120">**false**</span></span>|<span data-ttu-id="0104a-121">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0104a-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="0104a-122">Jest to opcja domyślna</span><span class="sxs-lookup"><span data-stu-id="0104a-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0104a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0104a-123">Child Elements</span></span>  
 <span data-ttu-id="0104a-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="0104a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0104a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0104a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0104a-126">Element</span><span class="sxs-lookup"><span data-stu-id="0104a-126">Element</span></span>|<span data-ttu-id="0104a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="0104a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0104a-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0104a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0104a-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0104a-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0104a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0104a-130">Remarks</span></span>  
 <span data-ttu-id="0104a-131">Użyj tego ustawienia w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="0104a-131">Use this setting only at development time.</span></span> <span data-ttu-id="0104a-132">Środowisko wykonawcze nie sprawdza obecności wersje zestawów o silnych nazwach, znaleziono w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0104a-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="0104a-133">Po prostu używa pierwszego zestawu, który odnajdzie.</span><span class="sxs-lookup"><span data-stu-id="0104a-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0104a-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="0104a-134">Example</span></span>  
 <span data-ttu-id="0104a-135">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe do przeszukania pod kątem zestawów w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0104a-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0104a-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0104a-136">See Also</span></span>  
- [<span data-ttu-id="0104a-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0104a-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="0104a-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0104a-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="0104a-139">Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="0104a-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
