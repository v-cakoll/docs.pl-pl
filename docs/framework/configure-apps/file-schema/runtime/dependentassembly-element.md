---
title: "&lt;dependentAssembly&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a968d2d1abf6e77cddd9d0a0367822ee4f9723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependentassemblygt-element"></a><span data-ttu-id="5b709-102">&lt;dependentAssembly&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="5b709-102">&lt;dependentAssembly&gt; Element</span></span>
<span data-ttu-id="5b709-103">Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5b709-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="5b709-104">Użyj jednej `dependentAssembly` elementu dla każdego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5b709-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="5b709-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5b709-105">\<configuration></span></span>  
<span data-ttu-id="5b709-106">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="5b709-106">\<runtime></span></span>  
<span data-ttu-id="5b709-107">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="5b709-107">\<assemblyBinding></span></span>  
<span data-ttu-id="5b709-108">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="5b709-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b709-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b709-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b709-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5b709-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5b709-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b709-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b709-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5b709-112">Attributes</span></span>  
 <span data-ttu-id="5b709-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="5b709-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b709-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5b709-114">Child Elements</span></span>  
  
|<span data-ttu-id="5b709-115">Element</span><span class="sxs-lookup"><span data-stu-id="5b709-115">Element</span></span>|<span data-ttu-id="5b709-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5b709-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="5b709-117">Zawiera informacje identyfikujące zestaw.</span><span class="sxs-lookup"><span data-stu-id="5b709-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="5b709-118">Ten element musi być uwzględniony w każdym `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="5b709-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="5b709-119">Określa, gdzie środowiska uruchomieniowego można znaleźć zestaw udostępnionego, jeśli nie jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5b709-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="5b709-120">Przekierowuje jedną wersję zestawu do innej.</span><span class="sxs-lookup"><span data-stu-id="5b709-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="5b709-121">Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5b709-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b709-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5b709-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5b709-123">Element</span><span class="sxs-lookup"><span data-stu-id="5b709-123">Element</span></span>|<span data-ttu-id="5b709-124">Opis</span><span class="sxs-lookup"><span data-stu-id="5b709-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5b709-125">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="5b709-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5b709-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b709-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5b709-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5b709-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b709-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b709-128">Example</span></span>  
 <span data-ttu-id="5b709-129">Poniższy przykład pokazuje, jak w celu hermetyzacji informacji o zestawie dla dwóch zestawów.</span><span class="sxs-lookup"><span data-stu-id="5b709-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b709-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b709-130">See Also</span></span>  
 [<span data-ttu-id="5b709-131">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5b709-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5b709-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5b709-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5b709-133">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="5b709-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
