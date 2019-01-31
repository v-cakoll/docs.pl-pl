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
ms.openlocfilehash: e862c52235c3836c79506dc2e80a264ceceddab3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267832"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="a3559-102">\<qualifyassembly — > Element</span><span class="sxs-lookup"><span data-stu-id="a3559-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="a3559-103">Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy część nazwy jest używany.</span><span class="sxs-lookup"><span data-stu-id="a3559-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="a3559-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a3559-104">\<configuration></span></span>  
<span data-ttu-id="a3559-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a3559-105">\<runtime></span></span>  
<span data-ttu-id="a3559-106">\<assemblybinding — ></span><span class="sxs-lookup"><span data-stu-id="a3559-106">\<assemblyBinding></span></span>  
<span data-ttu-id="a3559-107">\<qualifyassembly — ></span><span class="sxs-lookup"><span data-stu-id="a3559-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3559-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3559-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3559-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a3559-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a3559-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a3559-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3559-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3559-111">Attributes</span></span>  
  
|<span data-ttu-id="a3559-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a3559-112">Attribute</span></span>|<span data-ttu-id="a3559-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a3559-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="a3559-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a3559-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3559-115">Określa nazwę częściowego zestawu, wyświetlaną w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a3559-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="a3559-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a3559-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3559-117">Określa pełną nazwę zestawu, która jest wyświetlana w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a3559-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3559-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a3559-118">Child Elements</span></span>  
 <span data-ttu-id="a3559-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a3559-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3559-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a3559-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a3559-121">Element</span><span class="sxs-lookup"><span data-stu-id="a3559-121">Element</span></span>|<span data-ttu-id="a3559-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a3559-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a3559-123">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="a3559-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a3559-124">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3559-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a3559-125">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a3559-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3559-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3559-126">Remarks</span></span>  
 <span data-ttu-id="a3559-127">Wywoływanie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody przy użyciu nazwy zestawów częściowego powoduje, że środowisko uruchomieniowe języka wspólnego do wyszukania zestawu tylko w katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3559-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="a3559-128">Użyj  **\<qualifyassembly — >** elementu w pliku konfiguracyjnym aplikacji do udostępniania informacji pełnego zestawu (nazwa, wersja, token klucza publicznego i kultury) i spowodować, że środowisko uruchomieniowe języka wspólnego do wyszukiwania dla zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a3559-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="a3559-129">**Imię i nazwisko** atrybutu musi zawierać cztery pola tożsamości zestawu: nazwa, wersja, token klucza publicznego i kultury.</span><span class="sxs-lookup"><span data-stu-id="a3559-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="a3559-130">**PartialName** atrybut częściowo musi odwoływać się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a3559-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="a3559-131">Należy określić co najmniej nazwę tekstu zestawu (najbardziej typowe wielkości liter), ale może również obejmować wersji, token klucza publicznego lub kultury (lub dowolnej kombinacji cztery, ale nie wszystkie cztery).</span><span class="sxs-lookup"><span data-stu-id="a3559-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="a3559-132">**PartialName** musi pasować do nazwy określonej w swojej rozmowy.</span><span class="sxs-lookup"><span data-stu-id="a3559-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="a3559-133">Na przykład nie można określić `"math"` jako **partialName** atrybutu w pliku konfiguracji i wywołania `Assembly.Load("math, Version=3.3.3.3")` w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a3559-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3559-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3559-134">Example</span></span>  
 <span data-ttu-id="a3559-135">Poniższy przykład wyłącza logicznie wywołanie `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="a3559-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3559-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3559-136">See also</span></span>
- [<span data-ttu-id="a3559-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a3559-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a3559-138">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a3559-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a3559-139">NIB: Częściowe odwołania do zestawów</span><span class="sxs-lookup"><span data-stu-id="a3559-139">NIB: Partial Assembly References</span></span>](https://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
