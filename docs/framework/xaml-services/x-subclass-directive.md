---
title: x:Subclass — dyrektywa
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: 20
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 566b772db0e8f96c3272481d47b3e220f727d95b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xsubclass-directive"></a><span data-ttu-id="e2695-102">x:Subclass — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="e2695-102">x:Subclass Directive</span></span>
<span data-ttu-id="e2695-103">Modyfikuje zachowanie kompilacji znaczników XAML podczas `x:Class` jest również udostępniany.</span><span class="sxs-lookup"><span data-stu-id="e2695-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="e2695-104">Zamiast tworzenia częściowej klasy, która jest oparta na `x:Class`, dostarczonych `x:Class` zostanie utworzona jako klasa pośrednicząca, a następnie oczekuje na podstawie podanych klasy pochodnej `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="e2695-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="e2695-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="e2695-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e2695-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="e2695-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="e2695-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e2695-107">Optional.</span></span> <span data-ttu-id="e2695-108">Określa przestrzeń nazw środowiska CLR, która zawiera `classname`.</span><span class="sxs-lookup"><span data-stu-id="e2695-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="e2695-109">Jeśli `namespace` określono kropkę (.) oddziela `namespace` i `classname`.</span><span class="sxs-lookup"><span data-stu-id="e2695-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="e2695-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e2695-110">Required.</span></span> <span data-ttu-id="e2695-111">Określa nazwę CLR częściowej klasy, która łączy załadować XAML i z kodem dla tego języka XAML.</span><span class="sxs-lookup"><span data-stu-id="e2695-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="e2695-112">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="e2695-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="e2695-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e2695-113">Optional.</span></span> <span data-ttu-id="e2695-114">Może się różnić od `namespace` Jeśli każdej przestrzeni nazw można rozwiązać drugi.</span><span class="sxs-lookup"><span data-stu-id="e2695-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="e2695-115">Określa przestrzeń nazw środowiska CLR, która zawiera `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="e2695-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="e2695-116">Jeśli `subclassName` określono kropkę (.) oddziela `subclassNamespace` i `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="e2695-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="e2695-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e2695-117">Required.</span></span> <span data-ttu-id="e2695-118">Określa nazwę CLR podklasy.</span><span class="sxs-lookup"><span data-stu-id="e2695-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="e2695-119">Zależności</span><span class="sxs-lookup"><span data-stu-id="e2695-119">Dependencies</span></span>  
 <span data-ttu-id="e2695-120">[x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md) należy dostarczyć także na tym samym obiekcie i ten obiekt musi być elementem głównym produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="e2695-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2695-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2695-121">Remarks</span></span>  
 <span data-ttu-id="e2695-122">`x:Subclass` użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="e2695-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="e2695-123">Użyta jako klasa `x:Subclass` nie może być klasą zagnieżdżoną i `x:Subclass` musi odwoływać się do obiektu głównego, jak opisano w sekcji "Zależności".</span><span class="sxs-lookup"><span data-stu-id="e2695-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="e2695-124">W przeciwnym razie koncepcyjnej znaczenie `x:Subclass` jest niezdefiniowana przez implementację usług .NET Framework XAML.</span><span class="sxs-lookup"><span data-stu-id="e2695-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="e2695-125">Jest to spowodowane zachowanie usług .NET Framework XAML nie został określony ogólny model programowania przez XAML, które są połączone znaczników i tworzenie kopii kodu.</span><span class="sxs-lookup"><span data-stu-id="e2695-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="e2695-126">Implementacje dalsze pojęcia związane z `x:Class` i `x:Subclass` są wykonywane przez określone struktur, co umożliwia definiowanie sposobu połączenia znaczników XAML, znaczników skompilowany i na podstawie CLR kodem modele programowania i modeli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2695-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="e2695-127">Każdy framework może mieć własną akcji kompilacji, które udostępnia niektóre działania lub określone składniki, które muszą być zawarte w środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e2695-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="e2695-128">W ramach akcji kompilacji można również różnić w zależności od określonego języka środowiska CLR używanej do kodu powiązanego.</span><span class="sxs-lookup"><span data-stu-id="e2695-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="e2695-129">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="e2695-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="e2695-130">`x:Subclass` można na katalog główny strony lub <xref:System.Windows.Application> głównego definicji aplikacji, który ma już `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="e2695-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="e2695-131">Deklarowanie `x:Subclass` dla dowolnego elementu innego niż katalog główny strony lub aplikacji lub określanie go, jeśli nie `x:Class` istnieje, powoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e2695-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="e2695-132">Tworzenie pochodnych klas pracy prawidłowe `x:Subclass` scenariusza jest dość złożone.</span><span class="sxs-lookup"><span data-stu-id="e2695-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="e2695-133">Konieczne może być zbadać plików pośrednich (pliki .g tworzone w folderze obj. projektu przez kompilacji znaczników, z nazwami zawierające .xaml nazwy pliku).</span><span class="sxs-lookup"><span data-stu-id="e2695-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="e2695-134">Tych plików pośrednich może pomóc w określeniu źródła niektórych narzędzi programistycznych w dołączonym do klas częściowych w skompilowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2695-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="e2695-135">Programy obsługi zdarzeń w klasie pochodnej musi być `internal override` (`Friend Overrides` programu Microsoft Visual Basic) w celu zastąpienia klas zastępczych dla programów obsługi, jak utworzony w klasie pośrednie podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e2695-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="e2695-136">W przeciwnym razie implementacji klasy pochodnej Ukryj (tle) implementacji klasa pośrednicząca i nie są wywoływane programy obsługi klasa pośrednicząca.</span><span class="sxs-lookup"><span data-stu-id="e2695-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="e2695-137">Podczas definiowania zarówno `x:Class` i `x:Subclass`, nie trzeba podać implementacji klasy, która odwołuje się do niego `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="e2695-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="e2695-138">Musisz podać jego nazwę przy użyciu `x:Class` atrybutu, dzięki czemu kompilator ma pewne wskazówki dotyczące klasy, która tworzy w plikach pośredniego (kompilator nie wybierz nazwę domyślną w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="e2695-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="e2695-139">Można nadać `x:Class` klasa implementacji; mimo to nie jest typowym scenariuszem stosowania zarówno `x:Class` i `x:Subclass`.</span><span class="sxs-lookup"><span data-stu-id="e2695-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2695-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2695-140">See Also</span></span>  
 [<span data-ttu-id="e2695-141">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="e2695-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="e2695-142">Klasy XAML i niestandardowe dla WPF</span><span class="sxs-lookup"><span data-stu-id="e2695-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
