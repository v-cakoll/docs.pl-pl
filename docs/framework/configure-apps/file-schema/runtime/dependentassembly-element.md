---
title: <dependentAssembly> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac83a0b27a965721dabe1bdf2e05afbdc9b9c961
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083663"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="f15d3-102">\<dependentAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="f15d3-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="f15d3-103">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f15d3-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="f15d3-104">Użyj jednej `dependentAssembly` elementu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f15d3-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="f15d3-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f15d3-105">\<configuration></span></span>  
<span data-ttu-id="f15d3-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="f15d3-106">\<runtime></span></span>  
<span data-ttu-id="f15d3-107">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="f15d3-107">\<assemblyBinding></span></span>  
<span data-ttu-id="f15d3-108">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="f15d3-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15d3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f15d3-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f15d3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f15d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f15d3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f15d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f15d3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f15d3-112">Attributes</span></span>  
 <span data-ttu-id="f15d3-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="f15d3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f15d3-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f15d3-114">Child Elements</span></span>  
  
|<span data-ttu-id="f15d3-115">Element</span><span class="sxs-lookup"><span data-stu-id="f15d3-115">Element</span></span>|<span data-ttu-id="f15d3-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f15d3-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="f15d3-117">Zawiera informacje identyfikujące zestaw.</span><span class="sxs-lookup"><span data-stu-id="f15d3-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="f15d3-118">Ten element musi być uwzględniony w każdym `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="f15d3-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="f15d3-119">Określa, gdzie środowisko uruchomieniowe można znaleźć zestaw współużytkowany, jeśli nie jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f15d3-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="f15d3-120">Przekierowuje jedną wersję zestawu do innej.</span><span class="sxs-lookup"><span data-stu-id="f15d3-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="f15d3-121">Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f15d3-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f15d3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f15d3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f15d3-123">Element</span><span class="sxs-lookup"><span data-stu-id="f15d3-123">Element</span></span>|<span data-ttu-id="f15d3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f15d3-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="f15d3-125">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="f15d3-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="f15d3-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f15d3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f15d3-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f15d3-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f15d3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f15d3-128">Example</span></span>  
 <span data-ttu-id="f15d3-129">Poniższy przykład pokazuje, jak do hermetyzacji informacji o zestawie dla dwóch zestawów.</span><span class="sxs-lookup"><span data-stu-id="f15d3-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f15d3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f15d3-130">See also</span></span>

- [<span data-ttu-id="f15d3-131">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f15d3-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f15d3-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f15d3-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f15d3-133">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="f15d3-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
