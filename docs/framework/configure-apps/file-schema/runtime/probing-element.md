---
title: <probing>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b00a5349e22feb3cce404ff504edd798ff9e304
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663520"
---
# <a name="probing-element"></a><span data-ttu-id="4da6d-102">\<> elementu do sondowania</span><span class="sxs-lookup"><span data-stu-id="4da6d-102">\<probing> Element</span></span>
<span data-ttu-id="4da6d-103">Określa podkatalogi bazy aplikacji dla środowiska uruchomieniowego języka wspólnego do przeszukania podczas ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="4da6d-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="4da6d-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4da6d-104">\<configuration></span></span>  
<span data-ttu-id="4da6d-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="4da6d-105">\<runtime></span></span>  
<span data-ttu-id="4da6d-106">\<> zestawubinding</span><span class="sxs-lookup"><span data-stu-id="4da6d-106">\<assemblyBinding></span></span>  
<span data-ttu-id="4da6d-107">\<> sondowania</span><span class="sxs-lookup"><span data-stu-id="4da6d-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da6d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4da6d-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4da6d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4da6d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4da6d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4da6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4da6d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4da6d-111">Attributes</span></span>  
  
|<span data-ttu-id="4da6d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4da6d-112">Attribute</span></span>|<span data-ttu-id="4da6d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4da6d-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="4da6d-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4da6d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="4da6d-115">Określa podkatalogi katalogu podstawowego aplikacji, który może zawierać zestawy.</span><span class="sxs-lookup"><span data-stu-id="4da6d-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="4da6d-116">Rozdziel każdy podkatalog średnikami.</span><span class="sxs-lookup"><span data-stu-id="4da6d-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4da6d-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4da6d-117">Child Elements</span></span>  
 <span data-ttu-id="4da6d-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="4da6d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4da6d-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4da6d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4da6d-120">Element</span><span class="sxs-lookup"><span data-stu-id="4da6d-120">Element</span></span>|<span data-ttu-id="4da6d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4da6d-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="4da6d-122">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="4da6d-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="4da6d-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4da6d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4da6d-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4da6d-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4da6d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="4da6d-125">Example</span></span>  
 <span data-ttu-id="4da6d-126">Poniższy przykład pokazuje, jak określić podkatalogi bazy aplikacji środowisko uruchomieniowe powinno wyszukiwać zestawy.</span><span class="sxs-lookup"><span data-stu-id="4da6d-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4da6d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4da6d-127">See also</span></span>

- [<span data-ttu-id="4da6d-128">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="4da6d-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4da6d-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4da6d-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4da6d-130">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="4da6d-130">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="4da6d-131">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4da6d-131">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
