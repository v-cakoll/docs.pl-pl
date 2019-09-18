---
title: Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adfc0ae6d9bdae333daacee525c7775acd5a8029
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049139"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="3bb52-102">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3bb52-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="3bb52-103">Plik dyrektywy środowiska uruchomieniowego (. Rd. xml) jest plikiem konfiguracji XML, który określa, czy wyszukane elementy programu są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="3bb52-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="3bb52-104">Oto przykład pliku dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="3bb52-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="3bb52-105">Struktura pliku dyrektywy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3bb52-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="3bb52-106">Plik dyrektywy środowiska uruchomieniowego używa `http://schemas.microsoft.com/netfx/2013/01/metadata` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3bb52-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="3bb52-107">Elementem głównym jest element [dyrektywy](directives-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="3bb52-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="3bb52-108">Może zawierać zero lub więcej elementów [biblioteki](library-element-net-native.md) oraz zero lub jeden element [aplikacji](application-element-net-native.md) , jak pokazano w poniższej strukturze.</span><span class="sxs-lookup"><span data-stu-id="3bb52-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="3bb52-109">Atrybuty elementu [aplikacji](application-element-net-native.md) mogą definiować zasady odbicia w środowisku uruchomieniowym dla całej aplikacji lub mogą one stanowić kontener dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3bb52-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="3bb52-110">Element [biblioteki](library-element-net-native.md) , z drugiej strony, jest po prostu kontenerem.</span><span class="sxs-lookup"><span data-stu-id="3bb52-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="3bb52-111">Elementy podrzędne [aplikacji](application-element-net-native.md) i [biblioteki](library-element-net-native.md) definiują typy, metody, pola, właściwości i zdarzenia, które są dostępne do odbicia.</span><span class="sxs-lookup"><span data-stu-id="3bb52-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="3bb52-112">Aby uzyskać informacje referencyjne, wybierz elementy z następującej struktury lub zobacz [elementy dyrektywy środowiska uruchomieniowego](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="3bb52-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="3bb52-113">W poniższej hierarchii wielokropek oznacza strukturę cykliczną.</span><span class="sxs-lookup"><span data-stu-id="3bb52-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="3bb52-114">Informacje w nawiasach wskazują, czy ten element jest opcjonalny, czy wymagany, a jeśli jest używany, ile wystąpień (jeden lub wiele) jest dozwolonych.</span><span class="sxs-lookup"><span data-stu-id="3bb52-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="3bb52-115">[Dyrektywy](directives-element-net-native.md) [1:1] [aplikacja](application-element-net-native.md) [0:1] [zestaw](assembly-element-net-native.md) [0: m] [przestrzeń nazw](namespace-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="3bb52-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-116">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-116">.</span></span> <span data-ttu-id="3bb52-117">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-117">.</span></span>
<span data-ttu-id="3bb52-118">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-119">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-119">.</span></span> <span data-ttu-id="3bb52-120">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-120">.</span></span>
<span data-ttu-id="3bb52-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-122">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-122">.</span></span> <span data-ttu-id="3bb52-123">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-123">.</span></span>
<span data-ttu-id="3bb52-124">[Przestrzeń nazw](namespace-element-net-native.md) [0: M] [Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-125">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-125">.</span></span> <span data-ttu-id="3bb52-126">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-126">.</span></span>
<span data-ttu-id="3bb52-127">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-128">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-128">.</span></span> <span data-ttu-id="3bb52-129">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-129">.</span></span>
<span data-ttu-id="3bb52-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-131">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-131">.</span></span> <span data-ttu-id="3bb52-132">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-132">.</span></span>
<span data-ttu-id="3bb52-133">[Typ](type-element-net-native.md) [0: M] [Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1] [Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-134">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-134">.</span></span> <span data-ttu-id="3bb52-135">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-135">.</span></span>
<span data-ttu-id="3bb52-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-137">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-137">.</span></span> <span data-ttu-id="3bb52-138">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-138">.</span></span>
<span data-ttu-id="3bb52-139">[AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: M] [Metoda](method-element-net-native.md) [0: M] [Parametr](parameter-element-net-native.md) [0: M] [TypeParameter](typeparameter-element-net-native.md) [0: M] [GenericParameter](genericparameter-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M] [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M] [Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-140">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-140">.</span></span> <span data-ttu-id="3bb52-141">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-141">.</span></span>
<span data-ttu-id="3bb52-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-143">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-143">.</span></span> <span data-ttu-id="3bb52-144">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-144">.</span></span>
<span data-ttu-id="3bb52-145">[Metoda](method-element-net-native.md) [0: M] [Parametr](parameter-element-net-native.md) [0: M] [TypeParameter](typeparameter-element-net-native.md) [0: M] [GenericParameter](genericparameter-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M] [Biblioteka](library-element-net-native.md) [0: M] [Zestaw](assembly-element-net-native.md) [0: M] [Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-146">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-146">.</span></span> <span data-ttu-id="3bb52-147">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-147">.</span></span>
<span data-ttu-id="3bb52-148">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-149">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-149">.</span></span> <span data-ttu-id="3bb52-150">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-150">.</span></span>
<span data-ttu-id="3bb52-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-152">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-152">.</span></span> <span data-ttu-id="3bb52-153">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-153">.</span></span>
<span data-ttu-id="3bb52-154">[Przestrzeń nazw](namespace-element-net-native.md) [0: M] [Przestrzeń nazw](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-155">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-155">.</span></span> <span data-ttu-id="3bb52-156">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-156">.</span></span>
<span data-ttu-id="3bb52-157">[Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-158">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-158">.</span></span> <span data-ttu-id="3bb52-159">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-159">.</span></span>
<span data-ttu-id="3bb52-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-161">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-161">.</span></span> <span data-ttu-id="3bb52-162">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-162">.</span></span>
<span data-ttu-id="3bb52-163">[Typ](type-element-net-native.md) [0: M] [Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1] [Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-164">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-164">.</span></span> <span data-ttu-id="3bb52-165">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-165">.</span></span>
<span data-ttu-id="3bb52-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-167">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-167">.</span></span> <span data-ttu-id="3bb52-168">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-168">.</span></span>
<span data-ttu-id="3bb52-169">[AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: M] [Metoda](method-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M] [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M] [Typ](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="3bb52-170">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-170">.</span></span> <span data-ttu-id="3bb52-171">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-171">.</span></span>
<span data-ttu-id="3bb52-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M].</span><span class="sxs-lookup"><span data-stu-id="3bb52-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="3bb52-173">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-173">.</span></span> <span data-ttu-id="3bb52-174">.</span><span class="sxs-lookup"><span data-stu-id="3bb52-174">.</span></span>
<span data-ttu-id="3bb52-175">[Metoda](method-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M]</span><span class="sxs-lookup"><span data-stu-id="3bb52-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="3bb52-176">Element [aplikacji](application-element-net-native.md) nie może mieć żadnych atrybutów lub atrybuty zasad mogą być omówione w [sekcji dyrektywy i zasad środowiska uruchomieniowego](#Directives).</span><span class="sxs-lookup"><span data-stu-id="3bb52-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="3bb52-177">Element [biblioteki](library-element-net-native.md) ma jeden atrybut, `Name`, który określa nazwę biblioteki lub zestawu, bez rozszerzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="3bb52-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="3bb52-178">Na przykład poniższy element [biblioteki](library-element-net-native.md) ma zastosowanie do zestawu o nazwie Extensions. dll.</span><span class="sxs-lookup"><span data-stu-id="3bb52-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="3bb52-179">Dyrektywy i zasady środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3bb52-179">Runtime directives and policy</span></span>

<span data-ttu-id="3bb52-180">Sam element [aplikacji](application-element-net-native.md) i elementy podrzędne [biblioteki](library-element-net-native.md) i elementów [aplikacji](application-element-net-native.md) Express Policy; oznacza to, że definiują sposób, w jaki aplikacja może zastosować odbicie do elementu programu.</span><span class="sxs-lookup"><span data-stu-id="3bb52-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="3bb52-181">Typ zasad jest definiowany przez atrybut elementu (na przykład `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="3bb52-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="3bb52-182">Wartość zasad jest definiowana przez wartość atrybutu (na przykład `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="3bb52-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="3bb52-183">Wszelkie zasady określone przez atrybut elementu mają zastosowanie do wszystkich elementów podrzędnych, które nie określają wartości dla tych zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="3bb52-184">Na przykład jeśli zasady są określone przez element [typu](type-element-net-native.md) , te zasady mają zastosowanie do wszystkich typów i elementów członkowskich, dla których zasady nie są jawnie określone.</span><span class="sxs-lookup"><span data-stu-id="3bb52-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="3bb52-185">Zasady, które mogą być wyrażone przez [aplikację](application-element-net-native.md), [zestaw](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [przestrzeń nazw](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)i elementy [typu](type-element-net-native.md) , różnią się od zasad, które mogą być wyrażone dla poszczególnych członków (przez [Metoda](method-element-net-native.md), [Właściwość](property-element-net-native.md), [pole](field-element-net-native.md)i elementy [zdarzenia](event-element-net-native.md) ).</span><span class="sxs-lookup"><span data-stu-id="3bb52-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="3bb52-186">Określanie zasad dla zestawów, przestrzeni nazw i typów</span><span class="sxs-lookup"><span data-stu-id="3bb52-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="3bb52-187">Elementy [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [podtyp](subtypes-element-net-native.md)i [Type](type-element-net-native.md) obsługują następujące typy zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="3bb52-188">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-188">`Activate`.</span></span> <span data-ttu-id="3bb52-189">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3bb52-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="3bb52-190">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-190">`Browse`.</span></span> <span data-ttu-id="3bb52-191">Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="3bb52-192">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-192">`Dynamic`.</span></span> <span data-ttu-id="3bb52-193">Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="3bb52-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="3bb52-194">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-194">`Serialize`.</span></span> <span data-ttu-id="3bb52-195">Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i Serializowanie wystąpień typu przez biblioteki innych firm, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="3bb52-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="3bb52-196">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-196">`DataContractSerializer`.</span></span> <span data-ttu-id="3bb52-197">Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="3bb52-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="3bb52-198">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="3bb52-199">Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="3bb52-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="3bb52-200">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-200">`XmlSerializer`.</span></span> <span data-ttu-id="3bb52-201">Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="3bb52-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="3bb52-202">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-202">`MarshalObject`.</span></span> <span data-ttu-id="3bb52-203">Kontroluje zasady dotyczące organizowania typów odwołań do WinRT i COM.</span><span class="sxs-lookup"><span data-stu-id="3bb52-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="3bb52-204">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-204">`MarshalDelegate`.</span></span> <span data-ttu-id="3bb52-205">Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="3bb52-206">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="3bb52-206">`MarshalStructure` .</span></span> <span data-ttu-id="3bb52-207">Steruje zasadami organizowania struktur w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="3bb52-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="3bb52-208">Ustawienia skojarzone z tymi typami zasad są następujące:</span><span class="sxs-lookup"><span data-stu-id="3bb52-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="3bb52-209">`All`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-209">`All`.</span></span> <span data-ttu-id="3bb52-210">Włącz zasady dla wszystkich typów i elementów członkowskich, które nie są usuwane przez łańcuch narzędzi.</span><span class="sxs-lookup"><span data-stu-id="3bb52-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="3bb52-211">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-211">`Auto`.</span></span> <span data-ttu-id="3bb52-212">Użyj zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-212">Use the default behavior.</span></span> <span data-ttu-id="3bb52-213">(Nieokreślanie zasad jest równoznaczne z ustawieniem tych zasad `Auto` , chyba że te zasady zostaną zastąpione, na przykład przez element nadrzędny).</span><span class="sxs-lookup"><span data-stu-id="3bb52-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="3bb52-214">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-214">`Excluded`.</span></span> <span data-ttu-id="3bb52-215">Wyłącz zasady dla elementu program.</span><span class="sxs-lookup"><span data-stu-id="3bb52-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="3bb52-216">`Public`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-216">`Public`.</span></span> <span data-ttu-id="3bb52-217">Włącz zasady dla typów publicznych lub członków, chyba że łańcuch narzędzi nie ustali, że element członkowski jest niepotrzebny i usuwa go.</span><span class="sxs-lookup"><span data-stu-id="3bb52-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="3bb52-218">(W tym drugim przypadku należy użyć `Required Public` , aby upewnić się, że element członkowski jest przechowywany i ma możliwości odbicia).</span><span class="sxs-lookup"><span data-stu-id="3bb52-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="3bb52-219">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-219">`PublicAndInternal`.</span></span> <span data-ttu-id="3bb52-220">Włącz zasady dla typów publicznych i wewnętrznych lub członków, jeśli łańcuch narzędzi nie zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="3bb52-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="3bb52-221">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-221">`Required Public`.</span></span> <span data-ttu-id="3bb52-222">Należy wymagać łańcucha narzędzi, aby zachować publiczne typy i członków, niezależnie od tego, czy są one używane, i włączyć dla nich zasady.</span><span class="sxs-lookup"><span data-stu-id="3bb52-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="3bb52-223">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="3bb52-224">Wymagaj, aby łańcuch narzędzi zachował typy publiczne i wewnętrzne oraz członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.</span><span class="sxs-lookup"><span data-stu-id="3bb52-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="3bb52-225">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-225">`Required All`.</span></span> <span data-ttu-id="3bb52-226">Wymagaj łańcucha narzędzi, aby zachować wszystkie typy i członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.</span><span class="sxs-lookup"><span data-stu-id="3bb52-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="3bb52-227">Na przykład następujące pliki dyrektywy środowiska uruchomieniowego definiują zasady dla wszystkich typów i elementów członkowskich w zestawie DataClasses. dll.</span><span class="sxs-lookup"><span data-stu-id="3bb52-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="3bb52-228">Umożliwia odbicie dla serializacji wszystkich właściwości publicznych, umożliwia przeglądanie dla wszystkich typów i elementów członkowskich typu, umożliwia aktywację dla wszystkich typów (z `Dynamic` powodu atrybutu) i umożliwia odbicie dla wszystkich typów publicznych i członków.</span><span class="sxs-lookup"><span data-stu-id="3bb52-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="3bb52-229">Określanie zasad dla członków</span><span class="sxs-lookup"><span data-stu-id="3bb52-229">Specifying policy for members</span></span>

<span data-ttu-id="3bb52-230">Elementy [Właściwości](property-element-net-native.md) i [pól](field-element-net-native.md) obsługują następujące typy zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="3bb52-231">`Browse`-Kontroluje zapytania w celu uzyskania informacji dotyczących tego elementu członkowskiego, ale nie umożliwia dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="3bb52-232">`Dynamic`-Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="3bb52-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="3bb52-233">Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="3bb52-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="3bb52-234">`Serialize`-Kontroluje dostęp środowiska uruchomieniowego do elementu członkowskiego, aby umożliwić serializacji i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="3bb52-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="3bb52-235">Te zasady można stosować do konstruktorów, pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="3bb52-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="3bb52-236">Elementy [Method](method-element-net-native.md) i [Event](event-element-net-native.md) obsługują następujące typy zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="3bb52-237">`Browse`-Kontroluje zapytania o informacje dotyczące tego elementu członkowskiego, ale nie włącza żadnego dostępu do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="3bb52-238">`Dynamic`-Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="3bb52-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="3bb52-239">Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="3bb52-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="3bb52-240">Ustawienia skojarzone z tymi typami zasad są następujące:</span><span class="sxs-lookup"><span data-stu-id="3bb52-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="3bb52-241">`Auto`— Użyj zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="3bb52-242">(Nieokreślanie zasad jest równoznaczne z ustawieniem tych zasad `Auto` , chyba że coś zastępuje je).</span><span class="sxs-lookup"><span data-stu-id="3bb52-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="3bb52-243">`Excluded`-Nigdy nie dołączaj metadanych dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="3bb52-244">`Included`-Włącz zasady, jeśli typ nadrzędny jest obecny w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3bb52-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="3bb52-245">`Required`-Wymagaj łańcucha narzędzi, aby zachować ten element członkowski nawet wtedy, gdy jest nieużywany, i Włącz dla niego zasady.</span><span class="sxs-lookup"><span data-stu-id="3bb52-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="3bb52-246">Semantyka plików dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3bb52-246">Runtime directives file semantics</span></span>

<span data-ttu-id="3bb52-247">Zasady można definiować jednocześnie dla elementów wyższego poziomu i niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3bb52-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="3bb52-248">Na przykład można zdefiniować zasady dla zestawu i dla niektórych typów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="3bb52-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="3bb52-249">Jeśli określony element niższego poziomu nie jest reprezentowany, dziedziczy on zasady jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3bb52-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="3bb52-250">Na przykład jeśli `Assembly` element jest obecny, ale `Type` elementy nie są, zasady określone w `Assembly` elemencie mają zastosowanie do każdego typu w zestawie.</span><span class="sxs-lookup"><span data-stu-id="3bb52-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="3bb52-251">Wiele elementów może również stosować zasady do tego samego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="3bb52-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="3bb52-252">Na przykład oddzielne elementy [zestawu](assembly-element-net-native.md) mogą definiować ten sam element zasad dla tego samego zestawu inaczej.</span><span class="sxs-lookup"><span data-stu-id="3bb52-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="3bb52-253">W poniższych sekcjach wyjaśniono, w jaki sposób zasady dla określonego typu są rozwiązywane w tych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="3bb52-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="3bb52-254">[Typ](type-element-net-native.md) lub element [metody](method-element-net-native.md) typu ogólnego lub metody stosuje zasady do wszystkich wystąpień, które nie mają własnych zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="3bb52-255">Na przykład `Type` element określający <xref:System.Collections.Generic.List%601> zasady dotyczą wszystkich skonstruowanych wystąpień tego typu ogólnego, chyba że zostanie przesłonięty dla określonego konstruowanego `List<Int32>`typu ogólnego (takiego `TypeInstantiation` jak) przez element.</span><span class="sxs-lookup"><span data-stu-id="3bb52-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="3bb52-256">W przeciwnym razie elementy definiują zasady dla elementu programu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="3bb52-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="3bb52-257">Gdy element jest niejednoznaczny, aparat szuka pasujących elementów i jeśli znajdzie dokładne dopasowanie, użyje go.</span><span class="sxs-lookup"><span data-stu-id="3bb52-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="3bb52-258">Jeśli znajdzie wiele dopasowań, pojawi się ostrzeżenie lub błąd.</span><span class="sxs-lookup"><span data-stu-id="3bb52-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="3bb52-259">Jeśli dwie dyrektywy stosują zasady do tego samego elementu programu</span><span class="sxs-lookup"><span data-stu-id="3bb52-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="3bb52-260">Jeśli dwa elementy w różnych dyrektywach środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego elementu programu (na przykład zestawu lub typu) do różnych wartości, konflikt zostanie rozwiązany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3bb52-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="3bb52-261">`Excluded` Jeśli element jest obecny, ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="3bb52-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="3bb52-262">`Required`ma pierwszeństwo przed `Required`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="3bb52-263">`All`ma pierwszeństwo `PublicAndInternal`przed, który ma `Public`pierwszeństwo przed.</span><span class="sxs-lookup"><span data-stu-id="3bb52-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="3bb52-264">Każde ustawienie jawne ma pierwszeństwo `Auto`przed.</span><span class="sxs-lookup"><span data-stu-id="3bb52-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="3bb52-265">Na przykład jeśli pojedynczy projekt zawiera następujące dwa pliki dyrektywy środowiska uruchomieniowego, zasady serializacji dla DataClasses. dll są ustawione na `Required Public` i. `All`</span><span class="sxs-lookup"><span data-stu-id="3bb52-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="3bb52-266">W takim przypadku zasady serializacji byłyby rozpoznawane jako `Required All`.</span><span class="sxs-lookup"><span data-stu-id="3bb52-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="3bb52-267">Jeśli jednak dwie dyrektywy w jednym pliku dyrektywy środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego programu, narzędzie definicji schematu XML wyświetli komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3bb52-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="3bb52-268">Jeśli elementy podrzędne i nadrzędne stosują ten sam typ zasad</span><span class="sxs-lookup"><span data-stu-id="3bb52-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="3bb52-269">Elementy podrzędne przesłaniają elementy nadrzędne, w `Excluded` tym ustawienie.</span><span class="sxs-lookup"><span data-stu-id="3bb52-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="3bb52-270">Zastępowanie jest głównym powodem, który ma zostać `Auto`określony.</span><span class="sxs-lookup"><span data-stu-id="3bb52-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="3bb52-271">W poniższym przykładzie ustawienie zasad `DataClasses` serializacji dla wszystkiego w tym elemencie `DataClasses.ViewModels` nie `Required Public`jest, a `All`wszystko to w obu `DataClasses` i `DataClasses.ViewModels` .</span><span class="sxs-lookup"><span data-stu-id="3bb52-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="3bb52-272">Jeśli otwarte elementy generyczne i wystąpienia mają zastosowanie tego samego typu zasad</span><span class="sxs-lookup"><span data-stu-id="3bb52-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="3bb52-273">W `Dictionary<int,int>` poniższym przykładzie `Browse` zasady są przypisywane tylko wtedy, gdy silnik ma kolejną przyczynę, `Browse` aby nadać mu zasady (które w przeciwnym razie byłyby <xref:System.Collections.Generic.Dictionary%602> zachowaniem domyślnym); każde inne wystąpienie będzie miało wszystkie jego członkowie umożliwia przeglądania.</span><span class="sxs-lookup"><span data-stu-id="3bb52-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="3bb52-274">Jak zasady są wywnioskowane</span><span class="sxs-lookup"><span data-stu-id="3bb52-274">How policy is inferred</span></span>

<span data-ttu-id="3bb52-275">Każdy typ zasad ma inny zestaw reguł, które określają, jak obecność tego typu zasad ma wpływ na inne konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="3bb52-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="3bb52-276">Efekt przeglądania zasad</span><span class="sxs-lookup"><span data-stu-id="3bb52-276">The effect of Browse policy</span></span>

<span data-ttu-id="3bb52-277">`Browse` Zastosowanie zasad do typu obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-278">Typ podstawowy typu jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-279">Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-280">Jeśli typ jest delegatem, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-281">Każdy interfejs typu jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-282">Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-283">Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-284">Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone `Browse` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="3bb52-285">`Browse` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-286">Każdy typ parametru metody jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-287">Zwracany typ metody jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-288">Typ zawierający metodę jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-289">Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-290">Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-291">Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-292">Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone `Browse` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="3bb52-293">`Browse` Zastosowanie zasad do pola obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-294">Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-295">Typ pola jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-296">Typ, do którego należy pole, jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="3bb52-297">Efekt zasad dynamicznych</span><span class="sxs-lookup"><span data-stu-id="3bb52-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="3bb52-298">`Dynamic` Zastosowanie zasad do typu obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-299">Typ podstawowy typu jest oznaczony przy użyciu `Dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-300">Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-301">Jeśli typ jest typem delegata, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-302">Każdy interfejs typu jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-303">Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-304">Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-305">Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone `Browse` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="3bb52-306">`Dynamic` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-307">Każdy typ parametru metody jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-308">Zwracany typ metody jest oznaczony przy użyciu `Dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-309">Typ zawierający metodę jest oznaczony przy użyciu `Dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-310">Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-311">Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-312">Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-313">Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone `Browse` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-314">Metoda może być wywoływana przez `MethodInfo.Invoke`, a tworzenie delegatów jest możliwe przez. <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3bb52-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3bb52-315">`Dynamic` Zastosowanie zasad do pola obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-316">Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-317">Typ pola jest oznaczony przy użyciu `Dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-318">Typ, do którego należy pole, jest oznaczony przy użyciu `Dynamic` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="3bb52-319">Efekt zasad aktywacji</span><span class="sxs-lookup"><span data-stu-id="3bb52-319">The effect of Activation policy</span></span>

<span data-ttu-id="3bb52-320">Zastosowanie zasad aktywacji do typu wiąże się z następującymi zmianami zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-321">Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-322">Jeśli typ jest typem delegata, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-323">Konstruktory typu są oznaczone `Activation` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="3bb52-324">`Activation` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="3bb52-325">Konstruktor może być wywoływany przez <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> metody i. <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3bb52-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="3bb52-326">W przypadku metod `Activation` zasady mają wpływ tylko na konstruktory.</span><span class="sxs-lookup"><span data-stu-id="3bb52-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="3bb52-327">`Activation` Zastosowanie zasad do pola nie ma żadnego skutku.</span><span class="sxs-lookup"><span data-stu-id="3bb52-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="3bb52-328">Efekt serializacji zasad</span><span class="sxs-lookup"><span data-stu-id="3bb52-328">The effect of Serialize policy</span></span>

<span data-ttu-id="3bb52-329">`Serialize` Zasady umożliwiają korzystanie z typowych serializatorów opartych na odbiciach.</span><span class="sxs-lookup"><span data-stu-id="3bb52-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="3bb52-330">Jednak ze względu na to, że wzorce dostępu do odbicia dla serializatorów firm innych niż Microsoft nie są znane firmie Microsoft, te zasady mogą nie być całkowicie skuteczne.</span><span class="sxs-lookup"><span data-stu-id="3bb52-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="3bb52-331">`Serialize` Zastosowanie zasad do typu obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-332">Typ podstawowy typu jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-333">Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Browse` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="3bb52-334">Jeśli typ jest typem delegata, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="3bb52-335">Jeśli typ jest wyliczeniem, tablica typu jest oznaczona przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-336">Jeśli typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-337">Jeśli typ ma <xref:System.Collections.Generic.IEnumerable%601>wartość, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601> ,,<xref:System.Collections.Generic.IReadOnlyList%601>lub ,`T[]` i<xref:System.Collections.Generic.List%601> jest oznaczony`Serialize` przy użyciu zasad., ale żaden element członkowski typu interfejsu nie jest oznaczony za pomocą <xref:System.Collections.Generic.IReadOnlyCollection%601> `Serialize`zasady.</span><span class="sxs-lookup"><span data-stu-id="3bb52-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-338">Jeśli typ ma wartość <xref:System.Collections.Generic.List%601>, żadne elementy członkowskie tego typu nie są oznaczone `Serialize` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-339">Jeśli typ ma <xref:System.Collections.Generic.IDictionary%602>wartość, <xref:System.Collections.Generic.Dictionary%602> jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="3bb52-340">ale żadne elementy członkowskie tego typu nie są oznaczone `Serialize` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-341">Jeśli typ ma wartość <xref:System.Collections.Generic.Dictionary%602>, żadne elementy członkowskie tego typu nie są oznaczone `Serialize` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-342">Jeśli <xref:System.Collections.Generic.IDictionary%602>typ implementuje `TKey` i`TValue`jest oznaczony przy użyciu zasad.`Serialize`</span><span class="sxs-lookup"><span data-stu-id="3bb52-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-343">Każdy Konstruktor, każdy akcesor właściwości i każde pole jest oznaczone `Serialize` zasadami.</span><span class="sxs-lookup"><span data-stu-id="3bb52-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="3bb52-344">`Serialize` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-345">Typ zawierający jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-346">Zwracany typ metody jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="3bb52-347">`Serialize` Zastosowanie zasad do pola obejmuje następujące zmiany zasad:</span><span class="sxs-lookup"><span data-stu-id="3bb52-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="3bb52-348">Typ zawierający jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="3bb52-349">Typ pola jest oznaczony przy użyciu `Serialize` zasad.</span><span class="sxs-lookup"><span data-stu-id="3bb52-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="3bb52-350">Wpływ zasad XmlSerializer, DataContractSerializer i Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3bb52-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="3bb52-351">W przeciwieństwie `Serialize` do zasad, które są przeznaczone dla serializatorów opartych na odbiciach <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer>, zasady <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , i są używane do włączania zestawu serializatorów, które są znane do łańcucha narzędzi .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3bb52-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="3bb52-352">Te serializacji nie są implementowane przy użyciu odbicia, ale zestaw typów, które mogą być serializowane w czasie wykonywania, jest określany w podobny sposób, jak typy, które są odzwierciedlane.</span><span class="sxs-lookup"><span data-stu-id="3bb52-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="3bb52-353">Zastosowanie jednej z tych zasad do typu umożliwia serializacji typu przy użyciu pasującego serializatora.</span><span class="sxs-lookup"><span data-stu-id="3bb52-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="3bb52-354">Ponadto wszelkie typy, które aparat serializacji może statycznie określić, ponieważ wymaganie serializacji również będzie możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="3bb52-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="3bb52-355">Te zasady nie mają wpływu na metody lub pola.</span><span class="sxs-lookup"><span data-stu-id="3bb52-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="3bb52-356">Aby uzyskać więcej informacji, zobacz sekcję "różnice w Serializatorach" w temacie [Migrowanie aplikacji ze sklepu Windows do .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="3bb52-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3bb52-357">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bb52-357">See also</span></span>

- [<span data-ttu-id="3bb52-358">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3bb52-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="3bb52-359">Odbicie i architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="3bb52-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
