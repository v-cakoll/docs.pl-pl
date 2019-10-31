---
title: <developmentMode> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117632"
---
# <a name="developmentmode-element"></a><span data-ttu-id="6f46d-102">Element > \<developmentmode</span><span class="sxs-lookup"><span data-stu-id="6f46d-102">\<developmentMode> Element</span></span>
<span data-ttu-id="6f46d-103">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="6f46d-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="6f46d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6f46d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f46d-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f46d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6f46d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentmode >**</span><span class="sxs-lookup"><span data-stu-id="6f46d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f46d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f46d-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f46d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6f46d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6f46d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6f46d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f46d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6f46d-110">Attributes</span></span>  
  
|<span data-ttu-id="6f46d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6f46d-111">Attribute</span></span>|<span data-ttu-id="6f46d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6f46d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f46d-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="6f46d-113">**developerInstallation**</span></span>|<span data-ttu-id="6f46d-114">Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="6f46d-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="6f46d-115">developerInstallation — atrybut</span><span class="sxs-lookup"><span data-stu-id="6f46d-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="6f46d-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="6f46d-116">Value</span></span>|<span data-ttu-id="6f46d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6f46d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f46d-118">**true**</span><span class="sxs-lookup"><span data-stu-id="6f46d-118">**true**</span></span>|<span data-ttu-id="6f46d-119">Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="6f46d-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="6f46d-120">**false**</span><span class="sxs-lookup"><span data-stu-id="6f46d-120">**false**</span></span>|<span data-ttu-id="6f46d-121">Nie wyszukuje zestawów w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="6f46d-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="6f46d-122">Jest to wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6f46d-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f46d-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6f46d-123">Child Elements</span></span>  
 <span data-ttu-id="6f46d-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="6f46d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f46d-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6f46d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6f46d-126">Element</span><span class="sxs-lookup"><span data-stu-id="6f46d-126">Element</span></span>|<span data-ttu-id="6f46d-127">Opis</span><span class="sxs-lookup"><span data-stu-id="6f46d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6f46d-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f46d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6f46d-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6f46d-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f46d-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f46d-130">Remarks</span></span>  
 <span data-ttu-id="6f46d-131">Tego ustawienia należy używać tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="6f46d-131">Use this setting only at development time.</span></span> <span data-ttu-id="6f46d-132">Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="6f46d-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="6f46d-133">Po prostu używa pierwszego zestawu, który znajdzie.</span><span class="sxs-lookup"><span data-stu-id="6f46d-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f46d-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f46d-134">Example</span></span>  
 <span data-ttu-id="6f46d-135">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="6f46d-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f46d-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f46d-136">See also</span></span>

- [<span data-ttu-id="6f46d-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6f46d-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6f46d-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6f46d-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f46d-139">Instrukcje: lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="6f46d-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
