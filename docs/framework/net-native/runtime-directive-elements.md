---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128167"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="6fd67-102">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6fd67-102">Runtime Directive Elements</span></span>
<span data-ttu-id="6fd67-103">Format pliku dyrektyw środowiska uruchomieniowego (RD. xml) obsługuje następujące elementy dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6fd67-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="6fd67-104">Zobacz sekcję [dyrektywy środowiska uruchomieniowego informacje o pliku konfiguracyjnym](runtime-directives-rd-xml-configuration-file-reference.md) dla reprezentacji hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="6fd67-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="6fd67-105">\<> aplikacji</span><span class="sxs-lookup"><span data-stu-id="6fd67-105">\<Application></span></span>](application-element-net-native.md)  
 <span data-ttu-id="6fd67-106">Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów używanych przez aplikację i służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6fd67-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="6fd67-107">Jest to element podrzędny [> dyrektywy\<](directives-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6fd67-107">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="6fd67-108">\<zestawu ></span><span class="sxs-lookup"><span data-stu-id="6fd67-108">\<Assembly></span></span>](assembly-element-net-native.md)  
 <span data-ttu-id="6fd67-109">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="6fd67-109">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="6fd67-110">Jest to element podrzędny [\<> aplikacji](application-element-net-native.md) i [biblioteki\<](library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-110">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-111">\<AttributeImplies ></span><span class="sxs-lookup"><span data-stu-id="6fd67-111">\<AttributeImplies></span></span>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="6fd67-112">Jeśli > dyrektywy zawierającej [typ\<](type-element-net-native.md) jest atrybut, stosuje zasady środowiska uruchomieniowego do elementów kodu, do których ten atrybut jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="6fd67-112">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="6fd67-113">Dyrektywy \<</span><span class="sxs-lookup"><span data-stu-id="6fd67-113">\<Directives></span></span>](directives-element-net-native.md)  
 <span data-ttu-id="6fd67-114">Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6fd67-114">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="6fd67-115">Jego elementy podrzędne są [\<> aplikacji](application-element-net-native.md) i [biblioteki\<](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="6fd67-115">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="6fd67-116">> zdarzeń \<</span><span class="sxs-lookup"><span data-stu-id="6fd67-116">\<Event></span></span>](event-element-net-native.md)  
 <span data-ttu-id="6fd67-117">Stosuje zasady środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6fd67-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="6fd67-118">Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-118">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-119">\<pole ></span><span class="sxs-lookup"><span data-stu-id="6fd67-119">\<Field></span></span>](field-element-net-native.md)  
 <span data-ttu-id="6fd67-120">Stosuje zasady środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="6fd67-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="6fd67-121">Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="6fd67-122">\<GenericParameter></span></span>](genericparameter-element-net-native.md)  
 <span data-ttu-id="6fd67-123">Stosuje zasady środowiska uruchomieniowego do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="6fd67-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="6fd67-124">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="6fd67-124">\<ImpliesType></span></span>](impliestype-element-net-native.md)  
 <span data-ttu-id="6fd67-125">Stosuje zasady środowiska uruchomieniowego do typu, jeśli te zasady zostały zastosowane do zawierającego go typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="6fd67-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="6fd67-126">Biblioteka \<</span><span class="sxs-lookup"><span data-stu-id="6fd67-126">\<Library></span></span>](library-element-net-native.md)  
 <span data-ttu-id="6fd67-127">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="6fd67-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="6fd67-128">Jest to element podrzędny [\<> aplikacji](application-element-net-native.md) i [biblioteki\<](library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-128">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-129">> metody\<</span><span class="sxs-lookup"><span data-stu-id="6fd67-129">\<Method></span></span>](method-element-net-native.md)  
 <span data-ttu-id="6fd67-130">Stosuje zasady środowiska uruchomieniowego do metody.</span><span class="sxs-lookup"><span data-stu-id="6fd67-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="6fd67-131">Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-131">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-132">\<MethodInstantiation ></span><span class="sxs-lookup"><span data-stu-id="6fd67-132">\<MethodInstantiation></span></span>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="6fd67-133">Stosuje zasady środowiska uruchomieniowego do skonstruowanej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="6fd67-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="6fd67-134">Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-134">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-135">\<przestrzeni nazw ></span><span class="sxs-lookup"><span data-stu-id="6fd67-135">\<Namespace></span></span>](namespace-element-net-native.md)  
 <span data-ttu-id="6fd67-136">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fd67-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="6fd67-137">\<parametr ></span><span class="sxs-lookup"><span data-stu-id="6fd67-137">\<Parameter></span></span>](parameter-element-net-native.md)  
 <span data-ttu-id="6fd67-138">Stosuje zasady środowiska uruchomieniowego do typu argumentu przesłanego do metody.</span><span class="sxs-lookup"><span data-stu-id="6fd67-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="6fd67-139">\<Właściwość ></span><span class="sxs-lookup"><span data-stu-id="6fd67-139">\<Property></span></span>](property-element-net-native.md)  
 <span data-ttu-id="6fd67-140">Stosuje zasady środowiska uruchomieniowego do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fd67-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="6fd67-141">Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="6fd67-141">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="6fd67-142">podtypy \<</span><span class="sxs-lookup"><span data-stu-id="6fd67-142">\<Subtypes></span></span>](subtypes-element-net-native.md)  
 <span data-ttu-id="6fd67-143">Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="6fd67-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="6fd67-144">Typ\<</span><span class="sxs-lookup"><span data-stu-id="6fd67-144">\<Type></span></span>](type-element-net-native.md)  
 <span data-ttu-id="6fd67-145">Stosuje zasady środowiska uruchomieniowego do typu.</span><span class="sxs-lookup"><span data-stu-id="6fd67-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="6fd67-146">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="6fd67-146">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="6fd67-147">Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6fd67-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="6fd67-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="6fd67-148">\<TypeParameter></span></span>](typeparameter-element-net-native.md)  
 <span data-ttu-id="6fd67-149">Stosuje zasady środowiska uruchomieniowego do typu reprezentowanego przez argument <xref:System.Type> przekazaną do metody.</span><span class="sxs-lookup"><span data-stu-id="6fd67-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd67-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fd67-150">See also</span></span>

- [<span data-ttu-id="6fd67-151">Dokumentacja pliku konfiguracji usług Rd. XML</span><span class="sxs-lookup"><span data-stu-id="6fd67-151">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
