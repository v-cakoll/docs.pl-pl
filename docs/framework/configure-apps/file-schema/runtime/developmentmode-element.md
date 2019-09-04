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
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252695"
---
# <a name="developmentmode-element"></a><span data-ttu-id="172b6-102">\<Element > developmentmode</span><span class="sxs-lookup"><span data-stu-id="172b6-102">\<developmentMode> Element</span></span>
<span data-ttu-id="172b6-103">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="172b6-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="172b6-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="172b6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="172b6-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="172b6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="172b6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> developmentmode**</span><span class="sxs-lookup"><span data-stu-id="172b6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="172b6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="172b6-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="172b6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="172b6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="172b6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="172b6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="172b6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="172b6-110">Attributes</span></span>  
  
|<span data-ttu-id="172b6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="172b6-111">Attribute</span></span>|<span data-ttu-id="172b6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="172b6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="172b6-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="172b6-113">**developerInstallation**</span></span>|<span data-ttu-id="172b6-114">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="172b6-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="172b6-115">developerInstallation — atrybut</span><span class="sxs-lookup"><span data-stu-id="172b6-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="172b6-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="172b6-116">Value</span></span>|<span data-ttu-id="172b6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="172b6-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="172b6-118">**true**</span><span class="sxs-lookup"><span data-stu-id="172b6-118">**true**</span></span>|<span data-ttu-id="172b6-119">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="172b6-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="172b6-120">**false**</span><span class="sxs-lookup"><span data-stu-id="172b6-120">**false**</span></span>|<span data-ttu-id="172b6-121">Nie wyszukuje zestawów w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="172b6-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="172b6-122">Jest to wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="172b6-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="172b6-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="172b6-123">Child Elements</span></span>  
 <span data-ttu-id="172b6-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="172b6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="172b6-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="172b6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="172b6-126">Element</span><span class="sxs-lookup"><span data-stu-id="172b6-126">Element</span></span>|<span data-ttu-id="172b6-127">Opis</span><span class="sxs-lookup"><span data-stu-id="172b6-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="172b6-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="172b6-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="172b6-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="172b6-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="172b6-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="172b6-130">Remarks</span></span>  
 <span data-ttu-id="172b6-131">Tego ustawienia należy używać tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="172b6-131">Use this setting only at development time.</span></span> <span data-ttu-id="172b6-132">Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="172b6-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="172b6-133">Po prostu używa pierwszego zestawu, który znajdzie.</span><span class="sxs-lookup"><span data-stu-id="172b6-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="172b6-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="172b6-134">Example</span></span>  
 <span data-ttu-id="172b6-135">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="172b6-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="172b6-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="172b6-136">See also</span></span>

- [<span data-ttu-id="172b6-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="172b6-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="172b6-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="172b6-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="172b6-139">Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="172b6-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
