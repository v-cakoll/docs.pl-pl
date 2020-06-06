---
title: <Property>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128211"
---
# <a name="property-element-net-native"></a><span data-ttu-id="b3c36-102">\<Property>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b3c36-102">\<Property> Element (.NET Native)</span></span>
<span data-ttu-id="b3c36-103">Stosuje zasady odbicia środowiska uruchomieniowego do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c36-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3c36-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3c36-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3c36-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b3c36-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3c36-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3c36-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3c36-107">Attributes</span></span>  
  
|<span data-ttu-id="b3c36-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b3c36-108">Attribute</span></span>|<span data-ttu-id="b3c36-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="b3c36-109">Attribute type</span></span>|<span data-ttu-id="b3c36-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b3c36-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="b3c36-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="b3c36-111">General</span></span>|<span data-ttu-id="b3c36-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b3c36-112">Required attribute.</span></span> <span data-ttu-id="b3c36-113">Określa nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c36-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="b3c36-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b3c36-114">Reflection</span></span>|<span data-ttu-id="b3c36-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b3c36-115">Optional attribute.</span></span> <span data-ttu-id="b3c36-116">Kontroluje wykonywanie zapytań dotyczących informacji o lub wyliczania właściwości, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3c36-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="b3c36-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="b3c36-117">Reflection</span></span>|<span data-ttu-id="b3c36-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b3c36-118">Optional attribute.</span></span> <span data-ttu-id="b3c36-119">Kontroluje dostęp środowiska uruchomieniowego do właściwości w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="b3c36-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="b3c36-120">Te zasady zapewniają, że właściwość może być ustawiana lub pobierana dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3c36-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="b3c36-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="b3c36-121">Serialization</span></span>|<span data-ttu-id="b3c36-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b3c36-122">Optional attribute.</span></span> <span data-ttu-id="b3c36-123">Kontroluje dostęp środowiska uruchomieniowego do właściwości, aby umożliwić Serializowanie wystąpień typu przez biblioteki takie jak serializator JSON Newtonsoft lub używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="b3c36-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="b3c36-124">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="b3c36-124">Name attribute</span></span>  
  
|<span data-ttu-id="b3c36-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="b3c36-125">Value</span></span>|<span data-ttu-id="b3c36-126">Opis</span><span class="sxs-lookup"><span data-stu-id="b3c36-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b3c36-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="b3c36-127">*method_name*</span></span>|<span data-ttu-id="b3c36-128">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c36-128">The property name.</span></span> <span data-ttu-id="b3c36-129">Typ właściwości jest zdefiniowany przez [\<Type>](type-element-net-native.md) element nadrzędny lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c36-129">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="b3c36-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3c36-130">All other attributes</span></span>  
  
|<span data-ttu-id="b3c36-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="b3c36-131">Value</span></span>|<span data-ttu-id="b3c36-132">Opis</span><span class="sxs-lookup"><span data-stu-id="b3c36-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b3c36-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="b3c36-133">*policy_setting*</span></span>|<span data-ttu-id="b3c36-134">Ustawienie, które ma zostać zastosowane do tego typu zasad dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c36-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="b3c36-135">Możliwe wartości to `Auto` , `Excluded` , `Included` , i `Required` .</span><span class="sxs-lookup"><span data-stu-id="b3c36-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="b3c36-136">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b3c36-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3c36-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3c36-137">Child Elements</span></span>  
 <span data-ttu-id="b3c36-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="b3c36-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3c36-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3c36-139">Parent Elements</span></span>  
  
|<span data-ttu-id="b3c36-140">Element</span><span class="sxs-lookup"><span data-stu-id="b3c36-140">Element</span></span>|<span data-ttu-id="b3c36-141">Opis</span><span class="sxs-lookup"><span data-stu-id="b3c36-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="b3c36-142">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="b3c36-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b3c36-143">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="b3c36-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c36-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3c36-144">Remarks</span></span>  
 <span data-ttu-id="b3c36-145">Jeśli zasady właściwości nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b3c36-145">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3c36-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3c36-146">Example</span></span>  
 <span data-ttu-id="b3c36-147">Poniższy przykład używa odbicia, aby utworzyć wystąpienie `Book` obiektu i wyświetlić jego wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c36-147">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="b3c36-148">Oryginalny plik default. Rd. XML dla projektu jest wyświetlany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b3c36-148">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="b3c36-149">Plik stosuje `All` wartość do `Activate` zasad dla `Book` klasy, co umożliwia dostęp do konstruktorów klas poprzez odbicie.</span><span class="sxs-lookup"><span data-stu-id="b3c36-149">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="b3c36-150">`Browse`Zasady dla `Book` klasy są dziedziczone z jego nadrzędnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b3c36-150">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="b3c36-151">Ta wartość jest ustawiona na `Required Public` , co sprawia, że metadane są dostępne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3c36-151">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="b3c36-152">Poniżej znajduje się kod źródłowy dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="b3c36-152">The following is the source code for the example.</span></span> <span data-ttu-id="b3c36-153">`outputBlock`Zmienna reprezentuje <xref:Windows.UI.Xaml.Controls.TextBlock> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="b3c36-153">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="b3c36-154">Jednak Kompilowanie i wykonywanie tego przykładu zgłasza wyjątek [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c36-154">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="b3c36-155">Mimo że zostały zgłoszone metadane dla `Book` dostępnego typu, nie udało nam się zapewnić, że implementacje metod pobierających właściwości są dostępne dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="b3c36-155">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="b3c36-156">Możemy naprawić ten błąd w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="b3c36-156">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="b3c36-157">Definiowanie `Dynamic` zasad dla `Book` typu w jego [\<Type>](type-element-net-native.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="b3c36-157">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="b3c36-158">Dodając zagnieżdżony [\<Property>](property-element-net-native.md) element dla każdej właściwości, której ma dotyczyć metoda pobierająca, jako następujący domyślny plik. Rd. XML.</span><span class="sxs-lookup"><span data-stu-id="b3c36-158">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3c36-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3c36-159">See also</span></span>

- [<span data-ttu-id="b3c36-160">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b3c36-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b3c36-161">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b3c36-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="b3c36-162">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b3c36-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
