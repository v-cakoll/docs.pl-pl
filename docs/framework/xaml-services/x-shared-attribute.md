---
title: "x:Shared — Atrybut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d6a9333b2267e82fc25b2a0ec4bf5dd14f644078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xshared-attribute"></a><span data-ttu-id="79891-102">x:Shared — Atrybut</span><span class="sxs-lookup"><span data-stu-id="79891-102">x:Shared Attribute</span></span>
<span data-ttu-id="79891-103">Jeśli wartość `false`, modyfikuje zachowanie pobieranie zasobu WPF, tak aby żądania dotyczące zasobów oparte na atrybutach Utwórz nowe wystąpienie dla każdego żądania i nie udostępniały tej samej wystąpienia dla wszystkich żądań.</span><span class="sxs-lookup"><span data-stu-id="79891-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="79891-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="79891-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="79891-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79891-105">Remarks</span></span>  
 <span data-ttu-id="79891-106">`x:Shared`jest mapowany na przestrzeń nazw XAML dla języka XAML i został rozpoznany jako prawidłowy element języka XAML .NET Framework XAML Services i jego czytników XAML.</span><span class="sxs-lookup"><span data-stu-id="79891-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="79891-107">Jednak podane możliwości `x:Shared` są dostępne tylko dla aplikacji WPF i dla analizatora WPF XAML.</span><span class="sxs-lookup"><span data-stu-id="79891-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="79891-108">Na platformie WPF `x:Shared` przydaje się tylko jako atrybut po zastosowaniu do obiektu, który istnieje w ramach WPF <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="79891-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="79891-109">Inne użycia nie zgłaszają wyjątki analizy lub inne błędy, ale nie działają.</span><span class="sxs-lookup"><span data-stu-id="79891-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="79891-110">Znaczenie `x:Shared` nie została określona w specyfikacji języka XAML.</span><span class="sxs-lookup"><span data-stu-id="79891-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="79891-111">Inne implementacje XAML, takimi jak rozbudowywać usług .NET Framework XAML, nie zapewniają niekoniecznie udostępniania zasobów pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="79891-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="79891-112">Takie implementacje XAML może dostarczyć podobne zachowania w ramach obsługi, które również używane `x:Shared` wartości.</span><span class="sxs-lookup"><span data-stu-id="79891-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="79891-113">Na platformie WPF, domyślnie `x:Shared` warunek dla zasobów jest `true`.</span><span class="sxs-lookup"><span data-stu-id="79891-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="79891-114">Ten stan oznacza, że każde żądanie zasobu zawsze zwraca to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="79891-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="79891-115">Modyfikowanie obiektu, który jest zwracany za pomocą zasobów interfejsu API, takich jak <xref:System.Windows.FrameworkElement.FindResource%2A>, lub modyfikowania obiektu bezpośrednio w <xref:System.Windows.ResourceDictionary>, zmiany pierwotnego zasobu.</span><span class="sxs-lookup"><span data-stu-id="79891-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="79891-116">Odwołania do tego zasobu, gdyby odwołania do zasobów dynamicznych, korzystającym z tego zasobu Pobierz zmienione zasobów.</span><span class="sxs-lookup"><span data-stu-id="79891-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="79891-117">Odwołania do zasobu, gdyby odwołania do zasobu statycznych, zmiany zasobów po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] czas przetwarzania nie mają znaczenia.</span><span class="sxs-lookup"><span data-stu-id="79891-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="79891-118">Aby uzyskać więcej informacji o statyczne i odwołania do zasobów dynamicznej, zobacz [zasobów XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="79891-118">For more information about static versus dynamic resource references, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="79891-119">Jawne określenie `x:Shared="true"` rzadko się odbywa, ponieważ już jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="79891-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="79891-120">Nie ma odpowiednika dla żadnego kodu bezpośrednio `x:Shared` w podsystemie WPF modelu obiektów; można określić tylko w przypadku użycia XAML i muszą zostać przetworzone przez domyślne zachowanie WPF lub pośredni strumień węzłów XAML w ścieżce obciążenia przetwarzanie przy użyciu programu .NET Framework XAML Se rvices i jego czytników XAML.</span><span class="sxs-lookup"><span data-stu-id="79891-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="79891-121">Scenariusz dla `x:Shared="false"` jest Jeśli zdefiniujesz <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasy jako zasób, a następnie wprowadzić zasobów element do modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="79891-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="79891-122">`x:Shared="false"`Włącza zasób elementu można wprowadzać wiele razy w tej samej kolekcji (takie jak <xref:System.Windows.Controls.UIElementCollection>).</span><span class="sxs-lookup"><span data-stu-id="79891-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="79891-123">Bez `x:Shared="false"` to jest nieprawidłowa, ponieważ kolekcja wymusza unikatowości jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="79891-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="79891-124">Jednak `x:Shared="false"` zachowanie tworzy inne wystąpienie identyczne zasobu zamiast zwracać tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="79891-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="79891-125">Inny scenariusz `x:Shared="false"` jest użycie <xref:System.Windows.Freezable> zasobu dla wartości animacji, ale chcesz modyfikacja zasobu na podstawie na animacji.</span><span class="sxs-lookup"><span data-stu-id="79891-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="79891-126">Obsługa ciągu `false` nie jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="79891-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="79891-127">Na platformie WPF `x:Shared` działa tylko w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="79891-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="79891-128"><xref:System.Windows.ResourceDictionary> Zawiera elementy z `x:Shared` muszą być skompilowane.</span><span class="sxs-lookup"><span data-stu-id="79891-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="79891-129"><xref:System.Windows.ResourceDictionary> Nie może być w XAML utracić ani użyte dla motywów.</span><span class="sxs-lookup"><span data-stu-id="79891-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="79891-130"><xref:System.Windows.ResourceDictionary> Zawiera elementy nie może być zagnieżdżony w innym <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="79891-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="79891-131">Na przykład nie można użyć `x:Shared` dla elementów w <xref:System.Windows.ResourceDictionary> znajduje się w <xref:System.Windows.Style> jest już <xref:System.Windows.ResourceDictionary> elementu.</span><span class="sxs-lookup"><span data-stu-id="79891-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79891-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79891-132">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="79891-133">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="79891-133">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="79891-134">Elementy podstawowe</span><span class="sxs-lookup"><span data-stu-id="79891-134">Base Elements</span></span>](../../../docs/framework/wpf/advanced/base-elements.md)
