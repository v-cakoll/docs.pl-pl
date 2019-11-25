---
title: Bezpieczne wzorce konstruktora DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 66e380a9428395c772d0dcfe45a995374774aec6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283832"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="61e49-102">Bezpieczne wzorce konstruktora DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="61e49-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="61e49-103">Ogólnie rzecz biorąc, konstruktory klas nie powinny wywoływać wywołań zwrotnych, takich jak metody wirtualne lub Delegaty, ponieważ konstruktory mogą być wywoływane jako podstawowe inicjowanie konstruktorów dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="61e49-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="61e49-104">Wprowadzenie do wirtualnego stanu może być wykonywane z niekompletnym stanem inicjalizacji danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="61e49-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="61e49-105">Jednak sam system właściwości wywołuje i ujawnia wywołania zwrotne wewnętrznie w ramach systemu właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="61e49-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="61e49-106">Jako prostą operację, ponieważ ustawienie wartości właściwości zależności z wywołaniem <xref:System.Windows.DependencyObject.SetValue%2A> potencjalnie może zawierać wywołanie zwrotne w miejscu wyznaczania.</span><span class="sxs-lookup"><span data-stu-id="61e49-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="61e49-107">Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości zależności w treści konstruktora, które mogą stać się problematyczne, jeśli typ jest używany jako klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="61e49-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="61e49-108">Istnieje szczególny wzorzec służący do implementowania konstruktorów <xref:System.Windows.DependencyObject>, które unikają określonych problemów ze Stanami właściwości zależności i nieodłącznymi wywołaniami zwrotnymi, które opisano tutaj.</span><span class="sxs-lookup"><span data-stu-id="61e49-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="61e49-109">Metody wirtualne systemu właściwości</span><span class="sxs-lookup"><span data-stu-id="61e49-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="61e49-110">Następujące metody wirtualne lub wywołania zwrotne są potencjalnie wywoływane podczas obliczeń wywołania <xref:System.Windows.DependencyObject.SetValue%2A>, które ustawia wartość właściwości zależności: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="61e49-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="61e49-111">Każda z tych metod wirtualnych lub wywołań zwrotnych służy konkretnie do rozwijania uniwersalności właściwości systemu właściwości [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i zależności.</span><span class="sxs-lookup"><span data-stu-id="61e49-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="61e49-112">Aby uzyskać więcej informacji na temat sposobu użycia tych wirtualnych do dostosowywania określania wartości właściwości, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="61e49-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="61e49-113">Wymuszanie reguł FXCop a wirtualne system właściwości</span><span class="sxs-lookup"><span data-stu-id="61e49-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="61e49-114">Jeśli używasz narzędzia firmy Microsoft FXCop jako części procesu kompilacji i pochodzą z pewnych klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework wywoływanych przez Konstruktor podstawowy lub zaimplementować własne właściwości zależności w klasach pochodnych, może wystąpić naruszenie zasad FXCop.</span><span class="sxs-lookup"><span data-stu-id="61e49-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="61e49-115">Ciąg nazwy dla tego naruszenia:</span><span class="sxs-lookup"><span data-stu-id="61e49-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="61e49-116">Jest to reguła, która jest częścią domyślnego publicznego zestawu reguł dla FXCop.</span><span class="sxs-lookup"><span data-stu-id="61e49-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="61e49-117">Ta reguła może być raportowana przez system właściwości zależności, który ostatecznie wywołuje metodę wirtualną zależności systemu właściwości.</span><span class="sxs-lookup"><span data-stu-id="61e49-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="61e49-118">To naruszenie reguły może nadal występować nawet po zastosowaniu zalecanych wzorców konstruktorów udokumentowanych w tym temacie, więc może być konieczne wyłączenie lub pominięcie reguły w konfiguracji zestawu reguł FXCop.</span><span class="sxs-lookup"><span data-stu-id="61e49-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="61e49-119">Większość problemów pochodzi z klasy wyprowadzania, nie używając istniejących klas</span><span class="sxs-lookup"><span data-stu-id="61e49-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="61e49-120">Problemy zgłaszane przez tę regułę występuje, gdy Klasa, która jest zaimplementowana przy użyciu metod wirtualnych w jego sekwencji konstrukcji, pochodzi od.</span><span class="sxs-lookup"><span data-stu-id="61e49-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="61e49-121">W przypadku zapieczętowania klasy lub poznania lub wymuszenia, że Klasa nie zostanie pobrana z, zagadnienia wyjaśnione w tym miejscu i problemy, które zostały omówione przez regułę FXCop, nie mają zastosowania do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="61e49-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="61e49-122">Jednakże w przypadku tworzenia klas w taki sposób, aby były one przeznaczone do użycia jako klasy bazowe, na przykład w przypadku tworzenia szablonów lub zestawu bibliotek kontrolek rozszerzalnych należy stosować wzorce zalecane w tym miejscu dla konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="61e49-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="61e49-123">Domyślne konstruktory muszą inicjować wszystkie wartości żądane przez wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="61e49-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="61e49-124">Każdy element członkowski wystąpienia, który jest używany przez przesłonięcia klasy lub wywołania zwrotne (wywołania zwrotne z listy w sekcji "wirtualne system właściwości") musi być zainicjowany w konstruktorze bez parametrów klasy, nawet jeśli niektóre z tych wartości są wypełnione wartościami "Real" w parametry konstruktorów bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="61e49-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="61e49-125">Poniższy przykładowy kod (i kolejne przykłady) to pseudo-C# przykład, który narusza tę regułę i wyjaśnia problem:</span><span class="sxs-lookup"><span data-stu-id="61e49-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```csharp  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 <span data-ttu-id="61e49-126">Gdy kod aplikacji wywołuje `new MyClass(objectvalue)`, spowoduje to wywołanie konstruktora bez parametrów i konstruktorów klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="61e49-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="61e49-127">Następnie ustawia `Property1 = object1`, która wywołuje metodę wirtualną `OnPropertyChanged` do <xref:System.Windows.DependencyObject>będących właścicielem `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="61e49-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="61e49-128">Zastąpienie odwołuje się do `_myList`, które nie zostało jeszcze zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="61e49-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="61e49-129">Jednym ze sposobów uniknięcia tych problemów jest upewnienie się, że wywołania zwrotne używają tylko innych właściwości zależności i że każda taka właściwość zależności ma ustaloną wartość domyślną jako część zarejestrowanego metadanych.</span><span class="sxs-lookup"><span data-stu-id="61e49-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="61e49-130">Wzorce bezpiecznych konstruktorów</span><span class="sxs-lookup"><span data-stu-id="61e49-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="61e49-131">Aby uniknąć ryzyka niekompletnej inicjalizacji, jeśli klasa jest używana jako klasa bazowa, wykonaj następujące wzorce:</span><span class="sxs-lookup"><span data-stu-id="61e49-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="61e49-132">Konstruktory bez parametrów wywołujące podstawową inicjalizację</span><span class="sxs-lookup"><span data-stu-id="61e49-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="61e49-133">Zaimplementuj te konstruktory wywołujące podstawową wartość domyślną:</span><span class="sxs-lookup"><span data-stu-id="61e49-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="61e49-134">Konstruktory inne niż domyślne (wygoda), niezgodne z żadnymi podpisami podstawowymi</span><span class="sxs-lookup"><span data-stu-id="61e49-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="61e49-135">Jeśli te konstruktory używają parametrów do ustawiania właściwości zależności podczas inicjowania, najpierw Wywołaj konstruktora bez parametrów klasy do inicjalizacji, a następnie użyj parametrów, aby ustawić właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="61e49-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="61e49-136">Mogą to być właściwości zależności zdefiniowane przez klasę lub właściwości zależności dziedziczone z klas bazowych, ale w obu przypadkach używają następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="61e49-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="61e49-137">Konstruktory inne niż domyślne (wygodne), które pasują do sygnatur podstawowych</span><span class="sxs-lookup"><span data-stu-id="61e49-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="61e49-138">Zamiast wywołania konstruktora podstawowego z tym samym parametryzacja, należy ponownie wywołać Konstruktor bez parametrów klasy.</span><span class="sxs-lookup"><span data-stu-id="61e49-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="61e49-139">Nie wywołuj inicjatora podstawowego; Zamiast tego należy wywołać `this()`.</span><span class="sxs-lookup"><span data-stu-id="61e49-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="61e49-140">Następnie Odtwórz oryginalne zachowanie konstruktora przy użyciu parametrów zakończonych jako wartości dla ustawienia odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="61e49-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="61e49-141">Użyj oryginalnej dokumentacji konstruktora podstawowego, aby uzyskać wskazówki dotyczące określania właściwości, które mają być ustawione dla określonych parametrów:</span><span class="sxs-lookup"><span data-stu-id="61e49-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="61e49-142">Musi być zgodna ze wszystkimi podpisami</span><span class="sxs-lookup"><span data-stu-id="61e49-142">Must match all signatures</span></span>  
 <span data-ttu-id="61e49-143">W przypadku, gdy typ podstawowy ma wiele podpisów, należy świadomie dopasować wszystkie możliwe podpisy przy użyciu implementacji konstruktora, która używa zalecanego wzorca wywołania konstruktora bez parametrów klasy przed podjęciem dalszych ustawień aœciwoœci.</span><span class="sxs-lookup"><span data-stu-id="61e49-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="61e49-144">Ustawianie właściwości zależności przy użyciu wartości SetValue</span><span class="sxs-lookup"><span data-stu-id="61e49-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="61e49-145">Te same wzorce są stosowane, jeśli ustawiasz właściwość, która nie ma otoki dla wygody ustawienia właściwości, i ustaw wartości przy użyciu <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="61e49-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="61e49-146">Wywołania <xref:System.Windows.DependencyObject.SetValue%2A>, które przechodzą przez parametry konstruktora, powinny również wywołać Konstruktor bez parametrów klasy do inicjacji.</span><span class="sxs-lookup"><span data-stu-id="61e49-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e49-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61e49-147">See also</span></span>

- [<span data-ttu-id="61e49-148">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="61e49-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="61e49-149">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="61e49-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="61e49-150">Zabezpieczenia właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="61e49-150">Dependency Property Security</span></span>](dependency-property-security.md)
