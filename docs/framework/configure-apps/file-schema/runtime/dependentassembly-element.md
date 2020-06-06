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
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154208"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="16cfc-102">\<dependentAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="16cfc-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="16cfc-103">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="16cfc-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="16cfc-104">Użyj jednego `dependentAssembly` elementu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="16cfc-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="16cfc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16cfc-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16cfc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16cfc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="16cfc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="16cfc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16cfc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16cfc-108">Attributes</span></span>  
 <span data-ttu-id="16cfc-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="16cfc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="16cfc-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16cfc-110">Child Elements</span></span>  
  
|<span data-ttu-id="16cfc-111">Element</span><span class="sxs-lookup"><span data-stu-id="16cfc-111">Element</span></span>|<span data-ttu-id="16cfc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="16cfc-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="16cfc-113">Zawiera informacje identyfikacyjne zestawu.</span><span class="sxs-lookup"><span data-stu-id="16cfc-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="16cfc-114">Ten element musi być uwzględniony w każdym `dependentAssembly` elemencie.</span><span class="sxs-lookup"><span data-stu-id="16cfc-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="16cfc-115">Określa, gdzie środowisko uruchomieniowe może znaleźć zestaw współużytkowany, jeśli nie jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="16cfc-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="16cfc-116">Przekierowuje jedną wersję zestawu do innej.</span><span class="sxs-lookup"><span data-stu-id="16cfc-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="16cfc-117">Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="16cfc-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16cfc-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16cfc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="16cfc-119">Element</span><span class="sxs-lookup"><span data-stu-id="16cfc-119">Element</span></span>|<span data-ttu-id="16cfc-120">Opis</span><span class="sxs-lookup"><span data-stu-id="16cfc-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="16cfc-121">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="16cfc-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="16cfc-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16cfc-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16cfc-123">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="16cfc-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16cfc-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="16cfc-124">Example</span></span>  
 <span data-ttu-id="16cfc-125">Poniższy przykład pokazuje, jak hermetyzować informacje o zestawie dla dwóch zestawów.</span><span class="sxs-lookup"><span data-stu-id="16cfc-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16cfc-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16cfc-126">See also</span></span>

- [<span data-ttu-id="16cfc-127">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="16cfc-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16cfc-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="16cfc-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="16cfc-129">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="16cfc-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
