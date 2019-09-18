---
title: <Field>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dfb6a07f9733ab1a01a1ce9917c6a4bb4ce793b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049778"
---
# <a name="field-element-net-native"></a><span data-ttu-id="0a70d-102">\<Element > pola (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0a70d-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="0a70d-103">Stosuje zasady odbicia środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="0a70d-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a70d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a70d-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a70d-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0a70d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0a70d-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0a70d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a70d-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0a70d-107">Attributes</span></span>  
  
|<span data-ttu-id="0a70d-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0a70d-108">Attribute</span></span>|<span data-ttu-id="0a70d-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="0a70d-109">Attribute type</span></span>|<span data-ttu-id="0a70d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0a70d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0a70d-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="0a70d-111">General</span></span>|<span data-ttu-id="0a70d-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0a70d-112">Required attribute.</span></span> <span data-ttu-id="0a70d-113">Określa nazwę pola.</span><span class="sxs-lookup"><span data-stu-id="0a70d-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="0a70d-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0a70d-114">Reflection</span></span>|<span data-ttu-id="0a70d-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0a70d-115">Optional attribute.</span></span> <span data-ttu-id="0a70d-116">Kontroluje wykonywanie zapytań dotyczących informacji o lub wyliczanie pola, ale nie umożliwia dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0a70d-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0a70d-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0a70d-117">Reflection</span></span>|<span data-ttu-id="0a70d-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0a70d-118">Optional attribute.</span></span> <span data-ttu-id="0a70d-119">Kontroluje dostęp środowiska uruchomieniowego do pola w celu włączenia programowania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="0a70d-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="0a70d-120">Te zasady zapewniają, że w czasie wykonywania można dynamicznie ustawiać lub pobierać pole.</span><span class="sxs-lookup"><span data-stu-id="0a70d-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="0a70d-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="0a70d-121">Serialization</span></span>|<span data-ttu-id="0a70d-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0a70d-122">Optional attribute.</span></span> <span data-ttu-id="0a70d-123">Kontroluje dostęp środowiska uruchomieniowego do pola, aby umożliwić Serializowanie wystąpień typu przez biblioteki takie jak serializator JSON Newtonsoft lub używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="0a70d-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0a70d-124">Atrybut nazwy</span><span class="sxs-lookup"><span data-stu-id="0a70d-124">Name attribute</span></span>  
  
|<span data-ttu-id="0a70d-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="0a70d-125">Value</span></span>|<span data-ttu-id="0a70d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="0a70d-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a70d-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="0a70d-127">*method_name*</span></span>|<span data-ttu-id="0a70d-128">Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="0a70d-128">The field name.</span></span> <span data-ttu-id="0a70d-129">Typ pola jest zdefiniowany przez [ \<typ nadrzędny >](type-element-net-native.md) lub [ \<element > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="0a70d-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0a70d-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="0a70d-130">All other attributes</span></span>  
  
|<span data-ttu-id="0a70d-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="0a70d-131">Value</span></span>|<span data-ttu-id="0a70d-132">Opis</span><span class="sxs-lookup"><span data-stu-id="0a70d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a70d-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0a70d-133">*policy_setting*</span></span>|<span data-ttu-id="0a70d-134">Ustawienie, które ma zostać zastosowane do tego typu zasad dla pola.</span><span class="sxs-lookup"><span data-stu-id="0a70d-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="0a70d-135">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="0a70d-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="0a70d-136">Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska uruchomieniowego](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0a70d-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a70d-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0a70d-137">Child Elements</span></span>  
 <span data-ttu-id="0a70d-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a70d-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a70d-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0a70d-139">Parent Elements</span></span>  
  
|<span data-ttu-id="0a70d-140">Element</span><span class="sxs-lookup"><span data-stu-id="0a70d-140">Element</span></span>|<span data-ttu-id="0a70d-141">Opis</span><span class="sxs-lookup"><span data-stu-id="0a70d-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a70d-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="0a70d-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="0a70d-143">Stosuje zasady odbicia do typu i wszystkich jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="0a70d-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="0a70d-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="0a70d-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="0a70d-145">Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="0a70d-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a70d-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a70d-146">Remarks</span></span>  
 <span data-ttu-id="0a70d-147">Jeśli zasady pola nie są jawnie zdefiniowane, dziedziczy zasad środowiska uruchomieniowego jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0a70d-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a70d-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a70d-148">See also</span></span>

- [<span data-ttu-id="0a70d-149">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0a70d-149">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="0a70d-150">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0a70d-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0a70d-151">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0a70d-151">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
