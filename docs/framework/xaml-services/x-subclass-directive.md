---
title: "x:Subclass — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
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
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5c6e91fcecb60dee2577ea62c2313f8b2c7eecbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xsubclass-directive"></a><span data-ttu-id="c4b01-102">x:Subclass — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="c4b01-102">x:Subclass Directive</span></span>
<span data-ttu-id="c4b01-103">Modyfikuje zachowanie kompilacji znaczników XAML podczas `x:Class` jest również udostępniany.</span><span class="sxs-lookup"><span data-stu-id="c4b01-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="c4b01-104">Zamiast tworzenia częściowej klasy, która jest oparta na `x:Class`, dostarczonych `x:Class` zostanie utworzona jako klasa pośrednicząca, a następnie oczekuje na podstawie podanych klasy pochodnej `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c4b01-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c4b01-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c4b01-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="c4b01-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="c4b01-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c4b01-107">Optional.</span></span> <span data-ttu-id="c4b01-108">Określa przestrzeń nazw środowiska CLR, która zawiera `classname`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="c4b01-109">Jeśli `namespace` określono kropkę (.) oddziela `namespace` i `classname`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="c4b01-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c4b01-110">Required.</span></span> <span data-ttu-id="c4b01-111">Określa nazwę CLR częściowej klasy, która łączy załadować XAML i z kodem dla tego języka XAML.</span><span class="sxs-lookup"><span data-stu-id="c4b01-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="c4b01-112">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="c4b01-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="c4b01-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c4b01-113">Optional.</span></span> <span data-ttu-id="c4b01-114">Może się różnić od `namespace` Jeśli każdej przestrzeni nazw można rozwiązać drugi.</span><span class="sxs-lookup"><span data-stu-id="c4b01-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="c4b01-115">Określa przestrzeń nazw środowiska CLR, która zawiera `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="c4b01-116">Jeśli `subclassName` określono kropkę (.) oddziela `subclassNamespace` i `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="c4b01-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c4b01-117">Required.</span></span> <span data-ttu-id="c4b01-118">Określa nazwę CLR podklasy.</span><span class="sxs-lookup"><span data-stu-id="c4b01-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="c4b01-119">Zależności</span><span class="sxs-lookup"><span data-stu-id="c4b01-119">Dependencies</span></span>  
 <span data-ttu-id="c4b01-120">[x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md) należy dostarczyć także na tym samym obiekcie i ten obiekt musi być elementem głównym produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="c4b01-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b01-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4b01-121">Remarks</span></span>  
 <span data-ttu-id="c4b01-122">`x:Subclass`użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="c4b01-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="c4b01-123">Użyta jako klasa `x:Subclass` nie może być klasą zagnieżdżoną i `x:Subclass` musi odwoływać się do obiektu głównego, jak opisano w sekcji "Zależności".</span><span class="sxs-lookup"><span data-stu-id="c4b01-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="c4b01-124">W przeciwnym razie koncepcyjnej znaczenie `x:Subclass` jest niezdefiniowana przez implementację usług .NET Framework XAML.</span><span class="sxs-lookup"><span data-stu-id="c4b01-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="c4b01-125">Jest to spowodowane zachowanie usług .NET Framework XAML nie został określony ogólny model programowania przez XAML, które są połączone znaczników i tworzenie kopii kodu.</span><span class="sxs-lookup"><span data-stu-id="c4b01-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="c4b01-126">Implementacje dalsze pojęcia związane z `x:Class` i `x:Subclass` są wykonywane przez określone struktur, co umożliwia definiowanie sposobu połączenia znaczników XAML, znaczników skompilowany i na podstawie CLR kodem modele programowania i modeli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4b01-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="c4b01-127">Każdy framework może mieć własną akcji kompilacji, które udostępnia niektóre działania lub określone składniki, które muszą być zawarte w środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c4b01-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="c4b01-128">W ramach akcji kompilacji można również różnić w zależności od określonego języka środowiska CLR używanej do kodu powiązanego.</span><span class="sxs-lookup"><span data-stu-id="c4b01-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="c4b01-129">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="c4b01-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="c4b01-130">`x:Subclass`można na katalog główny strony lub <xref:System.Windows.Application> głównego definicji aplikacji, który ma już `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="c4b01-131">Deklarowanie `x:Subclass` dla dowolnego elementu innego niż katalog główny strony lub aplikacji lub określanie go, jeśli nie `x:Class` istnieje, powoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c4b01-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="c4b01-132">Tworzenie pochodnych klas pracy prawidłowe `x:Subclass` scenariusza jest dość złożone.</span><span class="sxs-lookup"><span data-stu-id="c4b01-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="c4b01-133">Konieczne może być zbadać plików pośrednich (pliki .g tworzone w folderze obj. projektu przez kompilacji znaczników, z nazwami zawierające .xaml nazwy pliku).</span><span class="sxs-lookup"><span data-stu-id="c4b01-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="c4b01-134">Tych plików pośrednich może pomóc w określeniu źródła niektórych narzędzi programistycznych w dołączonym do klas częściowych w skompilowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4b01-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="c4b01-135">Programy obsługi zdarzeń w klasie pochodnej musi być `internal override` (`Friend Overrides` w [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) w celu zastąpienia klas zastępczych dla programów obsługi, jak utworzony w klasie pośrednie podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c4b01-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="c4b01-136">W przeciwnym razie implementacji klasy pochodnej Ukryj (tle) implementacji klasa pośrednicząca i nie są wywoływane programy obsługi klasa pośrednicząca.</span><span class="sxs-lookup"><span data-stu-id="c4b01-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="c4b01-137">Podczas definiowania zarówno `x:Class` i `x:Subclass`, nie trzeba podać implementacji klasy, która odwołuje się do niego `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="c4b01-138">Musisz podać jego nazwę przy użyciu `x:Class` atrybutu, dzięki czemu kompilator ma pewne wskazówki dotyczące klasy, która tworzy w plikach pośredniego (kompilator nie wybierz nazwę domyślną w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="c4b01-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="c4b01-139">Można nadać `x:Class` klasa implementacji; mimo to nie jest typowym scenariuszem stosowania zarówno `x:Class` i `x:Subclass`.</span><span class="sxs-lookup"><span data-stu-id="c4b01-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b01-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4b01-140">See Also</span></span>  
 [<span data-ttu-id="c4b01-141">x: Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="c4b01-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="c4b01-142">XAML oraz klas niestandardowych dla WPF</span><span class="sxs-lookup"><span data-stu-id="c4b01-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
