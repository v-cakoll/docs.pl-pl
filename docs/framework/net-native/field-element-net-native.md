---
title: <Field> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58be27334bcb862367464475a4eade5e01bdbb2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221616"
---
# <a name="field-element-net-native"></a><span data-ttu-id="548e2-102">\<Pole > (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="548e2-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="548e2-103">Zastosowanie zasad odbicia środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="548e2-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="548e2-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="548e2-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="548e2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="548e2-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="548e2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="548e2-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="548e2-107">Attributes</span></span>  
  
|<span data-ttu-id="548e2-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="548e2-108">Attribute</span></span>|<span data-ttu-id="548e2-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="548e2-109">Attribute type</span></span>|<span data-ttu-id="548e2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="548e2-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="548e2-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="548e2-111">General</span></span>|<span data-ttu-id="548e2-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="548e2-112">Required attribute.</span></span> <span data-ttu-id="548e2-113">Określa nazwę pola.</span><span class="sxs-lookup"><span data-stu-id="548e2-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="548e2-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="548e2-114">Reflection</span></span>|<span data-ttu-id="548e2-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="548e2-115">Optional attribute.</span></span> <span data-ttu-id="548e2-116">Określa wykonanie zapytania dotyczącego informacji o wyliczanie pola, ale nie uwzględnia żadnych dostępu dynamicznego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="548e2-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="548e2-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="548e2-117">Reflection</span></span>|<span data-ttu-id="548e2-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="548e2-118">Optional attribute.</span></span> <span data-ttu-id="548e2-119">Dostęp do środowiska uruchomieniowego formanty do pola, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="548e2-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="548e2-120">Te zasady zapewniają, że pole można ustawić lub pobrać dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="548e2-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="548e2-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="548e2-121">Serialization</span></span>|<span data-ttu-id="548e2-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="548e2-122">Optional attribute.</span></span> <span data-ttu-id="548e2-123">Kontroluje dostęp do środowiska uruchomieniowego do pola, aby umożliwić wystąpień typu przez biblioteki, takie jak serializator Newtonsoft JSON lub ma być używany dla powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="548e2-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="548e2-124">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="548e2-124">Name attribute</span></span>  
  
|<span data-ttu-id="548e2-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="548e2-125">Value</span></span>|<span data-ttu-id="548e2-126">Opis</span><span class="sxs-lookup"><span data-stu-id="548e2-126">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="548e2-127">method_name</span><span class="sxs-lookup"><span data-stu-id="548e2-127">method_name</span></span>*|<span data-ttu-id="548e2-128">Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="548e2-128">The field name.</span></span> <span data-ttu-id="548e2-129">Typ pola jest definiowany przez nadrzędne [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="548e2-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="548e2-130">Wszystkie inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="548e2-130">All other attributes</span></span>  
  
|<span data-ttu-id="548e2-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="548e2-131">Value</span></span>|<span data-ttu-id="548e2-132">Opis</span><span class="sxs-lookup"><span data-stu-id="548e2-132">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="548e2-133">policy_setting</span><span class="sxs-lookup"><span data-stu-id="548e2-133">policy_setting</span></span>*|<span data-ttu-id="548e2-134">Ustawienia do zastosowania do tego typu zasad dla pola.</span><span class="sxs-lookup"><span data-stu-id="548e2-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="548e2-135">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="548e2-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="548e2-136">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="548e2-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="548e2-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="548e2-137">Child Elements</span></span>  
 <span data-ttu-id="548e2-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="548e2-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="548e2-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="548e2-139">Parent Elements</span></span>  
  
|<span data-ttu-id="548e2-140">Element</span><span class="sxs-lookup"><span data-stu-id="548e2-140">Element</span></span>|<span data-ttu-id="548e2-141">Opis</span><span class="sxs-lookup"><span data-stu-id="548e2-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="548e2-142">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="548e2-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="548e2-143">Ma zastosowanie zasad odbicia do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="548e2-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="548e2-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="548e2-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="548e2-145">Ma zastosowanie zasad odbicia do skonstruowany typ rodzajowy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="548e2-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="548e2-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="548e2-146">Remarks</span></span>  
 <span data-ttu-id="548e2-147">Jeśli zasady dotyczące pól nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania odpowiedniego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="548e2-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548e2-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="548e2-148">See also</span></span>

- [<span data-ttu-id="548e2-149">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="548e2-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="548e2-150">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="548e2-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="548e2-151">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="548e2-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
