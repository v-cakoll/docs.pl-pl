---
title: Element <Field> (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128417"
---
# <a name="field-element-net-native"></a><span data-ttu-id="2730c-102">\<pole > elementu (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="2730c-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="2730c-103">Stosuje zasady odbicia środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="2730c-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2730c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2730c-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2730c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2730c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2730c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2730c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2730c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2730c-107">Attributes</span></span>  
  
|<span data-ttu-id="2730c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2730c-108">Attribute</span></span>|<span data-ttu-id="2730c-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="2730c-109">Attribute type</span></span>|<span data-ttu-id="2730c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2730c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="2730c-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="2730c-111">General</span></span>|<span data-ttu-id="2730c-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="2730c-112">Required attribute.</span></span> <span data-ttu-id="2730c-113">Określa nazwę pola.</span><span class="sxs-lookup"><span data-stu-id="2730c-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="2730c-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="2730c-114">Reflection</span></span>|<span data-ttu-id="2730c-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2730c-115">Optional attribute.</span></span> <span data-ttu-id="2730c-116">Kontroluje wykonywanie zapytań dotyczących informacji o lub wyliczanie pola, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2730c-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="2730c-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="2730c-117">Reflection</span></span>|<span data-ttu-id="2730c-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2730c-118">Optional attribute.</span></span> <span data-ttu-id="2730c-119">Kontroluje dostęp środowiska uruchomieniowego do pola w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="2730c-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="2730c-120">Te zasady zapewniają, że w czasie wykonywania można dynamicznie ustawiać lub pobierać pole.</span><span class="sxs-lookup"><span data-stu-id="2730c-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="2730c-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="2730c-121">Serialization</span></span>|<span data-ttu-id="2730c-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2730c-122">Optional attribute.</span></span> <span data-ttu-id="2730c-123">Kontroluje dostęp środowiska uruchomieniowego do pola, aby umożliwić Serializowanie wystąpień typu przez biblioteki takie jak serializator JSON Newtonsoft lub używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="2730c-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="2730c-124">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="2730c-124">Name attribute</span></span>  
  
|<span data-ttu-id="2730c-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="2730c-125">Value</span></span>|<span data-ttu-id="2730c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="2730c-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2730c-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="2730c-127">*method_name*</span></span>|<span data-ttu-id="2730c-128">Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="2730c-128">The field name.</span></span> <span data-ttu-id="2730c-129">Typ pola jest definiowany przez [typ\<nadrzędnego >](type-element-net-native.md) lub [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="2730c-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="2730c-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="2730c-130">All other attributes</span></span>  
  
|<span data-ttu-id="2730c-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="2730c-131">Value</span></span>|<span data-ttu-id="2730c-132">Opis</span><span class="sxs-lookup"><span data-stu-id="2730c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2730c-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="2730c-133">*policy_setting*</span></span>|<span data-ttu-id="2730c-134">Ustawienie, które ma zostać zastosowane do tego typu zasad dla pola.</span><span class="sxs-lookup"><span data-stu-id="2730c-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="2730c-135">Możliwe wartości to `Auto`, `Excluded`, `Included`i `Required`.</span><span class="sxs-lookup"><span data-stu-id="2730c-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="2730c-136">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2730c-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2730c-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2730c-137">Child Elements</span></span>  
 <span data-ttu-id="2730c-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="2730c-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2730c-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2730c-139">Parent Elements</span></span>  
  
|<span data-ttu-id="2730c-140">Element</span><span class="sxs-lookup"><span data-stu-id="2730c-140">Element</span></span>|<span data-ttu-id="2730c-141">Opis</span><span class="sxs-lookup"><span data-stu-id="2730c-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2730c-142">Typ\<</span><span class="sxs-lookup"><span data-stu-id="2730c-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="2730c-143">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="2730c-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="2730c-144">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="2730c-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="2730c-145">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="2730c-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2730c-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2730c-146">Remarks</span></span>  
 <span data-ttu-id="2730c-147">Jeśli zasady pola nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2730c-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2730c-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2730c-148">See also</span></span>

- [<span data-ttu-id="2730c-149">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2730c-149">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="2730c-150">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="2730c-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="2730c-151">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2730c-151">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
