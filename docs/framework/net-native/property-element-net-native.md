---
title: Element &lt;Property&gt; (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ed75d377814a740edece2b6a69e44acbd8ef0c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676814"
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="5654c-102">Element &lt;Property&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="5654c-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="5654c-103">Zastosowanie zasad odbicia środowiska uruchomieniowego do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5654c-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5654c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5654c-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5654c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5654c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5654c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5654c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5654c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5654c-107">Attributes</span></span>  
  
|<span data-ttu-id="5654c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5654c-108">Attribute</span></span>|<span data-ttu-id="5654c-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="5654c-109">Attribute type</span></span>|<span data-ttu-id="5654c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5654c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="5654c-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="5654c-111">General</span></span>|<span data-ttu-id="5654c-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5654c-112">Required attribute.</span></span> <span data-ttu-id="5654c-113">Określa nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="5654c-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="5654c-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5654c-114">Reflection</span></span>|<span data-ttu-id="5654c-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5654c-115">Optional attribute.</span></span> <span data-ttu-id="5654c-116">Określa wykonanie zapytania dotyczącego informacji o wyliczanie właściwości, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5654c-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="5654c-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="5654c-117">Reflection</span></span>|<span data-ttu-id="5654c-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5654c-118">Optional attribute.</span></span> <span data-ttu-id="5654c-119">Dostęp do środowiska uruchomieniowego formanty do właściwości, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="5654c-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="5654c-120">Te zasady zapewniają, że właściwość można ustawić lub pobrać dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5654c-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="5654c-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="5654c-121">Serialization</span></span>|<span data-ttu-id="5654c-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5654c-122">Optional attribute.</span></span> <span data-ttu-id="5654c-123">Kontroluje dostęp do środowiska uruchomieniowego do właściwości w celu włączenia wystąpień typu przez biblioteki, takie jak serializator Newtonsoft JSON lub ma być używany dla powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5654c-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5654c-124">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="5654c-124">Name attribute</span></span>  
  
|<span data-ttu-id="5654c-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="5654c-125">Value</span></span>|<span data-ttu-id="5654c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="5654c-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5654c-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="5654c-127">*method_name*</span></span>|<span data-ttu-id="5654c-128">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="5654c-128">The property name.</span></span> <span data-ttu-id="5654c-129">Typ właściwości jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5654c-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="5654c-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="5654c-130">All other attributes</span></span>  
  
|<span data-ttu-id="5654c-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="5654c-131">Value</span></span>|<span data-ttu-id="5654c-132">Opis</span><span class="sxs-lookup"><span data-stu-id="5654c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5654c-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="5654c-133">*policy_setting*</span></span>|<span data-ttu-id="5654c-134">Ustawienia do zastosowania do tego typu zasad dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="5654c-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="5654c-135">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="5654c-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="5654c-136">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5654c-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5654c-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5654c-137">Child Elements</span></span>  
 <span data-ttu-id="5654c-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="5654c-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5654c-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5654c-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5654c-140">Element</span><span class="sxs-lookup"><span data-stu-id="5654c-140">Element</span></span>|<span data-ttu-id="5654c-141">Opis</span><span class="sxs-lookup"><span data-stu-id="5654c-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5654c-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="5654c-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="5654c-143">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5654c-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="5654c-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="5654c-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="5654c-145">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5654c-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5654c-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5654c-146">Remarks</span></span>  
 <span data-ttu-id="5654c-147">Jeśli właściwość zasad nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania odpowiedniego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5654c-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5654c-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="5654c-148">Example</span></span>  
 <span data-ttu-id="5654c-149">W poniższym przykładzie użyto odbicia w celu utworzenia wystąpienia `Book` obiektów i wyświetlić jego wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5654c-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="5654c-150">Oryginalny plik default.rd.xml projektu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="5654c-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="5654c-151">Plik ma zastosowanie `All` wartość `Activate` zasady dla `Book` klasy, która zezwala na dostęp do konstruktorów klas przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="5654c-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="5654c-152">`Browse` Zasady `Book` klasy jest dziedziczony z jego nadrzędna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="5654c-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="5654c-153">Jest ono ustawione na `Required Public`, co sprawia, że metadane dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5654c-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="5654c-154">Poniżej znajduje się kod źródłowy dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="5654c-154">The following is the source code for the example.</span></span> <span data-ttu-id="5654c-155">`outputBlock` Reprezentuje zmienną [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) kontroli.</span><span class="sxs-lookup"><span data-stu-id="5654c-155">The `outputBlock` variable represents a [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="5654c-156">Jednak kompilowanie i wykonywania w tym przykładzie zgłasza [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5654c-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="5654c-157">Mimo że wprowadziliśmy metadanych `Book` typ jest dostępny, już nie możemy udostępnić implementacji metody pobierające właściwości dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="5654c-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="5654c-158">Możemy naprawić ten błąd, wybierając w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="5654c-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="5654c-159">Definiując `Dynamic` zasady `Book` wpisz jego [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5654c-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="5654c-160">Dodając zagnieżdżoną [ \<właściwości >](../../../docs/framework/net-native/property-element-net-native.md) dla każdej właściwości, której metody pobierającej, prosimy o poświęcenie do wywołania, tak jak w następującym pliku default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="5654c-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5654c-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5654c-161">See Also</span></span>  
 [<span data-ttu-id="5654c-162">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5654c-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="5654c-163">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5654c-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="5654c-164">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5654c-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
