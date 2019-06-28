---
title: <Library> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce001ed25d7704301d7f809887a445e3492e93fc
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422533"
---
# <a name="library-element-net-native"></a><span data-ttu-id="eee0a-102">\<Biblioteka > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="eee0a-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="eee0a-103">Definiuje zestaw, który zawiera typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="eee0a-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="eee0a-104">\<Dyrektywy > Element</span><span class="sxs-lookup"><span data-stu-id="eee0a-104">\<Directives> Element</span></span>  
<span data-ttu-id="eee0a-105">\<Biblioteka > Element</span><span class="sxs-lookup"><span data-stu-id="eee0a-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee0a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eee0a-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eee0a-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eee0a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="eee0a-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eee0a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eee0a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eee0a-109">Attributes</span></span>  
  
|<span data-ttu-id="eee0a-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eee0a-110">Attribute</span></span>|<span data-ttu-id="eee0a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="eee0a-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="eee0a-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="eee0a-112">Required attribute.</span></span> <span data-ttu-id="eee0a-113">Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="eee0a-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="eee0a-114">Elementy podrzędne tego `<Library>` element zdefiniowania zasad odbicia środowiska uruchomieniowego dla typów i składowych typu, w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="eee0a-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="eee0a-115">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="eee0a-115">Name attribute</span></span>  
  
|<span data-ttu-id="eee0a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="eee0a-116">Value</span></span>|<span data-ttu-id="eee0a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="eee0a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eee0a-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="eee0a-118">*assembly_name*</span></span>|<span data-ttu-id="eee0a-119">Prosta nazwa zestawu, bez jego rozszerzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="eee0a-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="eee0a-120">Ten atrybut odnosi się do <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eee0a-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="eee0a-121">Na przykład nazwę zestawu o nazwie Extensions.dll jest "Rozszerzenia".</span><span class="sxs-lookup"><span data-stu-id="eee0a-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="eee0a-122">Zobacz sekcję Spostrzeżenia, aby specjalną postać *assembly_name* , która obsługuje dołączenie warunkowe metadanych z zestawu.</span><span class="sxs-lookup"><span data-stu-id="eee0a-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eee0a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eee0a-123">Child Elements</span></span>  
  
|<span data-ttu-id="eee0a-124">Element</span><span class="sxs-lookup"><span data-stu-id="eee0a-124">Element</span></span>|<span data-ttu-id="eee0a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="eee0a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee0a-126">\<Zestaw ></span><span class="sxs-lookup"><span data-stu-id="eee0a-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="eee0a-127">Stosuje zasady do wszystkich typów w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="eee0a-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="eee0a-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="eee0a-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="eee0a-129">Stosuje zasady do wszystkich typów w określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eee0a-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="eee0a-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="eee0a-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="eee0a-131">Stosuje zasady do określonego typu, takie jak klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="eee0a-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="eee0a-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="eee0a-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="eee0a-133">Stosuje zasady do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="eee0a-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="eee0a-134">Na przykład [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element może służyć do definiowania zasad dla `List<String>` typu.</span><span class="sxs-lookup"><span data-stu-id="eee0a-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eee0a-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eee0a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="eee0a-136">Element</span><span class="sxs-lookup"><span data-stu-id="eee0a-136">Element</span></span>|<span data-ttu-id="eee0a-137">Opis</span><span class="sxs-lookup"><span data-stu-id="eee0a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee0a-138">\<Dyrektywy ></span><span class="sxs-lookup"><span data-stu-id="eee0a-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="eee0a-139">Element główny plik dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="eee0a-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eee0a-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eee0a-140">Remarks</span></span>  
 <span data-ttu-id="eee0a-141">[ \<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) element może zawierać zero, co najmniej jeden `<Library>` elementów.</span><span class="sxs-lookup"><span data-stu-id="eee0a-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="eee0a-142">`<Library>` Element służy jako kontener służący do definiowania elementów programu, w których metadanych jest potrzebnych w czasie wykonywania; ten element nie express zasad.</span><span class="sxs-lookup"><span data-stu-id="eee0a-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="eee0a-143">W czasie kompilacji narzędzia kompilatora wyszukiwanie tylko w bibliotece, które są oznaczane `<Library>` element dla elementów programu identyfikowane przez jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="eee0a-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="eee0a-144">Z kolei narzędzia kompilatora Wyszukaj wszystkie biblioteki, w tym.NET Framework podstawowe biblioteki dla elementów programu identyfikowane przez elementy podrzędne [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="eee0a-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="eee0a-145">`<Library>` dyrektywy może być wykorzystywane w warunkowo.</span><span class="sxs-lookup"><span data-stu-id="eee0a-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="eee0a-146">Jeśli nazwa `<Library>` element rozpoczynający się i kończący znak gwiazdki (\*), `<Library>` dyrektywy obowiązuje tylko wtedy, gdy zestaw określony w zakresie od gwiazdki odwołuje się do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eee0a-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="eee0a-147">Na przykład następująca dyrektywa środowisko uruchomieniowe ma zastosowanie tylko wtedy, gdy zestaw Utilities.dll odwołuje się do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eee0a-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eee0a-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eee0a-148">See also</span></span>

- [<span data-ttu-id="eee0a-149">\<Aplikacja > Element</span><span class="sxs-lookup"><span data-stu-id="eee0a-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)
- [<span data-ttu-id="eee0a-150">\<Dyrektywy > Element</span><span class="sxs-lookup"><span data-stu-id="eee0a-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)
- [<span data-ttu-id="eee0a-151">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="eee0a-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="eee0a-152">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="eee0a-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
