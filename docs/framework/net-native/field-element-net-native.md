---
title: <Field>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128417"
---
# <a name="field-element-net-native"></a><span data-ttu-id="1fbdf-102">\<Field>— Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="1fbdf-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="1fbdf-103">Stosuje zasady odbicia środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fbdf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fbdf-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fbdf-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fbdf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1fbdf-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fbdf-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fbdf-107">Attributes</span></span>  
  
|<span data-ttu-id="1fbdf-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1fbdf-108">Attribute</span></span>|<span data-ttu-id="1fbdf-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="1fbdf-109">Attribute type</span></span>|<span data-ttu-id="1fbdf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1fbdf-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1fbdf-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="1fbdf-111">General</span></span>|<span data-ttu-id="1fbdf-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-112">Required attribute.</span></span> <span data-ttu-id="1fbdf-113">Określa nazwę pola.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="1fbdf-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="1fbdf-114">Reflection</span></span>|<span data-ttu-id="1fbdf-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-115">Optional attribute.</span></span> <span data-ttu-id="1fbdf-116">Kontroluje wykonywanie zapytań dotyczących informacji o lub wyliczanie pola, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="1fbdf-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="1fbdf-117">Reflection</span></span>|<span data-ttu-id="1fbdf-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-118">Optional attribute.</span></span> <span data-ttu-id="1fbdf-119">Kontroluje dostęp środowiska uruchomieniowego do pola w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="1fbdf-120">Te zasady zapewniają, że w czasie wykonywania można dynamicznie ustawiać lub pobierać pole.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="1fbdf-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="1fbdf-121">Serialization</span></span>|<span data-ttu-id="1fbdf-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-122">Optional attribute.</span></span> <span data-ttu-id="1fbdf-123">Kontroluje dostęp środowiska uruchomieniowego do pola, aby umożliwić Serializowanie wystąpień typu przez biblioteki takie jak serializator JSON Newtonsoft lub używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1fbdf-124">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="1fbdf-124">Name attribute</span></span>  
  
|<span data-ttu-id="1fbdf-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="1fbdf-125">Value</span></span>|<span data-ttu-id="1fbdf-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1fbdf-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1fbdf-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="1fbdf-127">*method_name*</span></span>|<span data-ttu-id="1fbdf-128">Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-128">The field name.</span></span> <span data-ttu-id="1fbdf-129">Typ pola jest definiowany przez [\<Type>](type-element-net-native.md) element nadrzędny lub [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="1fbdf-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1fbdf-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fbdf-130">All other attributes</span></span>  
  
|<span data-ttu-id="1fbdf-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="1fbdf-131">Value</span></span>|<span data-ttu-id="1fbdf-132">Opis</span><span class="sxs-lookup"><span data-stu-id="1fbdf-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1fbdf-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="1fbdf-133">*policy_setting*</span></span>|<span data-ttu-id="1fbdf-134">Ustawienie, które ma zostać zastosowane do tego typu zasad dla pola.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="1fbdf-135">Możliwe wartości to `Auto` , `Excluded` , `Included` , i `Required` .</span><span class="sxs-lookup"><span data-stu-id="1fbdf-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="1fbdf-136">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="1fbdf-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fbdf-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fbdf-137">Child Elements</span></span>  
 <span data-ttu-id="1fbdf-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fbdf-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fbdf-139">Parent Elements</span></span>  
  
|<span data-ttu-id="1fbdf-140">Element</span><span class="sxs-lookup"><span data-stu-id="1fbdf-140">Element</span></span>|<span data-ttu-id="1fbdf-141">Opis</span><span class="sxs-lookup"><span data-stu-id="1fbdf-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="1fbdf-142">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="1fbdf-143">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fbdf-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fbdf-144">Remarks</span></span>  
 <span data-ttu-id="1fbdf-145">Jeśli zasady pola nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1fbdf-145">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fbdf-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fbdf-146">See also</span></span>

- [<span data-ttu-id="1fbdf-147">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1fbdf-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="1fbdf-148">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="1fbdf-148">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1fbdf-149">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1fbdf-149">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
