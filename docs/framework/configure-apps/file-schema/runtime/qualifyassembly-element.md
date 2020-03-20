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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153922"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="019e1-102">\<qualifyAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="019e1-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="019e1-103">Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy używana jest nazwa częściowa.</span><span class="sxs-lookup"><span data-stu-id="019e1-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="019e1-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="019e1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="019e1-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="019e1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="019e1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>montażowy**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="019e1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="019e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<kwalifikacje>**</span><span class="sxs-lookup"><span data-stu-id="019e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019e1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="019e1-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="019e1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="019e1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="019e1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="019e1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="019e1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="019e1-111">Attributes</span></span>  
  
|<span data-ttu-id="019e1-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="019e1-112">Attribute</span></span>|<span data-ttu-id="019e1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="019e1-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="019e1-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="019e1-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="019e1-115">Określa częściową nazwę zestawu, jak pojawia się w kodzie.</span><span class="sxs-lookup"><span data-stu-id="019e1-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="019e1-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="019e1-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="019e1-117">Określa pełną nazwę zestawu, jak pojawia się w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="019e1-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="019e1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="019e1-118">Child Elements</span></span>  
 <span data-ttu-id="019e1-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="019e1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="019e1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="019e1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="019e1-121">Element</span><span class="sxs-lookup"><span data-stu-id="019e1-121">Element</span></span>|<span data-ttu-id="019e1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="019e1-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="019e1-123">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="019e1-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="019e1-124">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="019e1-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="019e1-125">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="019e1-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="019e1-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="019e1-126">Remarks</span></span>  
 <span data-ttu-id="019e1-127">Wywołanie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody przy użyciu nazw zestawu częściowego powoduje, że środowisko uruchomieniowe języka wspólnego wyszukać zestaw tylko w katalogu podstawowym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="019e1-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="019e1-128">Użyj \*\* \<elementu qualifyAssembly>\*\* w pliku konfiguracji aplikacji, aby podać pełne informacje o zestawie (nazwa, wersja, token klucza publicznego i kultury) i spowodować, że środowisko uruchomieniowe języka wspólnego do wyszukiwania zestawu w globalnej pamięci podręcznej zestawu.</span><span class="sxs-lookup"><span data-stu-id="019e1-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="019e1-129">Atrybut **fullName** musi zawierać cztery pola tożsamości zestawu: nazwa, wersja, token klucza publicznego i kultury.</span><span class="sxs-lookup"><span data-stu-id="019e1-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="019e1-130">Atrybut **partialName** musi częściowo odwoływać się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="019e1-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="019e1-131">Należy określić co najmniej nazwę tekstową zestawu (najczęstszym przypadkiem), ale można również dołączyć wersję, token klucza publicznego lub kultury (lub dowolną kombinację czterech, ale nie wszystkie cztery).</span><span class="sxs-lookup"><span data-stu-id="019e1-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="019e1-132">**PartialName** musi odpowiadać nazwie określonej w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="019e1-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="019e1-133">Na przykład nie `"math"` można określić jako atrybut **partialName** `Assembly.Load("math, Version=3.3.3.3")` w pliku konfiguracji i wywołać w kodzie.</span><span class="sxs-lookup"><span data-stu-id="019e1-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="019e1-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="019e1-134">Example</span></span>  
 <span data-ttu-id="019e1-135">Poniższy przykład logicznie `Assembly.Load("math")` zamienia `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`wywołanie w .</span><span class="sxs-lookup"><span data-stu-id="019e1-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="019e1-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="019e1-136">See also</span></span>

- [<span data-ttu-id="019e1-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="019e1-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="019e1-138">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="019e1-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="019e1-139">[Odwołania do złożenia częściowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="019e1-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
