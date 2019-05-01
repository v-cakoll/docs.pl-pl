---
title: <Subtypes> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0ec1ed73148b319217a70cc3be99b486be2f8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866857"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="ac514-102">\<Podtypy > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="ac514-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="ac514-103">Stosuje zasady środowiska uruchomieniowego dla wszystkich klas dziedziczone z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ac514-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac514-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac514-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"   
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac514-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ac514-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ac514-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ac514-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac514-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac514-107">Attributes</span></span>  
  
|<span data-ttu-id="ac514-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ac514-108">Attribute</span></span>|<span data-ttu-id="ac514-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="ac514-109">Attribute type</span></span>|<span data-ttu-id="ac514-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ac514-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="ac514-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="ac514-111">Reflection</span></span>|<span data-ttu-id="ac514-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-112">Optional attribute.</span></span> <span data-ttu-id="ac514-113">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.</span><span class="sxs-lookup"><span data-stu-id="ac514-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="ac514-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="ac514-114">Reflection</span></span>|<span data-ttu-id="ac514-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-115">Optional attribute.</span></span> <span data-ttu-id="ac514-116">Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ac514-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="ac514-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="ac514-117">Reflection</span></span>|<span data-ttu-id="ac514-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-118">Optional attribute.</span></span> <span data-ttu-id="ac514-119">Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="ac514-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="ac514-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="ac514-120">Serialization</span></span>|<span data-ttu-id="ac514-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-121">Optional attribute.</span></span> <span data-ttu-id="ac514-122">Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="ac514-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="ac514-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="ac514-123">Serialization</span></span>|<span data-ttu-id="ac514-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-124">Optional attribute.</span></span> <span data-ttu-id="ac514-125">Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ac514-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="ac514-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="ac514-126">Serialization</span></span>|<span data-ttu-id="ac514-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-127">Optional attribute.</span></span> <span data-ttu-id="ac514-128">Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ac514-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="ac514-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="ac514-129">Serialization</span></span>|<span data-ttu-id="ac514-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-130">Optional attribute.</span></span> <span data-ttu-id="ac514-131">Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="ac514-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="ac514-132">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="ac514-132">Interop</span></span>|<span data-ttu-id="ac514-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-133">Optional attribute.</span></span> <span data-ttu-id="ac514-134">Zasady kontroli marshaling typów referencyjnych do środowiska uruchomieniowego Windows i modelu COM.</span><span class="sxs-lookup"><span data-stu-id="ac514-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="ac514-135">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="ac514-135">Interop</span></span>|<span data-ttu-id="ac514-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-136">Optional attribute.</span></span> <span data-ttu-id="ac514-137">Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="ac514-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="ac514-138">Usługa międzyoperacyjna</span><span class="sxs-lookup"><span data-stu-id="ac514-138">Interop</span></span>|<span data-ttu-id="ac514-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac514-139">Optional attribute.</span></span> <span data-ttu-id="ac514-140">Określa zasady dla marshaling typów wartości do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="ac514-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="ac514-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac514-141">All attributes</span></span>  
  
|<span data-ttu-id="ac514-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="ac514-142">Value</span></span>|<span data-ttu-id="ac514-143">Opis</span><span class="sxs-lookup"><span data-stu-id="ac514-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac514-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ac514-144">*policy_setting*</span></span>|<span data-ttu-id="ac514-145">Ustawienia do zastosowania do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="ac514-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="ac514-146">Możliwe wartości to `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, i `Required All`.</span><span class="sxs-lookup"><span data-stu-id="ac514-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="ac514-147">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ac514-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac514-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ac514-148">Child Elements</span></span>  
 <span data-ttu-id="ac514-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="ac514-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac514-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ac514-150">Parent Elements</span></span>  
  
|<span data-ttu-id="ac514-151">Element</span><span class="sxs-lookup"><span data-stu-id="ac514-151">Element</span></span>|<span data-ttu-id="ac514-152">Opis</span><span class="sxs-lookup"><span data-stu-id="ac514-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac514-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="ac514-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ac514-154">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ac514-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac514-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac514-155">Remarks</span></span>  
 <span data-ttu-id="ac514-156">`<Subtypes>` Element dotyczy podtypy jej typ zawierający zasady.</span><span class="sxs-lookup"><span data-stu-id="ac514-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="ac514-157">Możesz użyć, jeśli chcesz zastosować zasady różnych typów pochodnych i ich klasami podstawowymi.</span><span class="sxs-lookup"><span data-stu-id="ac514-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="ac514-158">Odbicia, serializacja i atrybutów międzyoperacyjności są wszystkie opcjonalne, ale co najmniej jeden powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="ac514-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac514-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac514-159">Example</span></span>  
 <span data-ttu-id="ac514-160">W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` i podklasą klasy o nazwie `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="ac514-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="ac514-161">Jak pokazano w poniższym kodzie, dyrektywy środowiska uruchomieniowego jawnie plików zestawów `Dynamic` i `Activate` zasad `BaseClass` do `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="ac514-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="ac514-162">Ze względu na to, obiekty typu `BaseClass` nie można utworzyć wystąpienia dynamicznie lub przez wywołania do `BaseClass` konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="ac514-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="ac514-163">Jednak `<Subtypes>` elementu umożliwia klasy pochodne `BaseClass` z myślą o uruchamianiu dynamicznie i za pośrednictwem wywołania ich Konstruktory klasy.</span><span class="sxs-lookup"><span data-stu-id="ac514-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="ac514-164">Z powodu `<Subtypes>` dyrektywy, następujący kod, który tworzy wystąpienie `Derived1` wystąpienia dynamicznie przez wywołanie metody <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> metoda wykonuje z powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ac514-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="ac514-165">W tym miejscu zmienna bloku jest <xref:System.Windows.Controls.TextBlock> obiektu w pustej aplikacji Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ac514-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ac514-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac514-166">See also</span></span>

- [<span data-ttu-id="ac514-167">\<Typ > Element</span><span class="sxs-lookup"><span data-stu-id="ac514-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="ac514-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ac514-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ac514-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ac514-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="ac514-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ac514-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
