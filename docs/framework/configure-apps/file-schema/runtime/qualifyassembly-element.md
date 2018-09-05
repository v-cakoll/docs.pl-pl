---
title: '&lt;qualifyassembly —&gt; — Element'
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
ms.openlocfilehash: 59e3f54f4d3ce0c191193ff63a3c2bce5b93a1bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538034"
---
# <a name="ltqualifyassemblygt-element"></a><span data-ttu-id="c8c5c-102">&lt;qualifyassembly —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="c8c5c-102">&lt;qualifyAssembly&gt; Element</span></span>
<span data-ttu-id="c8c5c-103">Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy część nazwy jest używany.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="c8c5c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c8c5c-104">\<configuration></span></span>  
<span data-ttu-id="c8c5c-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="c8c5c-105">\<runtime></span></span>  
<span data-ttu-id="c8c5c-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="c8c5c-106">\<assemblyBinding></span></span>  
<span data-ttu-id="c8c5c-107">\<qualifyassembly — ></span><span class="sxs-lookup"><span data-stu-id="c8c5c-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c5c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8c5c-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8c5c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8c5c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c8c5c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8c5c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8c5c-111">Attributes</span></span>  
  
|<span data-ttu-id="c8c5c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c8c5c-112">Attribute</span></span>|<span data-ttu-id="c8c5c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c8c5c-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="c8c5c-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c8c5c-115">Określa nazwę częściowego zestawu, wyświetlaną w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="c8c5c-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c8c5c-117">Określa pełną nazwę zestawu, która jest wyświetlana w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8c5c-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8c5c-118">Child Elements</span></span>  
 <span data-ttu-id="c8c5c-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8c5c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8c5c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c8c5c-121">Element</span><span class="sxs-lookup"><span data-stu-id="c8c5c-121">Element</span></span>|<span data-ttu-id="c8c5c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c8c5c-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="c8c5c-123">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="c8c5c-124">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c8c5c-125">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8c5c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8c5c-126">Remarks</span></span>  
 <span data-ttu-id="c8c5c-127">Wywoływanie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody przy użyciu nazwy zestawów częściowego powoduje, że środowisko uruchomieniowe języka wspólnego do wyszukania zestawu tylko w katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="c8c5c-128">Użyj  **\<qualifyassembly — >** elementu w pliku konfiguracyjnym aplikacji do udostępniania informacji pełnego zestawu (nazwa, wersja, token klucza publicznego i kultury) i spowodować, że środowisko uruchomieniowe języka wspólnego do wyszukiwania dla zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="c8c5c-129">**Imię i nazwisko** atrybutu musi zawierać cztery pola tożsamości zestawu: nazwa, wersja, token klucza publicznego i kultury.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="c8c5c-130">**PartialName** atrybut częściowo musi odwoływać się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="c8c5c-131">Należy określić co najmniej nazwę tekstu zestawu (najbardziej typowe wielkości liter), ale może również obejmować wersji, token klucza publicznego lub kultury (lub dowolnej kombinacji cztery, ale nie wszystkie cztery).</span><span class="sxs-lookup"><span data-stu-id="c8c5c-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="c8c5c-132">**PartialName** musi pasować do nazwy określonej w swojej rozmowy.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="c8c5c-133">Na przykład nie można określić `"math"` jako **partialName** atrybutu w pliku konfiguracji i wywołania `Assembly.Load("math, Version=3.3.3.3")` w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c5c-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8c5c-134">Example</span></span>  
 <span data-ttu-id="c8c5c-135">Poniższy przykład wyłącza logicznie wywołanie `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="c8c5c-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8c5c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8c5c-136">See Also</span></span>  
 [<span data-ttu-id="c8c5c-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c8c5c-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c8c5c-138">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c8c5c-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="c8c5c-139">NIB: Częściowe odwołania do zestawów</span><span class="sxs-lookup"><span data-stu-id="c8c5c-139">NIB: Partial Assembly References</span></span>](https://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
