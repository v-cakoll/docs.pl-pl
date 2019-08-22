---
title: <qualifyAssembly>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4aa90a378630c9aff74923d8e8600aed15a77a5e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663500"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="808b5-102">\<qualifyAssembly, element ></span><span class="sxs-lookup"><span data-stu-id="808b5-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="808b5-103">Określa pełną nazwę zestawu, który ma być dynamicznie ładowany, gdy zostanie użyta nazwa częściowa.</span><span class="sxs-lookup"><span data-stu-id="808b5-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="808b5-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="808b5-104">\<configuration></span></span>  
<span data-ttu-id="808b5-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="808b5-105">\<runtime></span></span>  
<span data-ttu-id="808b5-106">\<> zestawubinding</span><span class="sxs-lookup"><span data-stu-id="808b5-106">\<assemblyBinding></span></span>  
<span data-ttu-id="808b5-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="808b5-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="808b5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="808b5-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="808b5-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="808b5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="808b5-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="808b5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="808b5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="808b5-111">Attributes</span></span>  
  
|<span data-ttu-id="808b5-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="808b5-112">Attribute</span></span>|<span data-ttu-id="808b5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="808b5-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="808b5-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="808b5-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="808b5-115">Określa częściową nazwę zestawu, która pojawia się w kodzie.</span><span class="sxs-lookup"><span data-stu-id="808b5-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="808b5-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="808b5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="808b5-117">Określa pełną nazwę zestawu, która pojawia się w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="808b5-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="808b5-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="808b5-118">Child Elements</span></span>  
 <span data-ttu-id="808b5-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="808b5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="808b5-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="808b5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="808b5-121">Element</span><span class="sxs-lookup"><span data-stu-id="808b5-121">Element</span></span>|<span data-ttu-id="808b5-122">Opis</span><span class="sxs-lookup"><span data-stu-id="808b5-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="808b5-123">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="808b5-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="808b5-124">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="808b5-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="808b5-125">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="808b5-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="808b5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="808b5-126">Remarks</span></span>  
 <span data-ttu-id="808b5-127"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Wywołanie metody przy użyciu częściowych nazw zestawów powoduje, że środowisko uruchomieniowe języka wspólnego szuka zestawu tylko w katalogu podstawowym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="808b5-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="808b5-128">Użyj elementu qualifyAssembly > w pliku konfiguracji aplikacji, aby podać pełne informacje o zestawie (nazwę, wersję, token klucza publicznego i kulturę) i spowodować, że środowisko uruchomieniowe języka wspólnego wyszukuje zestaw w  **\<** globalna pamięć podręczna zestawów.</span><span class="sxs-lookup"><span data-stu-id="808b5-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="808b5-129">Atrybut **FullName** musi zawierać cztery pola tożsamości zestawu: nazwę, wersję, token klucza publicznego i kulturę.</span><span class="sxs-lookup"><span data-stu-id="808b5-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="808b5-130">Atrybut **częściname** musi częściowo odwoływać się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="808b5-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="808b5-131">Należy określić co najmniej nazwę tekstu zestawu (najbardziej typowe), ale można również dołączyć wersję, token klucza publicznego lub kulturę (lub dowolną kombinację czterech, ale nie wszystkie cztery).</span><span class="sxs-lookup"><span data-stu-id="808b5-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="808b5-132">**Część częściowa** musi być zgodna z nazwą określoną w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="808b5-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="808b5-133">Na przykład nie można określić `"math"` jako atrybutu **częściname** w pliku konfiguracji i wywołać `Assembly.Load("math, Version=3.3.3.3")` w kodzie.</span><span class="sxs-lookup"><span data-stu-id="808b5-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="808b5-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="808b5-134">Example</span></span>  
 <span data-ttu-id="808b5-135">Poniższy przykład logicznie włącza wywołania `Assembly.Load("math")` do. `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`</span><span class="sxs-lookup"><span data-stu-id="808b5-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="808b5-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="808b5-136">See also</span></span>

- [<span data-ttu-id="808b5-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="808b5-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="808b5-138">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="808b5-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="808b5-139">[Odwołania do zestawów częściowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="808b5-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
