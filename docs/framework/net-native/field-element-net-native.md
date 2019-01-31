---
title: <Field> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4a062e060e7b367f0d56b3633238de74ae8ed88
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281674"
---
# <a name="field-element-net-native"></a><span data-ttu-id="6fa69-102">\<Pole > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="6fa69-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="6fa69-103">Zastosowanie zasad odbicia środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="6fa69-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fa69-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fa69-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6fa69-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6fa69-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fa69-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fa69-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6fa69-107">Attributes</span></span>  
  
|<span data-ttu-id="6fa69-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6fa69-108">Attribute</span></span>|<span data-ttu-id="6fa69-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="6fa69-109">Attribute type</span></span>|<span data-ttu-id="6fa69-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa69-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6fa69-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="6fa69-111">General</span></span>|<span data-ttu-id="6fa69-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6fa69-112">Required attribute.</span></span> <span data-ttu-id="6fa69-113">Określa nazwę pola.</span><span class="sxs-lookup"><span data-stu-id="6fa69-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="6fa69-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6fa69-114">Reflection</span></span>|<span data-ttu-id="6fa69-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6fa69-115">Optional attribute.</span></span> <span data-ttu-id="6fa69-116">Określa wykonanie zapytania dotyczącego informacji o wyliczanie pola, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6fa69-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="6fa69-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="6fa69-117">Reflection</span></span>|<span data-ttu-id="6fa69-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6fa69-118">Optional attribute.</span></span> <span data-ttu-id="6fa69-119">Dostęp do środowiska uruchomieniowego formanty do pola, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="6fa69-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="6fa69-120">Te zasady zapewniają, że pole można ustawić lub pobrać dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6fa69-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="6fa69-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="6fa69-121">Serialization</span></span>|<span data-ttu-id="6fa69-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6fa69-122">Optional attribute.</span></span> <span data-ttu-id="6fa69-123">Kontroluje dostęp do środowiska uruchomieniowego do pola, aby umożliwić wystąpień typu przez biblioteki, takie jak serializator Newtonsoft JSON lub ma być używany dla powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="6fa69-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6fa69-124">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="6fa69-124">Name attribute</span></span>  
  
|<span data-ttu-id="6fa69-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="6fa69-125">Value</span></span>|<span data-ttu-id="6fa69-126">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa69-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6fa69-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="6fa69-127">*method_name*</span></span>|<span data-ttu-id="6fa69-128">Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="6fa69-128">The field name.</span></span> <span data-ttu-id="6fa69-129">Typ pola jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6fa69-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6fa69-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="6fa69-130">All other attributes</span></span>  
  
|<span data-ttu-id="6fa69-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="6fa69-131">Value</span></span>|<span data-ttu-id="6fa69-132">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa69-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6fa69-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6fa69-133">*policy_setting*</span></span>|<span data-ttu-id="6fa69-134">Ustawienia do zastosowania do tego typu zasad dla pola.</span><span class="sxs-lookup"><span data-stu-id="6fa69-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="6fa69-135">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="6fa69-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="6fa69-136">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6fa69-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fa69-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6fa69-137">Child Elements</span></span>  
 <span data-ttu-id="6fa69-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="6fa69-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fa69-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6fa69-139">Parent Elements</span></span>  
  
|<span data-ttu-id="6fa69-140">Element</span><span class="sxs-lookup"><span data-stu-id="6fa69-140">Element</span></span>|<span data-ttu-id="6fa69-141">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa69-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fa69-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="6fa69-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6fa69-143">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6fa69-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="6fa69-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="6fa69-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="6fa69-145">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6fa69-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa69-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fa69-146">Remarks</span></span>  
 <span data-ttu-id="6fa69-147">Jeśli zasady dotyczące pól nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania odpowiedniego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6fa69-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa69-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fa69-148">See also</span></span>
- [<span data-ttu-id="6fa69-149">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6fa69-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="6fa69-150">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6fa69-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6fa69-151">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6fa69-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
