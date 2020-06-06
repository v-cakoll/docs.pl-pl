---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128167"
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="fa8a8-102">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fa8a8-102">Runtime Directive Elements</span></span>
<span data-ttu-id="fa8a8-103">Format pliku dyrektyw środowiska uruchomieniowego (RD. xml) obsługuje następujące elementy dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="fa8a8-104">Zobacz sekcję [dyrektywy środowiska uruchomieniowego informacje o pliku konfiguracyjnym](runtime-directives-rd-xml-configuration-file-reference.md) dla reprezentacji hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-104">See [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [\<Application>](application-element-net-native.md)  
 <span data-ttu-id="fa8a8-105">Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów używanych przez aplikację i służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-105">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="fa8a8-106">Jest to element podrzędny [\<Directives>](directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-106">This is a child of the [\<Directives>](directives-element-net-native.md) element.</span></span>  
  
 [\<Assembly>](assembly-element-net-native.md)  
 <span data-ttu-id="fa8a8-107">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-107">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="fa8a8-108">Jest to element podrzędny [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-108">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 <span data-ttu-id="fa8a8-109">Jeśli jego dyrektywa zawierająca [\<Type>](type-element-net-native.md) jest atrybutem, stosuje zasady środowiska uruchomieniowego do elementów kodu, do których ten atrybut jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-109">If its containing [\<Type>](type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [\<Directives>](directives-element-net-native.md)  
 <span data-ttu-id="fa8a8-110">Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-110">The root element in every runtime directives file for .NET Native.</span></span> <span data-ttu-id="fa8a8-111">Jego elementy podrzędne są [\<Application>](application-element-net-native.md) i [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="fa8a8-111">Its child elements are [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md).</span></span>  
  
 [\<Event>](event-element-net-native.md)  
 <span data-ttu-id="fa8a8-112">Stosuje zasady środowiska uruchomieniowego do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-112">Applies runtime policy to an event.</span></span> <span data-ttu-id="fa8a8-113">Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-113">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Field>](field-element-net-native.md)  
 <span data-ttu-id="fa8a8-114">Stosuje zasady środowiska uruchomieniowego do pola.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-114">Applies runtime policy to a field.</span></span> <span data-ttu-id="fa8a8-115">Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-115">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 <span data-ttu-id="fa8a8-116">Stosuje zasady środowiska uruchomieniowego do typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-116">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 <span data-ttu-id="fa8a8-117">Stosuje zasady środowiska uruchomieniowego do typu, jeśli te zasady zostały zastosowane do zawierającego go typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-117">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [\<Library>](library-element-net-native.md)  
 <span data-ttu-id="fa8a8-118">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-118">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="fa8a8-119">Jest to element podrzędny [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-119">This is a child of the [\<Application>](application-element-net-native.md) and [\<Library>](library-element-net-native.md) elements.</span></span>  
  
 [\<Method>](method-element-net-native.md)  
 <span data-ttu-id="fa8a8-120">Stosuje zasady środowiska uruchomieniowego do metody.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-120">Applies runtime policy to a method.</span></span> <span data-ttu-id="fa8a8-121">Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-121">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 <span data-ttu-id="fa8a8-122">Stosuje zasady środowiska uruchomieniowego do skonstruowanej metody ogólnej.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-122">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="fa8a8-123">Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-123">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Namespace>](namespace-element-net-native.md)  
 <span data-ttu-id="fa8a8-124">Stosuje zasady środowiska uruchomieniowego do wszystkich typów w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-124">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [\<Parameter>](parameter-element-net-native.md)  
 <span data-ttu-id="fa8a8-125">Stosuje zasady środowiska uruchomieniowego do typu argumentu przesłanego do metody.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-125">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [\<Property>](property-element-net-native.md)  
 <span data-ttu-id="fa8a8-126">Stosuje zasady środowiska uruchomieniowego do właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-126">Applies runtime policy to a property.</span></span> <span data-ttu-id="fa8a8-127">Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-127">This is a child of the [\<Type>](type-element-net-native.md) and [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 <span data-ttu-id="fa8a8-128">Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-128">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [\<Type>](type-element-net-native.md)  
 <span data-ttu-id="fa8a8-129">Stosuje zasady środowiska uruchomieniowego do typu.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-129">Applies runtime policy to a type.</span></span>  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 <span data-ttu-id="fa8a8-130">Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-130">Applies runtime policy to a constructed generic type.</span></span>  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 <span data-ttu-id="fa8a8-131">Stosuje zasady środowiska uruchomieniowego do typu reprezentowanego przez <xref:System.Type> argument przesłany do metody.</span><span class="sxs-lookup"><span data-stu-id="fa8a8-131">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8a8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa8a8-132">See also</span></span>

- [<span data-ttu-id="fa8a8-133">Dokumentacja pliku konfiguracji usług Rd. XML</span><span class="sxs-lookup"><span data-stu-id="fa8a8-133">rd.xml Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
