---
title: <Subtypes>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180937"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="cad85-102">\<Podtypy> elementu (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="cad85-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="cad85-103">Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="cad85-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cad85-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cad85-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cad85-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cad85-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cad85-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cad85-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cad85-107">Attributes</span></span>  
  
|<span data-ttu-id="cad85-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cad85-108">Attribute</span></span>|<span data-ttu-id="cad85-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="cad85-109">Attribute type</span></span>|<span data-ttu-id="cad85-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cad85-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="cad85-111">Odbicie</span><span class="sxs-lookup"><span data-stu-id="cad85-111">Reflection</span></span>|<span data-ttu-id="cad85-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-112">Optional attribute.</span></span> <span data-ttu-id="cad85-113">Steruje dostępem środowiska wykonawczego do konstruktorów, aby włączyć aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="cad85-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="cad85-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="cad85-114">Reflection</span></span>|<span data-ttu-id="cad85-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-115">Optional attribute.</span></span> <span data-ttu-id="cad85-116">Steruje wykonywaniem zapytań o informacje o elementach programu, ale nie włącza dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cad85-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="cad85-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="cad85-117">Reflection</span></span>|<span data-ttu-id="cad85-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-118">Optional attribute.</span></span> <span data-ttu-id="cad85-119">Steruje dostępem środowiska uruchomieniowego do wszystkich elementów członkowskich typu, w tym konstruktorów, metod, pól, właściwości i zdarzeń, aby włączyć programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="cad85-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="cad85-120">Serializacja</span><span class="sxs-lookup"><span data-stu-id="cad85-120">Serialization</span></span>|<span data-ttu-id="cad85-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-121">Optional attribute.</span></span> <span data-ttu-id="cad85-122">Steruje dostępem środowiska wykonawczego do konstruktorów, pól i właściwości, aby umożliwić serializowanie i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON firmy Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="cad85-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="cad85-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="cad85-123">Serialization</span></span>|<span data-ttu-id="cad85-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-124">Optional attribute.</span></span> <span data-ttu-id="cad85-125">Steruje zasadami serializacji, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> która używa klasy.</span><span class="sxs-lookup"><span data-stu-id="cad85-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="cad85-126">Serializacja</span><span class="sxs-lookup"><span data-stu-id="cad85-126">Serialization</span></span>|<span data-ttu-id="cad85-127">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-127">Optional attribute.</span></span> <span data-ttu-id="cad85-128">Steruje zasadami serializacji JSON, która używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="cad85-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="cad85-129">Serializacja</span><span class="sxs-lookup"><span data-stu-id="cad85-129">Serialization</span></span>|<span data-ttu-id="cad85-130">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-130">Optional attribute.</span></span> <span data-ttu-id="cad85-131">Steruje zasadami serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> tej klasy.</span><span class="sxs-lookup"><span data-stu-id="cad85-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="cad85-132">Interop</span><span class="sxs-lookup"><span data-stu-id="cad85-132">Interop</span></span>|<span data-ttu-id="cad85-133">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-133">Optional attribute.</span></span> <span data-ttu-id="cad85-134">Steruje zasadami organizowania typów odwołań do środowiska wykonawczego systemu Windows i środowiska COM.</span><span class="sxs-lookup"><span data-stu-id="cad85-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="cad85-135">Interop</span><span class="sxs-lookup"><span data-stu-id="cad85-135">Interop</span></span>|<span data-ttu-id="cad85-136">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-136">Optional attribute.</span></span> <span data-ttu-id="cad85-137">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="cad85-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="cad85-138">Interop</span><span class="sxs-lookup"><span data-stu-id="cad85-138">Interop</span></span>|<span data-ttu-id="cad85-139">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cad85-139">Optional attribute.</span></span> <span data-ttu-id="cad85-140">Steruje zasadami organizowania typów wartości do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="cad85-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="cad85-141">Wszystkie atrybuty</span><span class="sxs-lookup"><span data-stu-id="cad85-141">All attributes</span></span>  
  
|<span data-ttu-id="cad85-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="cad85-142">Value</span></span>|<span data-ttu-id="cad85-143">Opis</span><span class="sxs-lookup"><span data-stu-id="cad85-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cad85-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="cad85-144">*policy_setting*</span></span>|<span data-ttu-id="cad85-145">Ustawienie, które ma zastosowanie do tego typu zasad.</span><span class="sxs-lookup"><span data-stu-id="cad85-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="cad85-146">Możliwe wartości `All` `Auto`to `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , i .</span><span class="sxs-lookup"><span data-stu-id="cad85-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="cad85-147">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="cad85-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cad85-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cad85-148">Child Elements</span></span>  
 <span data-ttu-id="cad85-149">Brak.</span><span class="sxs-lookup"><span data-stu-id="cad85-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cad85-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cad85-150">Parent Elements</span></span>  
  
|<span data-ttu-id="cad85-151">Element</span><span class="sxs-lookup"><span data-stu-id="cad85-151">Element</span></span>|<span data-ttu-id="cad85-152">Opis</span><span class="sxs-lookup"><span data-stu-id="cad85-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cad85-153">\<Typ></span><span class="sxs-lookup"><span data-stu-id="cad85-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="cad85-154">Stosuje zasady odbicia do typu i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="cad85-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cad85-155">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cad85-155">Remarks</span></span>  
 <span data-ttu-id="cad85-156">Element `<Subtypes>` stosuje zasady do wszystkich podtypów jego typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="cad85-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="cad85-157">Można go używać, gdy chcesz zastosować różne zasady do typów pochodnych i ich klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="cad85-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="cad85-158">Atrybuty odbicia, serializacji i międzyoperacyjne są opcjonalne, chociaż co najmniej jeden powinien być obecny.</span><span class="sxs-lookup"><span data-stu-id="cad85-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cad85-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="cad85-159">Example</span></span>  
 <span data-ttu-id="cad85-160">Poniższy przykład definiuje klasę `BaseClass` o nazwie `Derived1`i podklasę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="cad85-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="cad85-161">Jak pokazano w poniższym kodzie, plik dyrektyw `Dynamic` środowiska `Activate` uruchomieniowego jawnie ustawia zasady i zasady dla `BaseClass` . `Excluded`</span><span class="sxs-lookup"><span data-stu-id="cad85-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="cad85-162">Z tego powodu obiekty `BaseClass` typu nie mogą być tworzone dynamicznie lub przez wywołania konstruktora `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="cad85-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="cad85-163">Jednak `<Subtypes>` element umożliwia klasy pochodzące z `BaseClass` do wystąpienia dynamicznie i za pośrednictwem wywołań do ich konstruktorów klas.</span><span class="sxs-lookup"><span data-stu-id="cad85-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="cad85-164">Ze względu `<Subtypes>` na dyrektywę następujący kod, `Derived1` który dynamicznie <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> wywołuje wystąpienie, wywołując metodę, jest wykonywana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cad85-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="cad85-165">Zmienna bloku w <xref:System.Windows.Controls.TextBlock> tym miejscu jest obiektem w pustej aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="cad85-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="cad85-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cad85-166">See also</span></span>

- [<span data-ttu-id="cad85-167">\<Wpisz element></span><span class="sxs-lookup"><span data-stu-id="cad85-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="cad85-168">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="cad85-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="cad85-169">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="cad85-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="cad85-170">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="cad85-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
