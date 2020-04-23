---
title: x:Subclass — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071368"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="87df6-102">x:Subclass — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="87df6-102">x:Subclass Directive</span></span>

<span data-ttu-id="87df6-103">Modyfikuje zachowanie kompilacji znaczników `x:Class` XAML, gdy jest również podany.</span><span class="sxs-lookup"><span data-stu-id="87df6-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="87df6-104">Zamiast tworzenia klasy częściowej, która `x:Class`jest oparta na , pod warunkiem `x:Class` jest tworzony jako klasa pośrednia, a następnie pod warunkiem, że klasa pochodna ma być oparta na `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="87df6-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="87df6-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="87df6-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="87df6-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="87df6-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="87df6-107">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="87df6-107">Optional.</span></span> <span data-ttu-id="87df6-108">Określa obszar nazw CLR `classname`zawierający plik .</span><span class="sxs-lookup"><span data-stu-id="87df6-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="87df6-109">Jeśli `namespace` jest określony, kropka (.) oddziela `namespace` i `classname`.</span><span class="sxs-lookup"><span data-stu-id="87df6-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="87df6-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="87df6-110">Required.</span></span> <span data-ttu-id="87df6-111">Określa nazwę CLR klasy częściowej, która łączy załadowany kod XAML i kod dla tego kodu XAML.</span><span class="sxs-lookup"><span data-stu-id="87df6-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="87df6-112">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="87df6-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="87df6-113">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="87df6-113">Optional.</span></span> <span data-ttu-id="87df6-114">Może się `namespace` różnić od tego, czy każdy obszar nazw może rozwiązać inny.</span><span class="sxs-lookup"><span data-stu-id="87df6-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="87df6-115">Określa obszar nazw CLR `subclassName`zawierający plik .</span><span class="sxs-lookup"><span data-stu-id="87df6-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="87df6-116">Jeśli `subclassName` jest określony, kropka (.) oddziela `subclassNamespace` i `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="87df6-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="87df6-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="87df6-117">Required.</span></span> <span data-ttu-id="87df6-118">Określa nazwę CLR podklasy.</span><span class="sxs-lookup"><span data-stu-id="87df6-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="87df6-119">Zależności</span><span class="sxs-lookup"><span data-stu-id="87df6-119">Dependencies</span></span>

<span data-ttu-id="87df6-120">[x:Dyrektywa klasy](xclass-directive.md) musi być również podana na tym samym obiekcie, a ten obiekt musi być głównym elementem produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="87df6-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="87df6-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87df6-121">Remarks</span></span>

<span data-ttu-id="87df6-122">`x:Subclass`użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="87df6-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="87df6-123">Klasa używana jako `x:Subclass` klasa nie może być `x:Subclass` klasą zagnieżdżoną i musi odwoływać się do obiektu głównego, jak wyjaśniono w sekcji "Zależności".</span><span class="sxs-lookup"><span data-stu-id="87df6-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="87df6-124">W przeciwnym razie znaczenie `x:Subclass` koncepcyjne jest niezdefiniowane przez implementację usług .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="87df6-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="87df6-125">Dzieje się tak, ponieważ zachowanie usług .NET XAML services nie określa ogólnego modelu programowania, za pomocą którego są połączone znaczniki XAML i kod zapasowy.</span><span class="sxs-lookup"><span data-stu-id="87df6-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="87df6-126">Implementacje dalszych pojęć `x:Class` związanych z i `x:Subclass` są wykonywane przez określone struktury, które używają modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML, skompilowanych znaczników i opartych na programie CLR związanych z kodem.</span><span class="sxs-lookup"><span data-stu-id="87df6-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="87df6-127">Każda struktura może mieć własne akcje kompilacji, które umożliwiają niektóre zachowanie lub określonych składników, które muszą być uwzględnione w środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="87df6-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="87df6-128">W ramach akcje kompilacji mogą się również różnić w zależności od określonego języka CLR, który jest używany dla kodu.</span><span class="sxs-lookup"><span data-stu-id="87df6-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="87df6-129">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="87df6-129">WPF Usage Notes</span></span>

<span data-ttu-id="87df6-130">`x:Subclass`może znajdować się na stronie <xref:System.Windows.Application> głównej lub na katalogu `x:Class`głównym w definicji aplikacji, która już ma .</span><span class="sxs-lookup"><span data-stu-id="87df6-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="87df6-131">Deklarowanie `x:Subclass` na dowolny element inny niż strona lub katalog `x:Class` główny aplikacji lub określenie go tam, gdzie nie istnieje, powoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="87df6-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="87df6-132">Tworzenie klas pochodnych, które `x:Subclass` działają poprawnie dla scenariusza jest dość skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="87df6-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="87df6-133">Może być konieczne zbadanie plików pośrednich (pliki .g utworzone w folderze obj projektu przez kompilację znaczników, z nazwami zawierającymi nazwy plików .xaml).</span><span class="sxs-lookup"><span data-stu-id="87df6-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="87df6-134">Te pliki pośrednie mogą pomóc w określeniu pochodzenia niektórych konstrukcji programowania w połączonych klas częściowych w skompilowaną aplikację.</span><span class="sxs-lookup"><span data-stu-id="87df6-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="87df6-135">Programy obsługi zdarzeń w klasie `internal override` pochodnej muszą być (w`Friend Overrides` programie Microsoft Visual Basic) w celu zastąpienia wycinków dla programów obsługi utworzonych w klasie pośredniej podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="87df6-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="87df6-136">W przeciwnym razie implementacje klasy pochodnej ukryć (cień) implementacji klasy pośredniej i pośrednich obsługi klasy nie są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="87df6-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="87df6-137">Podczas definiowania `x:Class` `x:Subclass`zarówno i , nie trzeba podać żadnej implementacji `x:Class`dla klasy, do której odwołuje się .</span><span class="sxs-lookup"><span data-stu-id="87df6-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="87df6-138">Wystarczy nadać mu nazwę za `x:Class` pośrednictwem atrybutu, tak aby kompilator ma pewne wskazówki dla klasy, która tworzy w plikach pośrednich (kompilator nie wybiera domyślnej nazwy w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="87df6-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="87df6-139">Można dać `x:Class` klasie implementacji; jednak nie jest to typowy scenariusz `x:Class` `x:Subclass`do korzystania zarówno i .</span><span class="sxs-lookup"><span data-stu-id="87df6-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="87df6-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87df6-140">See also</span></span>

- [<span data-ttu-id="87df6-141">x:Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="87df6-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="87df6-142">Klasy XAML i niestandardowe dla WPF</span><span class="sxs-lookup"><span data-stu-id="87df6-142">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
