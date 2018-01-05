---
title: Element &lt;Field&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ef073004b213ee03ce9655096f612acb5750684
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfieldgt-element-net-native"></a><span data-ttu-id="03889-102">Element &lt;Field&gt; (architektura .NET Native)</span><span class="sxs-lookup"><span data-stu-id="03889-102">&lt;Field&gt; Element (.NET Native)</span></span>
<span data-ttu-id="03889-103">Zastosowanie zasad wykonywania odbicia do pola.</span><span class="sxs-lookup"><span data-stu-id="03889-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03889-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03889-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03889-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="03889-105">Attributes and Elements</span></span>  
 <span data-ttu-id="03889-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="03889-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03889-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="03889-107">Attributes</span></span>  
  
|<span data-ttu-id="03889-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="03889-108">Attribute</span></span>|<span data-ttu-id="03889-109">Typ atrybutu</span><span class="sxs-lookup"><span data-stu-id="03889-109">Attribute type</span></span>|<span data-ttu-id="03889-110">Opis</span><span class="sxs-lookup"><span data-stu-id="03889-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="03889-111">Ogólne</span><span class="sxs-lookup"><span data-stu-id="03889-111">General</span></span>|<span data-ttu-id="03889-112">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="03889-112">Required attribute.</span></span> <span data-ttu-id="03889-113">Określa nazwę pola.</span><span class="sxs-lookup"><span data-stu-id="03889-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="03889-114">Odbicie</span><span class="sxs-lookup"><span data-stu-id="03889-114">Reflection</span></span>|<span data-ttu-id="03889-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="03889-115">Optional attribute.</span></span> <span data-ttu-id="03889-116">Określa, czy wykonywania zapytania dotyczącego informacji o wyliczaniu pola, ale nie umożliwia dostępu dynamicznej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="03889-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="03889-117">Odbicie</span><span class="sxs-lookup"><span data-stu-id="03889-117">Reflection</span></span>|<span data-ttu-id="03889-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="03889-118">Optional attribute.</span></span> <span data-ttu-id="03889-119">Formanty środowiska uruchomieniowego dostępu do pola, aby włączyć dynamiczne programowania.</span><span class="sxs-lookup"><span data-stu-id="03889-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="03889-120">Ta zasada zapewnia, że pole można ustawić ani pobrać dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="03889-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="03889-121">Serializacja</span><span class="sxs-lookup"><span data-stu-id="03889-121">Serialization</span></span>|<span data-ttu-id="03889-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="03889-122">Optional attribute.</span></span> <span data-ttu-id="03889-123">Formanty środowiska uruchomieniowego dostępu do pola, aby włączyć wystąpień typów przez biblioteki, takich jak serializator Newtonsoft JSON lub do użycia dla powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="03889-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="03889-124">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="03889-124">Name attribute</span></span>  
  
|<span data-ttu-id="03889-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="03889-125">Value</span></span>|<span data-ttu-id="03889-126">Opis</span><span class="sxs-lookup"><span data-stu-id="03889-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="03889-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="03889-127">*method_name*</span></span>|<span data-ttu-id="03889-128">Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="03889-128">The field name.</span></span> <span data-ttu-id="03889-129">Typ pola jest określany przez element nadrzędny [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) lub [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="03889-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="03889-130">Inne atrybuty</span><span class="sxs-lookup"><span data-stu-id="03889-130">All other attributes</span></span>  
  
|<span data-ttu-id="03889-131">Wartość</span><span class="sxs-lookup"><span data-stu-id="03889-131">Value</span></span>|<span data-ttu-id="03889-132">Opis</span><span class="sxs-lookup"><span data-stu-id="03889-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="03889-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="03889-133">*policy_setting*</span></span>|<span data-ttu-id="03889-134">Ustawienia do zastosowania dla tego typu zasad dla pola.</span><span class="sxs-lookup"><span data-stu-id="03889-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="03889-135">Możliwe wartości to `Auto`, `Excluded`, `Included`, i `Required`.</span><span class="sxs-lookup"><span data-stu-id="03889-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="03889-136">Aby uzyskać więcej informacji, zobacz [ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="03889-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03889-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="03889-137">Child Elements</span></span>  
 <span data-ttu-id="03889-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="03889-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03889-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03889-139">Parent Elements</span></span>  
  
|<span data-ttu-id="03889-140">Element</span><span class="sxs-lookup"><span data-stu-id="03889-140">Element</span></span>|<span data-ttu-id="03889-141">Opis</span><span class="sxs-lookup"><span data-stu-id="03889-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03889-142">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="03889-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="03889-143">Stosuje odbicia zasady do typu i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="03889-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="03889-144">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="03889-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="03889-145">Stosuje zasady odbicia do skonstruowanego typu ogólnego i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="03889-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03889-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03889-146">Remarks</span></span>  
 <span data-ttu-id="03889-147">Jeśli zasady pola nie jest jawnie zdefiniowany, dziedziczy zasad wykonywania jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="03889-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03889-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03889-148">See Also</span></span>  
 [<span data-ttu-id="03889-149">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="03889-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="03889-150">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="03889-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="03889-151">Ustawienia zasad dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="03889-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
