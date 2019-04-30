---
title: <developmentMode>, element
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
ms.openlocfilehash: fdf840035150f08c894c984213af9a0abe6e95af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704768"
---
# <a name="developmentmode-element"></a><span data-ttu-id="f3322-102">\<developmentMode> Element</span><span class="sxs-lookup"><span data-stu-id="f3322-102">\<developmentMode> Element</span></span>
<span data-ttu-id="f3322-103">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="f3322-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="f3322-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f3322-104">\<configuration></span></span>  
<span data-ttu-id="f3322-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="f3322-105">\<runtime></span></span>  
<span data-ttu-id="f3322-106">\<developmentMode></span><span class="sxs-lookup"><span data-stu-id="f3322-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3322-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3322-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3322-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3322-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3322-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3322-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3322-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3322-110">Attributes</span></span>  
  
|<span data-ttu-id="f3322-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f3322-111">Attribute</span></span>|<span data-ttu-id="f3322-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f3322-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3322-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="f3322-113">**developerInstallation**</span></span>|<span data-ttu-id="f3322-114">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="f3322-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="f3322-115">developerInstallation atrybutu</span><span class="sxs-lookup"><span data-stu-id="f3322-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="f3322-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="f3322-116">Value</span></span>|<span data-ttu-id="f3322-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f3322-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3322-118">**true**</span><span class="sxs-lookup"><span data-stu-id="f3322-118">**true**</span></span>|<span data-ttu-id="f3322-119">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="f3322-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="f3322-120">**false**</span><span class="sxs-lookup"><span data-stu-id="f3322-120">**false**</span></span>|<span data-ttu-id="f3322-121">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="f3322-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="f3322-122">Jest to opcja domyślna</span><span class="sxs-lookup"><span data-stu-id="f3322-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3322-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3322-123">Child Elements</span></span>  
 <span data-ttu-id="f3322-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="f3322-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3322-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3322-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f3322-126">Element</span><span class="sxs-lookup"><span data-stu-id="f3322-126">Element</span></span>|<span data-ttu-id="f3322-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f3322-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f3322-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3322-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f3322-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f3322-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3322-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3322-130">Remarks</span></span>  
 <span data-ttu-id="f3322-131">Użyj tego ustawienia w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f3322-131">Use this setting only at development time.</span></span> <span data-ttu-id="f3322-132">Środowisko wykonawcze nie sprawdza obecności wersje zestawów o silnych nazwach, znaleziono w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="f3322-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="f3322-133">Po prostu używa pierwszego zestawu, który odnajdzie.</span><span class="sxs-lookup"><span data-stu-id="f3322-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3322-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3322-134">Example</span></span>  
 <span data-ttu-id="f3322-135">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe do przeszukania pod kątem zestawów w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="f3322-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3322-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3322-136">See also</span></span>

- [<span data-ttu-id="f3322-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f3322-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f3322-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f3322-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f3322-139">Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="f3322-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
