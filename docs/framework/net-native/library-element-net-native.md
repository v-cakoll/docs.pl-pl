---
title: <Library>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049651"
---
# <a name="library-element-net-native"></a><span data-ttu-id="b72ab-102">\<Biblioteka > element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b72ab-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="b72ab-103">Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b72ab-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="b72ab-104">\<Dyrektywy > element</span><span class="sxs-lookup"><span data-stu-id="b72ab-104">\<Directives> Element</span></span>  
<span data-ttu-id="b72ab-105">\<Biblioteka > element</span><span class="sxs-lookup"><span data-stu-id="b72ab-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72ab-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b72ab-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b72ab-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b72ab-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b72ab-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b72ab-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b72ab-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b72ab-109">Attributes</span></span>  
  
|<span data-ttu-id="b72ab-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b72ab-110">Attribute</span></span>|<span data-ttu-id="b72ab-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b72ab-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="b72ab-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b72ab-112">Required attribute.</span></span> <span data-ttu-id="b72ab-113">Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="b72ab-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="b72ab-114">Elementy podrzędne tego `<Library>` elementu definiują zasady odbicia środowiska uruchomieniowego dla typów i elementów członkowskich typu znalezionych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b72ab-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="b72ab-115">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="b72ab-115">Name attribute</span></span>  
  
|<span data-ttu-id="b72ab-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b72ab-116">Value</span></span>|<span data-ttu-id="b72ab-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b72ab-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b72ab-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="b72ab-118">*assembly_name*</span></span>|<span data-ttu-id="b72ab-119">Prosta nazwa zestawu bez rozszerzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="b72ab-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="b72ab-120">Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b72ab-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b72ab-121">Na przykład nazwa zestawu o nazwie Extensions. dll ma wartość "Extensions".</span><span class="sxs-lookup"><span data-stu-id="b72ab-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="b72ab-122">Zobacz sekcję Uwagi, aby uzyskać specjalną postać *assembly_name* , która obsługuje warunkowe dołączanie metadanych z zestawu.</span><span class="sxs-lookup"><span data-stu-id="b72ab-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b72ab-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b72ab-123">Child Elements</span></span>  
  
|<span data-ttu-id="b72ab-124">Element</span><span class="sxs-lookup"><span data-stu-id="b72ab-124">Element</span></span>|<span data-ttu-id="b72ab-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b72ab-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b72ab-126">\<> Zestawu</span><span class="sxs-lookup"><span data-stu-id="b72ab-126">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="b72ab-127">Stosuje zasady do wszystkich typów w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b72ab-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="b72ab-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="b72ab-128">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="b72ab-129">Stosuje zasady do wszystkich typów w konkretnym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b72ab-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="b72ab-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="b72ab-130">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="b72ab-131">Stosuje zasady do określonego typu, na przykład klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b72ab-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="b72ab-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="b72ab-132">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b72ab-133">Stosuje zasady do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b72ab-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="b72ab-134">Na przykład [ \<element TypeInstantiation >](typeinstantiation-element-net-native.md) może służyć do `List<String>` definiowania zasad dla typu.</span><span class="sxs-lookup"><span data-stu-id="b72ab-134">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b72ab-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b72ab-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b72ab-136">Element</span><span class="sxs-lookup"><span data-stu-id="b72ab-136">Element</span></span>|<span data-ttu-id="b72ab-137">Opis</span><span class="sxs-lookup"><span data-stu-id="b72ab-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b72ab-138">\<Dyrektywy ></span><span class="sxs-lookup"><span data-stu-id="b72ab-138">\<Directives></span></span>](directives-element-net-native.md)|<span data-ttu-id="b72ab-139">Element główny pliku dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b72ab-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b72ab-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b72ab-140">Remarks</span></span>  
 <span data-ttu-id="b72ab-141">Dyrektywy > element może zawierać zero, jeden lub więcej `<Library>` elementów. [ \<](directives-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="b72ab-141">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="b72ab-142">`<Library>` Element służy jako kontener do definiowania elementów programu, których metadane są konieczne w czasie wykonywania; ten element nie ma zasad ekspresowych.</span><span class="sxs-lookup"><span data-stu-id="b72ab-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="b72ab-143">W czasie kompilacji narzędzia kompilatora przeszukują tylko bibliotekę wyznaczony przez `<Library>` element dla elementów programu identyfikowanych przez jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="b72ab-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="b72ab-144">Z kolei narzędzia kompilatora przeszukują wszystkie biblioteki, including.NET Framework Core librarys dla elementów programu identyfikowanych przez elementy [ \<podrzędne aplikacji >](application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b72ab-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="b72ab-145">`<Library>`dyrektywy mogą być warunkowo wykorzystywane.</span><span class="sxs-lookup"><span data-stu-id="b72ab-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="b72ab-146">Jeśli nazwa `<Library>` elementu zaczyna się i kończy się gwiazdką (\*), `<Library>` dyrektywa ma wpływ tylko wtedy, gdy zestaw określony między gwiazdkami jest przywoływany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="b72ab-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="b72ab-147">Na przykład następująca dyrektywa środowiska uruchomieniowego ma zastosowanie tylko wtedy, gdy aplikacja jest przywoływana przez zestaw Utilities. dll.</span><span class="sxs-lookup"><span data-stu-id="b72ab-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b72ab-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b72ab-148">See also</span></span>

- [<span data-ttu-id="b72ab-149">\<Element > aplikacji</span><span class="sxs-lookup"><span data-stu-id="b72ab-149">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="b72ab-150">\<Dyrektywy > element</span><span class="sxs-lookup"><span data-stu-id="b72ab-150">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="b72ab-151">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b72ab-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b72ab-152">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b72ab-152">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
