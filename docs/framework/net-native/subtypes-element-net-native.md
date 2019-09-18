---
title: <Subtypes>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af1acc02b18c5b97ef66ccae9b70c1f5327bff4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049124"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="8f1de-102">\<Podtypy > element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="8f1de-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="8f1de-103">Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="8f1de-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f1de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f1de-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f1de-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8f1de-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8f1de-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8f1de-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f1de-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f1de-107">Attributes</span></span>  
  
|<span data-ttu-id="8f1de-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8f1de-108">Attribute</span></span>|<span data-ttu-id="8f1de-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="8f1de-109">Attribute type</span></span>|<span data-ttu-id="8f1de-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8f1de-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="8f1de-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="8f1de-111">Reflection</span></span>|<span data-ttu-id="8f1de-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-112">Optional attribute.</span></span> <span data-ttu-id="8f1de-113">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8f1de-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="8f1de-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="8f1de-114">Reflection</span></span>|<span data-ttu-id="8f1de-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-115">Optional attribute.</span></span> <span data-ttu-id="8f1de-116">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8f1de-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="8f1de-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="8f1de-117">Reflection</span></span>|<span data-ttu-id="8f1de-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-118">Optional attribute.</span></span> <span data-ttu-id="8f1de-119">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="8f1de-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="8f1de-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f1de-120">Serialization</span></span>|<span data-ttu-id="8f1de-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-121">Optional attribute.</span></span> <span data-ttu-id="8f1de-122">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i deserializacja wystąpień typów przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="8f1de-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="8f1de-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f1de-123">Serialization</span></span>|<span data-ttu-id="8f1de-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-124">Optional attribute.</span></span> <span data-ttu-id="8f1de-125">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f1de-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="8f1de-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f1de-126">Serialization</span></span>|<span data-ttu-id="8f1de-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-127">Optional attribute.</span></span> <span data-ttu-id="8f1de-128">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f1de-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="8f1de-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="8f1de-129">Serialization</span></span>|<span data-ttu-id="8f1de-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-130">Optional attribute.</span></span> <span data-ttu-id="8f1de-131">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8f1de-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="8f1de-132">Interop</span><span class="sxs-lookup"><span data-stu-id="8f1de-132">Interop</span></span>|<span data-ttu-id="8f1de-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-133">Optional attribute.</span></span> <span data-ttu-id="8f1de-134">Kontroluje zasady dotyczące organizowania typów odwołań do środowisko wykonawcze systemu Windows i COM.</span><span class="sxs-lookup"><span data-stu-id="8f1de-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="8f1de-135">Interop</span><span class="sxs-lookup"><span data-stu-id="8f1de-135">Interop</span></span>|<span data-ttu-id="8f1de-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-136">Optional attribute.</span></span> <span data-ttu-id="8f1de-137">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="8f1de-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="8f1de-138">Interop</span><span class="sxs-lookup"><span data-stu-id="8f1de-138">Interop</span></span>|<span data-ttu-id="8f1de-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-139">Optional attribute.</span></span> <span data-ttu-id="8f1de-140">Steruje zasadami dotyczącymi organizowania typów wartości na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="8f1de-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f1de-141">All attributes</span></span>  
  
|<span data-ttu-id="8f1de-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="8f1de-142">Value</span></span>|<span data-ttu-id="8f1de-143">Opis</span><span class="sxs-lookup"><span data-stu-id="8f1de-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f1de-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8f1de-144">*policy_setting*</span></span>|<span data-ttu-id="8f1de-145">Ustawienie, które ma zostać zastosowane do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="8f1de-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="8f1de-146">Możliwe wartości to `All`, `Auto` `Excluded` ,,`Public` ,,`Required All`, i. `PublicAndInternal` `Required Public` `Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="8f1de-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="8f1de-147">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8f1de-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f1de-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8f1de-148">Child Elements</span></span>  
 <span data-ttu-id="8f1de-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="8f1de-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f1de-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8f1de-150">Parent Elements</span></span>  
  
|<span data-ttu-id="8f1de-151">Element</span><span class="sxs-lookup"><span data-stu-id="8f1de-151">Element</span></span>|<span data-ttu-id="8f1de-152">Opis</span><span class="sxs-lookup"><span data-stu-id="8f1de-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f1de-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="8f1de-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="8f1de-154">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="8f1de-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f1de-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f1de-155">Remarks</span></span>  
 <span data-ttu-id="8f1de-156">`<Subtypes>` Element stosuje zasady do wszystkich podtypów zawierającego go typu.</span><span class="sxs-lookup"><span data-stu-id="8f1de-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="8f1de-157">Jest ona używana, gdy chcesz zastosować różne zasady do typów pochodnych i ich klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="8f1de-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="8f1de-158">Atrybuty odbicia, serializacji i międzyoperacyjności są opcjonalne, chociaż co najmniej jeden z nich powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="8f1de-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f1de-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f1de-159">Example</span></span>  
 <span data-ttu-id="8f1de-160">W poniższym przykładzie zdefiniowano klasę o `BaseClass` nazwie i podklasą o nazwie. `Derived1`</span><span class="sxs-lookup"><span data-stu-id="8f1de-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="8f1de-161">Jak pokazano w poniższym kodzie, plik `Dynamic` dyrektywy środowiska uruchomieniowego jawnie ustawia zasady i `Activate` dla `BaseClass` na `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="8f1de-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="8f1de-162">Z tego powodu obiekty typu `BaseClass` nie mogą być tworzone dynamicznie lub przez wywołania `BaseClass` konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="8f1de-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="8f1de-163">Jednakże element pozwala na dynamiczne tworzenie wystąpień klas `BaseClass` pochodzących z programu, a za pomocą wywołań do ich konstruktorów klas. `<Subtypes>`</span><span class="sxs-lookup"><span data-stu-id="8f1de-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="8f1de-164">Ze względu `<Subtypes>` na dyrektywę, poniższy kod, który `Derived1` tworzy <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> wystąpienie dynamicznie przez wywołanie metody zostało wykonane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8f1de-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="8f1de-165">Tutaj zmienna blokowa jest <xref:System.Windows.Controls.TextBlock> obiektem w pustej aplikacji ze sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="8f1de-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8f1de-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f1de-166">See also</span></span>

- [<span data-ttu-id="8f1de-167">\<Typ > element</span><span class="sxs-lookup"><span data-stu-id="8f1de-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="8f1de-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8f1de-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8f1de-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8f1de-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="8f1de-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8f1de-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
