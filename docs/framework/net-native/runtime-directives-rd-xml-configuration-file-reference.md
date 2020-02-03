---
title: Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738408"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="09a0a-102">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="09a0a-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="09a0a-103">Plik dyrektywy środowiska uruchomieniowego (. Rd. xml) jest plikiem konfiguracji XML, który określa, czy wyszukane elementy programu są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="09a0a-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="09a0a-104">Oto przykład pliku dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="09a0a-104">Here’s an example of a runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
    <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
    <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
    <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

    <Namespace Name="System.Collections.ObjectModel" >
      <TypeInstantiation Name="ObservableCollection"
            Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
      <TypeInstantiation Name="ReadOnlyObservableCollection"
            Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
    </Namespace>
  </Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="09a0a-105">Struktura pliku dyrektywy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="09a0a-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="09a0a-106">Plik dyrektywy środowiska uruchomieniowego używa przestrzeni nazw `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="09a0a-107">Elementem głównym jest element [dyrektywy](directives-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="09a0a-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="09a0a-108">Może zawierać zero lub więcej elementów [biblioteki](library-element-net-native.md) oraz zero lub jeden element [aplikacji](application-element-net-native.md) , jak pokazano w poniższej strukturze.</span><span class="sxs-lookup"><span data-stu-id="09a0a-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="09a0a-109">Atrybuty elementu [aplikacji](application-element-net-native.md) mogą definiować zasady odbicia w środowisku uruchomieniowym dla całej aplikacji lub mogą one stanowić kontener dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="09a0a-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="09a0a-110">Element [biblioteki](library-element-net-native.md) , z drugiej strony, jest po prostu kontenerem.</span><span class="sxs-lookup"><span data-stu-id="09a0a-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="09a0a-111">Elementy podrzędne [aplikacji](application-element-net-native.md) i [biblioteki](library-element-net-native.md) definiują typy, metody, pola, właściwości i zdarzenia, które są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="09a0a-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="09a0a-112">Aby uzyskać informacje referencyjne, wybierz elementy z następującej struktury lub zobacz [elementy dyrektywy środowiska uruchomieniowego](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="09a0a-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="09a0a-113">W poniższej hierarchii wielokropek oznacza strukturę cykliczną.</span><span class="sxs-lookup"><span data-stu-id="09a0a-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="09a0a-114">Informacje w nawiasach wskazują, czy ten element jest opcjonalny, czy wymagany, a jeśli jest używany, ile wystąpień (jeden lub wiele) jest dozwolonych.</span><span class="sxs-lookup"><span data-stu-id="09a0a-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="09a0a-115">[Dyrektywy](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="09a0a-115">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="09a0a-116">[Aplikacja](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="09a0a-116">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="09a0a-117">[Zestaw](assembly-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-117">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-118">[Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-118">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-119">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-119">.</span></span> <span data-ttu-id="09a0a-120">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-120">.</span></span>
      - <span data-ttu-id="09a0a-121">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-121">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-122">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-122">.</span></span> <span data-ttu-id="09a0a-123">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-123">.</span></span>
      - <span data-ttu-id="09a0a-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-125">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-125">.</span></span> <span data-ttu-id="09a0a-126">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-126">.</span></span>
    - <span data-ttu-id="09a0a-127">[Przestrzeń nazw](namespace-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-127">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-128">[Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-128">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-129">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-129">.</span></span> <span data-ttu-id="09a0a-130">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-130">.</span></span>
      - <span data-ttu-id="09a0a-131">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-131">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-132">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-132">.</span></span> <span data-ttu-id="09a0a-133">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-133">.</span></span>
      - <span data-ttu-id="09a0a-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-135">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-135">.</span></span> <span data-ttu-id="09a0a-136">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-136">.</span></span>
    - <span data-ttu-id="09a0a-137">[Typ](type-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-137">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-138">[Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1]</span><span class="sxs-lookup"><span data-stu-id="09a0a-138">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="09a0a-139">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-139">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-140">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-140">.</span></span> <span data-ttu-id="09a0a-141">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-141">.</span></span>
      - <span data-ttu-id="09a0a-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-143">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-143">.</span></span> <span data-ttu-id="09a0a-144">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-144">.</span></span>
      - <span data-ttu-id="09a0a-145">[AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1]</span><span class="sxs-lookup"><span data-stu-id="09a0a-145">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="09a0a-146">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-147">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-147">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="09a0a-148">[Parametr](parameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-148">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="09a0a-149">[TypeParameter](typeparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="09a0a-150">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="09a0a-152">[Właściwość](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-152">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-153">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-153">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-154">[Zdarzenie](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-154">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="09a0a-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="09a0a-156">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-156">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-157">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-157">.</span></span> <span data-ttu-id="09a0a-158">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-158">.</span></span>
      - <span data-ttu-id="09a0a-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-160">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-160">.</span></span> <span data-ttu-id="09a0a-161">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-161">.</span></span>
      - <span data-ttu-id="09a0a-162">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-162">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="09a0a-163">[Parametr](parameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-163">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="09a0a-164">[TypeParameter](typeparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="09a0a-165">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="09a0a-167">[Właściwość](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-167">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-168">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-168">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-169">[Zdarzenie](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-169">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="09a0a-170">[Biblioteka](library-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-170">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="09a0a-171">[Zestaw](assembly-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-171">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-172">[Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-172">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-173">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-173">.</span></span> <span data-ttu-id="09a0a-174">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-174">.</span></span>
      - <span data-ttu-id="09a0a-175">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-175">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-176">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-176">.</span></span> <span data-ttu-id="09a0a-177">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-177">.</span></span>
      - <span data-ttu-id="09a0a-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-179">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-179">.</span></span> <span data-ttu-id="09a0a-180">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-180">.</span></span>
    - <span data-ttu-id="09a0a-181">[Przestrzeń nazw](namespace-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-181">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-182">[Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-182">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-183">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-183">.</span></span> <span data-ttu-id="09a0a-184">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-184">.</span></span>
      - <span data-ttu-id="09a0a-185">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-185">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-186">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-186">.</span></span> <span data-ttu-id="09a0a-187">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-187">.</span></span>
      - <span data-ttu-id="09a0a-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-189">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-189">.</span></span> <span data-ttu-id="09a0a-190">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-190">.</span></span>
    - <span data-ttu-id="09a0a-191">[Typ](type-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-191">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-192">[Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1]</span><span class="sxs-lookup"><span data-stu-id="09a0a-192">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="09a0a-193">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-193">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-194">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-194">.</span></span> <span data-ttu-id="09a0a-195">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-195">.</span></span>
      - <span data-ttu-id="09a0a-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-197">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-197">.</span></span> <span data-ttu-id="09a0a-198">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-198">.</span></span>
      - <span data-ttu-id="09a0a-199">[AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1]</span><span class="sxs-lookup"><span data-stu-id="09a0a-199">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="09a0a-200">[GenericParameter](genericparameter-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-201">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-201">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="09a0a-203">[Właściwość](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-203">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-204">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-204">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-205">[Zdarzenie](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-205">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="09a0a-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="09a0a-207">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-207">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="09a0a-208">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-208">.</span></span> <span data-ttu-id="09a0a-209">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-209">.</span></span>
      - <span data-ttu-id="09a0a-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="09a0a-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="09a0a-211">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-211">.</span></span> <span data-ttu-id="09a0a-212">.</span><span class="sxs-lookup"><span data-stu-id="09a0a-212">.</span></span>
      - <span data-ttu-id="09a0a-213">[Metoda](method-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-213">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="09a0a-215">[Właściwość](property-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-215">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-216">[Pole](field-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-216">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="09a0a-217">[Zdarzenie](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="09a0a-217">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="09a0a-218">Element [aplikacji](application-element-net-native.md) nie może mieć żadnych atrybutów lub atrybuty zasad mogą być omówione w [sekcji dyrektywy i zasad środowiska uruchomieniowego](#Directives).</span><span class="sxs-lookup"><span data-stu-id="09a0a-218">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="09a0a-219">Element [biblioteki](library-element-net-native.md) ma jeden atrybut, `Name`, który określa nazwę biblioteki lub zestawu, bez rozszerzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="09a0a-219">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="09a0a-220">Na przykład poniższy element [biblioteki](library-element-net-native.md) ma zastosowanie do zestawu o nazwie Extensions. dll.</span><span class="sxs-lookup"><span data-stu-id="09a0a-220">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="09a0a-221">Dyrektywy i zasady środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="09a0a-221">Runtime directives and policy</span></span>

<span data-ttu-id="09a0a-222">Sam element [aplikacji](application-element-net-native.md) i elementy podrzędne [biblioteki](library-element-net-native.md) i elementów [aplikacji](application-element-net-native.md) Express Policy; oznacza to, że definiują sposób, w jaki aplikacja może zastosować odbicie do elementu programu.</span><span class="sxs-lookup"><span data-stu-id="09a0a-222">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="09a0a-223">Typ zasad jest definiowany przez atrybut elementu (na przykład `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="09a0a-223">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="09a0a-224">Wartość zasad jest definiowana przez wartość atrybutu (na przykład `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="09a0a-224">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="09a0a-225">Wszelkie zasady określone przez atrybut elementu mają zastosowanie do wszystkich elementów podrzędnych, które nie określają wartości dla tych zasad.</span><span class="sxs-lookup"><span data-stu-id="09a0a-225">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="09a0a-226">Na przykład jeśli zasady są określone przez element [typu](type-element-net-native.md) , te zasady mają zastosowanie do wszystkich typów i elementów członkowskich, dla których zasady nie są jawnie określone.</span><span class="sxs-lookup"><span data-stu-id="09a0a-226">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="09a0a-227">Zasady, które mogą być wyrażone przez [aplikację](application-element-net-native.md), [zestaw](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [przestrzeń nazw](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)i elementy [typu](type-element-net-native.md) , różnią się od zasad, które mogą być wyrażone dla poszczególnych członków (przez [metodę](method-element-net-native.md), [Właściwość](property-element-net-native.md), [pole](field-element-net-native.md)i elementy [zdarzenia](event-element-net-native.md) ).</span><span class="sxs-lookup"><span data-stu-id="09a0a-227">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="09a0a-228">Określanie zasad dla zestawów, przestrzeni nazw i typów</span><span class="sxs-lookup"><span data-stu-id="09a0a-228">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="09a0a-229">Elementy [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [podtyp](subtypes-element-net-native.md)i [Type](type-element-net-native.md) obsługują następujące typy zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-229">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="09a0a-230">`Activate`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-230">`Activate`.</span></span> <span data-ttu-id="09a0a-231">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="09a0a-231">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="09a0a-232">`Browse`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-232">`Browse`.</span></span> <span data-ttu-id="09a0a-233">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-233">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="09a0a-234">`Dynamic`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-234">`Dynamic`.</span></span> <span data-ttu-id="09a0a-235">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="09a0a-235">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="09a0a-236">`Serialize`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-236">`Serialize`.</span></span> <span data-ttu-id="09a0a-237">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i Serializowanie wystąpień typu przez biblioteki innych firm, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="09a0a-237">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="09a0a-238">`DataContractSerializer`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-238">`DataContractSerializer`.</span></span> <span data-ttu-id="09a0a-239">Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09a0a-239">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="09a0a-240">`DataContractJsonSerializer`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-240">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="09a0a-241">Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09a0a-241">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="09a0a-242">`XmlSerializer`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-242">`XmlSerializer`.</span></span> <span data-ttu-id="09a0a-243">Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09a0a-243">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="09a0a-244">`MarshalObject`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-244">`MarshalObject`.</span></span> <span data-ttu-id="09a0a-245">Kontroluje zasady dotyczące organizowania typów odwołań do WinRT i COM.</span><span class="sxs-lookup"><span data-stu-id="09a0a-245">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="09a0a-246">`MarshalDelegate`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-246">`MarshalDelegate`.</span></span> <span data-ttu-id="09a0a-247">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-247">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="09a0a-248">`MarshalStructure`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-248">`MarshalStructure` .</span></span> <span data-ttu-id="09a0a-249">Steruje zasadami organizowania struktur w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="09a0a-249">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="09a0a-250">Ustawienia skojarzone z tymi typami zasad są następujące:</span><span class="sxs-lookup"><span data-stu-id="09a0a-250">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="09a0a-251">`All`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-251">`All`.</span></span> <span data-ttu-id="09a0a-252">Włącz zasady dla wszystkich typów i elementów członkowskich, które nie są usuwane przez łańcuch narzędzi.</span><span class="sxs-lookup"><span data-stu-id="09a0a-252">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="09a0a-253">`Auto`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-253">`Auto`.</span></span> <span data-ttu-id="09a0a-254">Użyj zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-254">Use the default behavior.</span></span> <span data-ttu-id="09a0a-255">(Nieokreślanie zasad jest równoznaczne z ustawieniem zasad do `Auto`, chyba że te zasady zostaną zastąpione, na przykład przez element nadrzędny).</span><span class="sxs-lookup"><span data-stu-id="09a0a-255">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="09a0a-256">`Excluded`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-256">`Excluded`.</span></span> <span data-ttu-id="09a0a-257">Wyłącz zasady dla elementu program.</span><span class="sxs-lookup"><span data-stu-id="09a0a-257">Disable the policy for the program element.</span></span>

- <span data-ttu-id="09a0a-258">`Public`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-258">`Public`.</span></span> <span data-ttu-id="09a0a-259">Włącz zasady dla typów publicznych lub członków, chyba że łańcuch narzędzi nie ustali, że element członkowski jest niepotrzebny i usuwa go.</span><span class="sxs-lookup"><span data-stu-id="09a0a-259">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="09a0a-260">(W tym drugim przypadku należy użyć `Required Public`, aby upewnić się, że element członkowski jest przechowywany i ma możliwości odbicia).</span><span class="sxs-lookup"><span data-stu-id="09a0a-260">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="09a0a-261">`PublicAndInternal`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-261">`PublicAndInternal`.</span></span> <span data-ttu-id="09a0a-262">Włącz zasady dla typów publicznych i wewnętrznych lub członków, jeśli łańcuch narzędzi nie zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="09a0a-262">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="09a0a-263">`Required Public`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-263">`Required Public`.</span></span> <span data-ttu-id="09a0a-264">Należy wymagać łańcucha narzędzi, aby zachować publiczne typy i członków, niezależnie od tego, czy są one używane, i włączyć dla nich zasady.</span><span class="sxs-lookup"><span data-stu-id="09a0a-264">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="09a0a-265">`Required PublicAndInternal`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-265">`Required PublicAndInternal`.</span></span> <span data-ttu-id="09a0a-266">Wymagaj, aby łańcuch narzędzi zachował typy publiczne i wewnętrzne oraz członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.</span><span class="sxs-lookup"><span data-stu-id="09a0a-266">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="09a0a-267">`Required All`.,</span><span class="sxs-lookup"><span data-stu-id="09a0a-267">`Required All`.</span></span> <span data-ttu-id="09a0a-268">Wymagaj łańcucha narzędzi, aby zachować wszystkie typy i członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.</span><span class="sxs-lookup"><span data-stu-id="09a0a-268">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="09a0a-269">Na przykład następujące pliki dyrektywy środowiska uruchomieniowego definiują zasady dla wszystkich typów i elementów członkowskich w zestawie DataClasses. dll.</span><span class="sxs-lookup"><span data-stu-id="09a0a-269">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="09a0a-270">Umożliwia odbicie dla serializacji wszystkich właściwości publicznych, umożliwia przeglądanie dla wszystkich typów i elementów członkowskich typu, umożliwia aktywację dla wszystkich typów (z powodu `Dynamic` atrybutu) i umożliwia odbicie dla wszystkich typów i członków publicznych.</span><span class="sxs-lookup"><span data-stu-id="09a0a-270">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a><span data-ttu-id="09a0a-271">Określanie zasad dla członków</span><span class="sxs-lookup"><span data-stu-id="09a0a-271">Specifying policy for members</span></span>

<span data-ttu-id="09a0a-272">Elementy [Właściwości](property-element-net-native.md) i [pól](field-element-net-native.md) obsługują następujące typy zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-272">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="09a0a-273">`Browse`-kontroluje wykonywanie zapytań dotyczących informacji o tym elemencie członkowskim, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-273">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="09a0a-274">`Dynamic` — kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="09a0a-274">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="09a0a-275">Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="09a0a-275">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="09a0a-276">`Serialize` — kontroluje dostęp środowiska uruchomieniowego do elementu członkowskiego, aby umożliwić serializacji i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="09a0a-276">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="09a0a-277">Te zasady można stosować do konstruktorów, pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="09a0a-277">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="09a0a-278">Elementy [Method](method-element-net-native.md) i [Event](event-element-net-native.md) obsługują następujące typy zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-278">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="09a0a-279">`Browse`-kontroluje zapytania o informacje dotyczące tego elementu członkowskiego, ale nie włącza żadnego dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-279">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="09a0a-280">`Dynamic` — kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="09a0a-280">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="09a0a-281">Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="09a0a-281">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="09a0a-282">Ustawienia skojarzone z tymi typami zasad są następujące:</span><span class="sxs-lookup"><span data-stu-id="09a0a-282">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="09a0a-283">`Auto` — Użyj zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-283">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="09a0a-284">(Nieokreślanie zasad jest równoznaczne z ustawieniem tych zasad do `Auto`, chyba że coś zastąpi go).</span><span class="sxs-lookup"><span data-stu-id="09a0a-284">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="09a0a-285">`Excluded` — nigdy nie dołączaj metadanych dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-285">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="09a0a-286">`Included` — Włącz zasady, jeśli typ nadrzędny jest obecny w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="09a0a-286">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="09a0a-287">`Required` — Wymagaj łańcucha narzędzi, aby zachować ten element członkowski nawet wtedy, gdy jest nieużywany, i Włącz dla niego zasady.</span><span class="sxs-lookup"><span data-stu-id="09a0a-287">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="09a0a-288">Semantyka plików dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="09a0a-288">Runtime directives file semantics</span></span>

<span data-ttu-id="09a0a-289">Zasady można definiować jednocześnie dla elementów wyższego poziomu i niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="09a0a-289">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="09a0a-290">Na przykład można zdefiniować zasady dla zestawu i dla niektórych typów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="09a0a-290">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="09a0a-291">Jeśli określony element niższego poziomu nie jest reprezentowany, dziedziczy on zasady jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-291">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="09a0a-292">Na przykład jeśli element `Assembly` jest obecny, ale `Type` elementy nie są, zasady określone w elemencie `Assembly` mają zastosowanie do każdego typu w zestawie.</span><span class="sxs-lookup"><span data-stu-id="09a0a-292">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="09a0a-293">Wiele elementów może również stosować zasady do tego samego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="09a0a-293">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="09a0a-294">Na przykład oddzielne elementy [zestawu](assembly-element-net-native.md) mogą definiować ten sam element zasad dla tego samego zestawu inaczej.</span><span class="sxs-lookup"><span data-stu-id="09a0a-294">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="09a0a-295">W poniższych sekcjach wyjaśniono, w jaki sposób zasady dla określonego typu są rozwiązywane w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="09a0a-295">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="09a0a-296">[Typ](type-element-net-native.md) lub element [metody](method-element-net-native.md) typu ogólnego lub metody stosuje zasady do wszystkich wystąpień, które nie mają własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="09a0a-296">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="09a0a-297">Na przykład element `Type`, który określa zasady dla <xref:System.Collections.Generic.List%601>, ma zastosowanie do wszystkich skonstruowanych wystąpień tego typu ogólnego, chyba że zostanie on zastąpiony dla określonego konstruowanego typu ogólnego (takiego jak `List<Int32>`) przez element `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-297">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="09a0a-298">W przeciwnym razie elementy definiują zasady dla elementu programu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="09a0a-298">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="09a0a-299">Gdy element jest niejednoznaczny, aparat szuka pasujących elementów i jeśli znajdzie dokładne dopasowanie, użyje go.</span><span class="sxs-lookup"><span data-stu-id="09a0a-299">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="09a0a-300">Jeśli znajdzie wiele dopasowań, pojawi się ostrzeżenie lub błąd.</span><span class="sxs-lookup"><span data-stu-id="09a0a-300">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="09a0a-301">Jeśli dwie dyrektywy stosują zasady do tego samego elementu programu</span><span class="sxs-lookup"><span data-stu-id="09a0a-301">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="09a0a-302">Jeśli dwa elementy w różnych dyrektywach środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego elementu programu (na przykład zestawu lub typu) do różnych wartości, konflikt zostanie rozwiązany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="09a0a-302">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="09a0a-303">Jeśli element `Excluded` jest obecny, ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="09a0a-303">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="09a0a-304">`Required` ma pierwszeństwo przed nie `Required`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-304">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="09a0a-305">`All` ma pierwszeństwo przed `PublicAndInternal`, które ma pierwszeństwo przed `Public`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-305">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="09a0a-306">Każde ustawienie jawne ma pierwszeństwo przed `Auto`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-306">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="09a0a-307">Na przykład, jeśli pojedynczy projekt zawiera następujące dwa pliki dyrektywy środowiska uruchomieniowego, zasady serializacji dla klas DataClasses. dll są ustawione na `Required Public` i `All`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-307">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="09a0a-308">W takim przypadku zasady serializacji zostaną rozpoznane jako `Required All`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-308">In this case, the serialization policy would be resolved as `Required All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

<span data-ttu-id="09a0a-309">Jeśli jednak dwie dyrektywy w jednym pliku dyrektywy środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego programu, narzędzie definicji schematu XML wyświetli komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="09a0a-309">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="09a0a-310">Jeśli elementy podrzędne i nadrzędne stosują ten sam typ zasad</span><span class="sxs-lookup"><span data-stu-id="09a0a-310">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="09a0a-311">Elementy podrzędne przesłaniają elementy nadrzędne, w tym ustawienie `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-311">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="09a0a-312">Zastępowanie jest głównym powodem, który ma być określony `Auto`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-312">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="09a0a-313">W poniższym przykładzie ustawienie zasad serializacji dla wszystkiego w `DataClasses`, które nie znajduje się w `DataClasses.ViewModels` byłoby `Required Public`, a wszystko to w `DataClasses` i `DataClasses.ViewModels` będzie `All`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-313">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="09a0a-314">Jeśli otwarte elementy generyczne i wystąpienia mają zastosowanie tego samego typu zasad</span><span class="sxs-lookup"><span data-stu-id="09a0a-314">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="09a0a-315">W poniższym przykładzie `Dictionary<int,int>` są przypisane zasady `Browse` tylko wtedy, gdy silnik ma kolejną przyczynę, aby nadać mu zasady `Browse` (w przeciwnym razie będzie to zachowanie domyślne); każde inne wystąpienie <xref:System.Collections.Generic.Dictionary%602> będzie miało wszystkie jego członków umożliwia przeglądania.</span><span class="sxs-lookup"><span data-stu-id="09a0a-315">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a><span data-ttu-id="09a0a-316">Jak zasady są wywnioskowane</span><span class="sxs-lookup"><span data-stu-id="09a0a-316">How policy is inferred</span></span>

<span data-ttu-id="09a0a-317">Każdy typ zasad ma inny zestaw reguł, które określają, jak obecność tego typu zasad ma wpływ na inne konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="09a0a-317">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="09a0a-318">Efekt przeglądania zasad</span><span class="sxs-lookup"><span data-stu-id="09a0a-318">The effect of Browse policy</span></span>

<span data-ttu-id="09a0a-319">Zastosowanie zasad `Browse` do typu wiąże się z następującymi zmianami zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-319">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-320">Typ podstawowy typu jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-320">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-321">Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-322">Jeśli typ jest delegatem, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-322">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-323">Każdy interfejs typu jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-323">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-324">Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-324">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-325">Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-325">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-326">Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-326">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="09a0a-327">Zastosowanie zasad `Browse` do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-327">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-328">Każdy typ parametru metody jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-328">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-329">Zwracany typ metody jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-329">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-330">Typ zawierający metodę jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-330">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-331">Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona za pomocą zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-331">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-332">Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-332">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-333">Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-333">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-334">Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-334">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="09a0a-335">Zastosowanie zasad `Browse` do pola obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-335">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-336">Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-336">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-337">Typ pola jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-337">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-338">Typ, do którego należy pole, jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-338">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="09a0a-339">Efekt zasad dynamicznych</span><span class="sxs-lookup"><span data-stu-id="09a0a-339">The effect of Dynamic policy</span></span>

<span data-ttu-id="09a0a-340">Zastosowanie zasad `Dynamic` do typu wiąże się z następującymi zmianami zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-340">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-341">Typ podstawowy typu jest oznaczony przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-341">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-342">Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-342">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-343">Jeśli typ jest typem delegata, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-343">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-344">Każdy interfejs typu jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-344">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-345">Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-345">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-346">Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-346">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-347">Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-347">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="09a0a-348">Zastosowanie zasad `Dynamic` do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-348">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-349">Każdy typ parametru metody jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-349">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-350">Zwracany typ metody jest oznaczony przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-350">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-351">Typ zawierający metodę jest oznaczony przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-351">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-352">Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona za pomocą zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-352">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-353">Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-353">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-354">Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-354">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-355">Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-355">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-356">Metoda może być wywoływana przez `MethodInfo.Invoke`, a tworzenie delegatów będzie możliwe przez <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09a0a-356">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="09a0a-357">Zastosowanie zasad `Dynamic` do pola obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-357">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-358">Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-358">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-359">Typ pola jest oznaczony przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-359">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-360">Typ, do którego należy pole, jest oznaczony przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-360">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="09a0a-361">Efekt zasad aktywacji</span><span class="sxs-lookup"><span data-stu-id="09a0a-361">The effect of Activation policy</span></span>

<span data-ttu-id="09a0a-362">Zastosowanie zasad aktywacji do typu wiąże się z następującymi zmianami zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-362">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-363">Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-363">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-364">Jeśli typ jest typem delegata, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-364">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-365">Konstruktory typu są oznaczone przy użyciu zasad `Activation`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-365">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="09a0a-366">Zastosowanie zasad `Activation` do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-366">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="09a0a-367">Konstruktor może być wywoływany przez metody <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> i <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09a0a-367">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="09a0a-368">W przypadku metod zasady `Activation` mają wpływ tylko na konstruktory.</span><span class="sxs-lookup"><span data-stu-id="09a0a-368">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="09a0a-369">Zastosowanie zasad `Activation` do pola nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="09a0a-369">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="09a0a-370">Efekt serializacji zasad</span><span class="sxs-lookup"><span data-stu-id="09a0a-370">The effect of Serialize policy</span></span>

<span data-ttu-id="09a0a-371">Zasady `Serialize` umożliwiają korzystanie z typowych serializatorów opartych na odbiciach.</span><span class="sxs-lookup"><span data-stu-id="09a0a-371">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="09a0a-372">Jednak ze względu na to, że wzorce dostępu do odbicia dla serializatorów firm innych niż Microsoft nie są znane firmie Microsoft, te zasady mogą nie być całkowicie skuteczne.</span><span class="sxs-lookup"><span data-stu-id="09a0a-372">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="09a0a-373">Zastosowanie zasad `Serialize` do typu wiąże się z następującymi zmianami zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-373">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-374">Typ podstawowy typu jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-374">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-375">Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Browse`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-375">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="09a0a-376">Jeśli typ jest typem delegata, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-376">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="09a0a-377">Jeśli typ jest wyliczeniem, tablica typu jest oznaczona za pomocą zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-377">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-378">Jeśli typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-378">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-379">Jeśli typ to <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>lub <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` i <xref:System.Collections.Generic.List%601> oznaczone zasadami `Serialize`., ale żaden element członkowski typu interfejsu nie jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-379">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-380">Jeśli typ jest <xref:System.Collections.Generic.List%601>, żadne elementy członkowskie tego typu nie są oznaczone przy użyciu zasad `Serialize`ymi.</span><span class="sxs-lookup"><span data-stu-id="09a0a-380">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-381">Jeśli typ jest <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> zostanie oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-381">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="09a0a-382">ale żadne elementy członkowskie tego typu nie są oznaczone za pomocą zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-382">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-383">Jeśli typ jest <xref:System.Collections.Generic.Dictionary%602>, żadne elementy członkowskie tego typu nie są oznaczone przy użyciu zasad `Serialize`ymi.</span><span class="sxs-lookup"><span data-stu-id="09a0a-383">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-384">Jeśli typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` i `TValue` są oznaczone przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-384">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-385">Każdy Konstruktor, każdy akcesor właściwości i każde pole jest oznaczone za pomocą zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-385">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="09a0a-386">Zastosowanie zasad `Serialize` do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-386">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-387">Typ zawierający jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-387">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-388">Zwracany typ metody jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-388">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="09a0a-389">Zastosowanie zasad `Serialize` do pola obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="09a0a-389">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="09a0a-390">Typ zawierający jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-390">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="09a0a-391">Typ pola jest oznaczony przy użyciu zasad `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="09a0a-391">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="09a0a-392">Wpływ zasad XmlSerializer, DataContractSerializer i Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="09a0a-392">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="09a0a-393">W przeciwieństwie do zasad `Serialize`, które są przeznaczone dla serializatorów opartych na odbiciach, zasady <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> są używane do włączania zestawu serializatorów znanych do łańcucha narzędzi .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09a0a-393">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="09a0a-394">Te serializacji nie są implementowane przy użyciu odbicia, ale zestaw typów, które mogą być serializowane w czasie wykonywania, jest określany w podobny sposób, jak typy, które są odzwierciedlane.</span><span class="sxs-lookup"><span data-stu-id="09a0a-394">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="09a0a-395">Zastosowanie jednej z tych zasad do typu umożliwia serializacji typu przy użyciu pasującego serializatora.</span><span class="sxs-lookup"><span data-stu-id="09a0a-395">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="09a0a-396">Ponadto wszelkie typy, które aparat serializacji może statycznie określić, ponieważ wymaganie serializacji również będzie możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="09a0a-396">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="09a0a-397">Te zasady nie mają wpływu na metody lub pola.</span><span class="sxs-lookup"><span data-stu-id="09a0a-397">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="09a0a-398">Aby uzyskać więcej informacji, zobacz sekcję "różnice w Serializatorach" w temacie [Migrowanie aplikacji ze sklepu Windows do .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="09a0a-398">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09a0a-399">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09a0a-399">See also</span></span>

- [<span data-ttu-id="09a0a-400">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="09a0a-400">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="09a0a-401">Odbicie i architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="09a0a-401">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
