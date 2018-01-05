---
title: Element &lt;Library&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2663bbd5ca93341455b7bd036469d25d91f4a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltlibrarygt-element-net-native"></a><span data-ttu-id="47b99-102">Element &lt;Library&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="47b99-102">&lt;Library&gt; Element (.NET Native)</span></span>
<span data-ttu-id="47b99-103">Definiuje zestaw zawierający typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="47b99-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="47b99-104">\<Dyrektywy > — Element</span><span class="sxs-lookup"><span data-stu-id="47b99-104">\<Directives> Element</span></span>  
<span data-ttu-id="47b99-105">\<Biblioteka > — Element</span><span class="sxs-lookup"><span data-stu-id="47b99-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b99-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="47b99-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47b99-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47b99-107">Attributes and Elements</span></span>  
 <span data-ttu-id="47b99-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47b99-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47b99-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47b99-109">Attributes</span></span>  
  
|<span data-ttu-id="47b99-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47b99-110">Attribute</span></span>|<span data-ttu-id="47b99-111">Opis</span><span class="sxs-lookup"><span data-stu-id="47b99-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="47b99-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="47b99-112">Required attribute.</span></span> <span data-ttu-id="47b99-113">Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="47b99-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="47b99-114">Elementy podrzędne tego `<Library>` element zdefiniowania zasad środowiska uruchomieniowego odbicia dla typów i członków typu w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="47b99-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="47b99-115">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="47b99-115">Name attribute</span></span>  
  
|<span data-ttu-id="47b99-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="47b99-116">Value</span></span>|<span data-ttu-id="47b99-117">Opis</span><span class="sxs-lookup"><span data-stu-id="47b99-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47b99-118">*nazwa_zestawu*</span><span class="sxs-lookup"><span data-stu-id="47b99-118">*assembly_name*</span></span>|<span data-ttu-id="47b99-119">Prosta nazwa zestawu, bez jego rozszerzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="47b99-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="47b99-120">Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="47b99-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="47b99-121">Na przykład nazwa zestawu o nazwie Extensions.dll jest "Rozszerzenia".</span><span class="sxs-lookup"><span data-stu-id="47b99-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="47b99-122">Specjalna forma w sekcji uwag *nazwa_zestawu* obsługującej dołączenie warunkowe metadanych z zestawu.</span><span class="sxs-lookup"><span data-stu-id="47b99-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47b99-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47b99-123">Child Elements</span></span>  
  
|<span data-ttu-id="47b99-124">Element</span><span class="sxs-lookup"><span data-stu-id="47b99-124">Element</span></span>|<span data-ttu-id="47b99-125">Opis</span><span class="sxs-lookup"><span data-stu-id="47b99-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47b99-126">\<Zestaw ></span><span class="sxs-lookup"><span data-stu-id="47b99-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="47b99-127">Stosuje zasady do wszystkich typów w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="47b99-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="47b99-128">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="47b99-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="47b99-129">Stosuje zasady do wszystkich typów w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="47b99-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="47b99-130">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="47b99-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="47b99-131">Stosuje zasady do określonego typu, takich jak klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="47b99-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="47b99-132">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="47b99-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="47b99-133">Stosuje zasady do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="47b99-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="47b99-134">Na przykład [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element może służyć do zdefiniowania zasad dla `List<String>` typu.</span><span class="sxs-lookup"><span data-stu-id="47b99-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47b99-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47b99-135">Parent Elements</span></span>  
  
|<span data-ttu-id="47b99-136">Element</span><span class="sxs-lookup"><span data-stu-id="47b99-136">Element</span></span>|<span data-ttu-id="47b99-137">Opis</span><span class="sxs-lookup"><span data-stu-id="47b99-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47b99-138">\<Dyrektywy ></span><span class="sxs-lookup"><span data-stu-id="47b99-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="47b99-139">Element główny pliku dyrektyw środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="47b99-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47b99-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47b99-140">Remarks</span></span>  
 <span data-ttu-id="47b99-141">[ \<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) element może zawierać zero, co najmniej jeden `<Library>` elementów.</span><span class="sxs-lookup"><span data-stu-id="47b99-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="47b99-142">`<Library>` Elementu służy jako kontener do zdefiniowania elementów program, którego metadanych jest wymagane w czasie wykonywania; ten element nie wyrażenie zasad.</span><span class="sxs-lookup"><span data-stu-id="47b99-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="47b99-143">W czasie kompilacji narzędzia kompilatora wyszukiwania biblioteki wskazywany przez `<Library>` elementu dla elementów programu identyfikowane przez jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="47b99-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="47b99-144">Z kolei narzędzia kompilatora wyszukiwać wszystkie biblioteki, including.NET Framework core bibliotek, określone przez elementy podrzędne elementy programu [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="47b99-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="47b99-145">`<Library>`dyrektywy mogą zostać użyte warunkowo.</span><span class="sxs-lookup"><span data-stu-id="47b99-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="47b99-146">Jeśli nazwa `<Library>` elementu rozpoczyna się i kończy się gwiazdką (*), `<Library>` dyrektywy przynosi efekty tylko wtedy, gdy odwołuje się do zestawu określonego między gwiazdki przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="47b99-146">If the name of the `<Library>` element starts and ends with an asterisk (*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="47b99-147">Na przykład następujące dyrektyw środowiska uruchomieniowego ma zastosowanie tylko wtedy, gdy odwołuje się do zestawu Utillities.dll przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="47b99-147">For example, the following runtime directive applies only if the Utillities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47b99-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47b99-148">See Also</span></span>  
 [<span data-ttu-id="47b99-149">\<Aplikacja > — Element</span><span class="sxs-lookup"><span data-stu-id="47b99-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 [<span data-ttu-id="47b99-150">\<Dyrektywy > — Element</span><span class="sxs-lookup"><span data-stu-id="47b99-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 [<span data-ttu-id="47b99-151">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="47b99-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="47b99-152">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="47b99-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
