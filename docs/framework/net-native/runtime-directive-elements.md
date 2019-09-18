---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049274"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="49b56-102">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="49b56-102">Runtime Directive Elements</span></span>
<span data-ttu-id="49b56-103">Format pliku dyrektyw środowiska uruchomieniowego (RD. xml) obsługuje następujące elementy dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="49b56-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="49b56-104">Zobacz sekcję [dyrektywy środowiska uruchomieniowego informacje o pliku konfiguracyjnym](runtime-directives-rd-xml-configuration-file-reference.md) dla reprezentacji hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="49b56-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="49b56-105">\<> Aplikacji</span><span class="sxs-lookup"><span data-stu-id="49b56-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="49b56-106">Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów używanych przez aplikację i służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="49b56-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="49b56-107">Jest to element podrzędny [ \<dyrektyw >](directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="49b56-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="49b56-108">\<> Zestawu</span><span class="sxs-lookup"><span data-stu-id="49b56-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="49b56-109">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="49b56-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="49b56-110">Jest to element podrzędny [ \<> aplikacji](application-element-net-native.md) i [ \<biblioteki >](library-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="49b56-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-111">\<AttributeImplies ></span><span class="sxs-lookup"><span data-stu-id="49b56-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="49b56-112">Jeśli typ zawierający [ \<>](type-element-net-native.md) dyrektywie jest atrybut, stosuje zasady środowiska uruchomieniowego do elementów kodu, do których ten atrybut jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="49b56-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="49b56-113">\<Dyrektywy ></span><span class="sxs-lookup"><span data-stu-id="49b56-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="49b56-114">Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49b56-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="49b56-115">Jego elementami podrzędnymi są [ \<> aplikacji](application-element-net-native.md) i [ \<> biblioteki](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="49b56-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="49b56-116">\<> Zdarzeń</span><span class="sxs-lookup"><span data-stu-id="49b56-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="49b56-117">Stosuje zasady środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="49b56-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="49b56-118">Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="49b56-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-119">\<> Pola</span><span class="sxs-lookup"><span data-stu-id="49b56-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="49b56-120">Stosuje zasady środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="49b56-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="49b56-121">Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="49b56-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="49b56-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="49b56-123">Stosuje zasady środowiska uruchomieniowego do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="49b56-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="49b56-124">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="49b56-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="49b56-125">Stosuje zasady środowiska uruchomieniowego do typu, jeśli te zasady zostały zastosowane do zawierającego go typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="49b56-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="49b56-126">\<> Biblioteki</span><span class="sxs-lookup"><span data-stu-id="49b56-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="49b56-127">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="49b56-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="49b56-128">Jest to element podrzędny [ \<> aplikacji](application-element-net-native.md) i [ \<biblioteki >](library-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="49b56-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-129">\<> Metody</span><span class="sxs-lookup"><span data-stu-id="49b56-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="49b56-130">Stosuje zasady środowiska uruchomieniowego do metody.</span><span class="sxs-lookup"><span data-stu-id="49b56-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="49b56-131">Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="49b56-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-132">\<MethodInstantiation ></span><span class="sxs-lookup"><span data-stu-id="49b56-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="49b56-133">Stosuje zasady środowiska uruchomieniowego do skonstruowanej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="49b56-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="49b56-134">Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="49b56-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="49b56-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="49b56-136">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="49b56-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="49b56-137">\<> Parametru</span><span class="sxs-lookup"><span data-stu-id="49b56-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="49b56-138">Stosuje zasady środowiska uruchomieniowego do typu argumentu przesłanego do metody.</span><span class="sxs-lookup"><span data-stu-id="49b56-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="49b56-139">\<> Właściwości</span><span class="sxs-lookup"><span data-stu-id="49b56-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="49b56-140">Stosuje zasady środowiska uruchomieniowego do właściwości.</span><span class="sxs-lookup"><span data-stu-id="49b56-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="49b56-141">Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="49b56-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="49b56-142">\<Podtypy ></span><span class="sxs-lookup"><span data-stu-id="49b56-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="49b56-143">Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="49b56-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="49b56-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="49b56-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="49b56-145">Stosuje zasady środowiska uruchomieniowego do typu.</span><span class="sxs-lookup"><span data-stu-id="49b56-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="49b56-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="49b56-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="49b56-147">Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="49b56-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="49b56-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="49b56-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="49b56-149">Stosuje zasady środowiska uruchomieniowego do typu reprezentowanego <xref:System.Type> przez argument przesłany do metody.</span><span class="sxs-lookup"><span data-stu-id="49b56-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b56-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49b56-150">See also</span></span>

- [<span data-ttu-id="49b56-151">Dokumentacja pliku konfiguracji usług Rd. XML</span><span class="sxs-lookup"><span data-stu-id="49b56-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
