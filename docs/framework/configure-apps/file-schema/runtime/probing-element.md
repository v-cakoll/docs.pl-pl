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
ms.openlocfilehash: ae789e99a1306102c67f2252760e215989132406
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971631"
---
# <a name="probing-element"></a><span data-ttu-id="fb69f-102">\<> elementu do sondowania</span><span class="sxs-lookup"><span data-stu-id="fb69f-102">\<probing> Element</span></span>
<span data-ttu-id="fb69f-103">Określa podkatalogi bazy aplikacji dla środowiska uruchomieniowego języka wspólnego do przeszukania podczas ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="fb69f-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="fb69f-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb69f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fb69f-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb69f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="fb69f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="fb69f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="fb69f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> sondowania**</span><span class="sxs-lookup"><span data-stu-id="fb69f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb69f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb69f-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb69f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb69f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fb69f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb69f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb69f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb69f-111">Attributes</span></span>  
  
|<span data-ttu-id="fb69f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb69f-112">Attribute</span></span>|<span data-ttu-id="fb69f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fb69f-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="fb69f-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb69f-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="fb69f-115">Określa podkatalogi katalogu podstawowego aplikacji, który może zawierać zestawy.</span><span class="sxs-lookup"><span data-stu-id="fb69f-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="fb69f-116">Rozdziel każdy podkatalog średnikami.</span><span class="sxs-lookup"><span data-stu-id="fb69f-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb69f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb69f-117">Child Elements</span></span>  

<span data-ttu-id="fb69f-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb69f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb69f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb69f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fb69f-120">Element</span><span class="sxs-lookup"><span data-stu-id="fb69f-120">Element</span></span>|<span data-ttu-id="fb69f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fb69f-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="fb69f-122">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="fb69f-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="fb69f-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb69f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fb69f-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fb69f-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fb69f-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb69f-125">Example</span></span>  
 <span data-ttu-id="fb69f-126">Poniższy przykład pokazuje, jak określić podkatalogi bazy aplikacji środowisko uruchomieniowe powinno wyszukiwać zestawy.</span><span class="sxs-lookup"><span data-stu-id="fb69f-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb69f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb69f-127">See also</span></span>

- [<span data-ttu-id="fb69f-128">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fb69f-128">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="fb69f-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fb69f-129">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="fb69f-130">Określ lokalizację zestawu</span><span class="sxs-lookup"><span data-stu-id="fb69f-130">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="fb69f-131">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="fb69f-131">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
