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
ms.openlocfilehash: 9402c9f28c123affb7b90fc189484bb1fd43db46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210272"
---
# <a name="probing-element"></a><span data-ttu-id="29ec1-102">\<probing> Element</span><span class="sxs-lookup"><span data-stu-id="29ec1-102">\<probing> Element</span></span>
<span data-ttu-id="29ec1-103">Określa podkatalogi podstawowej aplikacji dla środowiska uruchomieniowego języka wspólnego wyszukiwania podczas ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="29ec1-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
 <span data-ttu-id="29ec1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="29ec1-104">\<configuration></span></span>  
<span data-ttu-id="29ec1-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="29ec1-105">\<runtime></span></span>  
<span data-ttu-id="29ec1-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="29ec1-106">\<assemblyBinding></span></span>  
<span data-ttu-id="29ec1-107">\<sondowanie ></span><span class="sxs-lookup"><span data-stu-id="29ec1-107">\<probing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ec1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="29ec1-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29ec1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29ec1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="29ec1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="29ec1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29ec1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29ec1-111">Attributes</span></span>  
  
|<span data-ttu-id="29ec1-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="29ec1-112">Attribute</span></span>|<span data-ttu-id="29ec1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="29ec1-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="29ec1-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="29ec1-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="29ec1-115">Określa podkatalogi katalogu podstawowego aplikacji, który może zawierać zestawów.</span><span class="sxs-lookup"><span data-stu-id="29ec1-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="29ec1-116">Powinny one być poszczególnych podkatalogach średnikiem.</span><span class="sxs-lookup"><span data-stu-id="29ec1-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29ec1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29ec1-117">Child Elements</span></span>  
 <span data-ttu-id="29ec1-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="29ec1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29ec1-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29ec1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="29ec1-120">Element</span><span class="sxs-lookup"><span data-stu-id="29ec1-120">Element</span></span>|<span data-ttu-id="29ec1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="29ec1-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="29ec1-122">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="29ec1-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="29ec1-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29ec1-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="29ec1-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="29ec1-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29ec1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="29ec1-125">Example</span></span>  
 <span data-ttu-id="29ec1-126">Poniższy przykład pokazuje, jak określić podkatalogów podstawowej aplikacji, które środowisko wykonawcze powinno poszukać zestawów.</span><span class="sxs-lookup"><span data-stu-id="29ec1-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29ec1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29ec1-127">See also</span></span>

- [<span data-ttu-id="29ec1-128">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="29ec1-128">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="29ec1-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="29ec1-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="29ec1-130">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="29ec1-130">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [<span data-ttu-id="29ec1-131">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="29ec1-131">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
