---
title: Bezpieczne wzorce konstruktora DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 6d6ff444b99ca893e687731c56a48ea3ac072dd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187230"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="53fc4-102">Bezpieczne wzorce konstruktora DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="53fc4-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="53fc4-103">Ogólnie rzecz biorąc konstruktory klas nie należy wywoływać wywołania zwrotne, takie jak metody wirtualne lub delegatów, ponieważ konstruktory mogą być wywoływane jako inicjowania podstawowego konstruktorów dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="53fc4-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="53fc4-104">Wprowadzanie wirtualnego może odbywać się w stanie niepełnego inicjowania danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="53fc4-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="53fc4-105">Jednak sam system właściwości wywołuje i udostępnia wywołania zwrotne wewnętrznie, jako część systemu właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="53fc4-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="53fc4-106">Tak proste operacji, jak ustawienie wartości <xref:System.Windows.DependencyObject.SetValue%2A> właściwości zależności z wywołaniem potencjalnie zawiera wywołanie zwrotne gdzieś w określaniu.</span><span class="sxs-lookup"><span data-stu-id="53fc4-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="53fc4-107">Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości zależności w treści konstruktora, co może stać się problematyczne, jeśli typ jest używany jako klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="53fc4-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="53fc4-108">Istnieje określony wzorzec <xref:System.Windows.DependencyObject> implementacji konstruktorów, który pozwala uniknąć określonych problemów ze stanami właściwości zależności i nieodłączne wywołania zwrotne, co jest udokumentowane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="53fc4-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a><span data-ttu-id="53fc4-109">Metody wirtualne systemu właściwości</span><span class="sxs-lookup"><span data-stu-id="53fc4-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="53fc4-110">Następujące metody wirtualne lub wywołania zwrotne są <xref:System.Windows.DependencyObject.SetValue%2A> potencjalnie wywoływane podczas obliczeń <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.PropertyChangedCallback>wywołania, które ustawia wartość właściwości zależności: , , <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="53fc4-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="53fc4-111">Każda z tych metod wirtualnych lub wywołania zwrotne służy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] określonego celu w rozwijaniu wszechstronność systemu właściwości i właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="53fc4-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="53fc4-112">Aby uzyskać więcej informacji na temat używania tych wirtualnych do dostosowywania określania wartości właściwości, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności.](dependency-property-callbacks-and-validation.md)</span><span class="sxs-lookup"><span data-stu-id="53fc4-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="53fc4-113">Wymuszanie reguł FXCop a wirtualne systemu właściwości</span><span class="sxs-lookup"><span data-stu-id="53fc4-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="53fc4-114">Jeśli używasz narzędzia Microsoft FXCop jako część procesu kompilacji i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] albo pochodzą z niektórych klas struktury wywołujących konstruktora podstawowego lub zaimplementować własne właściwości zależności na klasy pochodne, może wystąpić naruszenie reguły FXCop określonego.</span><span class="sxs-lookup"><span data-stu-id="53fc4-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="53fc4-115">Ciąg nazwy dla tego naruszenia jest:</span><span class="sxs-lookup"><span data-stu-id="53fc4-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="53fc4-116">Jest to reguła, która jest częścią domyślnego zestawu reguł publicznych dla FXCop.</span><span class="sxs-lookup"><span data-stu-id="53fc4-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="53fc4-117">Co ta reguła może być raportowanie jest śledzenie za pośrednictwem systemu właściwości zależności, który ostatecznie wywołuje metody wirtualnej systemu właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="53fc4-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="53fc4-118">To naruszenie reguły może nadal pojawiać się nawet po przestrzeganiu zalecanych wzorców konstruktora udokumentowanych w tym temacie, więc może być konieczne wyłączenie lub wyłączenie tej reguły w konfiguracji zestawu reguł FXCop.</span><span class="sxs-lookup"><span data-stu-id="53fc4-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="53fc4-119">Większość problemów pochodzi z klas pochodnych, nie używając istniejących klas</span><span class="sxs-lookup"><span data-stu-id="53fc4-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="53fc4-120">Problemy zgłaszane przez tę regułę występują, gdy klasa, która implementujesz za pomocą metod wirtualnych w sekwencji konstrukcji jest następnie pochodną.</span><span class="sxs-lookup"><span data-stu-id="53fc4-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="53fc4-121">Jeśli uszczelnisz klasę lub w inny sposób wiesz lub wymuszsz, że twoja klasa nie będzie pochodzić z, rozważania wyjaśnione tutaj i problemy, które motywowane regułą FXCop nie mają zastosowania do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="53fc4-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="53fc4-122">Jednak jeśli są tworzenie klas w taki sposób, że są one przeznaczone do użycia jako klasy podstawowe, na przykład w przypadku tworzenia szablonów lub rozwijany zestaw biblioteki formantu, należy postępować zgodnie z wzorców zalecanych w tym miejscu dla konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="53fc4-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="53fc4-123">Domyślne konstruktory muszą inicjować wszystkie wartości wymagane przez wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="53fc4-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="53fc4-124">Wszystkie elementy członkowskie wystąpienia, które są używane przez zastąpienia klasy lub wywołania zwrotne (wywołania zwrotne z listy w sekcji Wirtualne systemu właściwości) muszą być inicjowane w konstruktorze bez parametrów klasy, nawet jeśli niektóre z tych wartości są wypełniane przez "prawdziwe" wartości za pośrednictwem parametrów konstruktorów nieparameterless.</span><span class="sxs-lookup"><span data-stu-id="53fc4-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="53fc4-125">Poniższy przykładowy kod (i kolejne przykłady) jest przykładem pseudo-C#, który narusza tę regułę i wyjaśnia problem:</span><span class="sxs-lookup"><span data-stu-id="53fc4-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="53fc4-126">Gdy wywołano `new MyClass(objectvalue)`kod aplikacji, wywołuje konstruktora bez parametrów i klasy podstawowej konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="53fc4-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="53fc4-127">Następnie ustawia `Property1 = object1`, który wywołuje `OnPropertyChanged` metodę wirtualną na posiadanie `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="53fc4-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="53fc4-128">Zastąpienie odnosi się do `_myList`, który nie został jeszcze zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="53fc4-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="53fc4-129">Jednym ze sposobów uniknięcia tych problemów jest upewnienie się, że wywołania zwrotne używają tylko innych właściwości zależności i że każda taka właściwość zależności ma ustaloną wartość domyślną jako część zarejestrowanych metadanych.</span><span class="sxs-lookup"><span data-stu-id="53fc4-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a><span data-ttu-id="53fc4-130">Bezpieczne wzory konstruktora</span><span class="sxs-lookup"><span data-stu-id="53fc4-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="53fc4-131">Aby uniknąć ryzyka niepełnego inicjowania, jeśli klasa jest używana jako klasa podstawowa, postępuj zgodnie z następującymi wzorcami:</span><span class="sxs-lookup"><span data-stu-id="53fc4-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="53fc4-132">Konstruktory bez parametrów wywołujące inicjowanie podstawowe</span><span class="sxs-lookup"><span data-stu-id="53fc4-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="53fc4-133">Zaimplementuj te konstruktory wywołujące domyślne wartości podstawowe:</span><span class="sxs-lookup"><span data-stu-id="53fc4-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="53fc4-134">Konstruktory inne niż domyślne (wygoda), niepasujące do żadnych podpisów podstawowych</span><span class="sxs-lookup"><span data-stu-id="53fc4-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="53fc4-135">Jeśli te konstruktory używają parametrów do ustawiania właściwości zależności w inicjacji, najpierw wywołaj własny konstruktor bez parametrów klasy do inicjowania, a następnie użyj parametrów, aby ustawić właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="53fc4-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="53fc4-136">Mogą to być właściwości zależności zdefiniowane przez klasę lub właściwości zależności dziedziczone z klas podstawowych, ale w obu przypadkach użyj następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="53fc4-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="53fc4-137">Konstruktory inne niż domyślne (wygoda), które pasują do podpisów podstawowych</span><span class="sxs-lookup"><span data-stu-id="53fc4-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="53fc4-138">Zamiast wywoływania konstruktora podstawowego z taką samą parametryzacji, ponownie wywołać własną klasę' konstrukcję bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="53fc4-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="53fc4-139">Nie należy wywoływać inicjatora podstawowego; zamiast tego należy `this()`zadzwonić .</span><span class="sxs-lookup"><span data-stu-id="53fc4-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="53fc4-140">Następnie odtwórz oryginalne zachowanie konstruktora przy użyciu przekazanych parametrów jako wartości do ustawiania odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="53fc4-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="53fc4-141">Użyj oryginalnej dokumentacji konstruktora podstawowego, aby uzyskać wskazówki dotyczące określania właściwości, które mają ustawić określone parametry:</span><span class="sxs-lookup"><span data-stu-id="53fc4-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="53fc4-142">Musi być zgodna ze wszystkimi podpisami</span><span class="sxs-lookup"><span data-stu-id="53fc4-142">Must match all signatures</span></span>  
 <span data-ttu-id="53fc4-143">W przypadkach, gdy typ podstawowy ma wiele podpisów, należy celowo dopasować wszystkie możliwe podpisy z implementacją konstruktora, która używa zalecanego wzorca wywoływania konstruktora bez parametrów klasy przed ustawieniem dalej Właściwości.</span><span class="sxs-lookup"><span data-stu-id="53fc4-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="53fc4-144">Ustawianie właściwości zależności za pomocą wartości SetValue</span><span class="sxs-lookup"><span data-stu-id="53fc4-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="53fc4-145">Te same wzorce mają zastosowanie, jeśli ustawiasz właściwość, która nie ma <xref:System.Windows.DependencyObject.SetValue%2A>otoki dla wygody ustawiania właściwości, i ustawiasz wartości za pomocą .</span><span class="sxs-lookup"><span data-stu-id="53fc4-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="53fc4-146">Wywołania <xref:System.Windows.DependencyObject.SetValue%2A> do tego przechodzą przez parametry konstruktora należy również wywołać klasy' konstruktora bez parametrów do inicjowania.</span><span class="sxs-lookup"><span data-stu-id="53fc4-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fc4-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53fc4-147">See also</span></span>

- [<span data-ttu-id="53fc4-148">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="53fc4-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="53fc4-149">Przegląd Właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="53fc4-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="53fc4-150">Zabezpieczenie właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="53fc4-150">Dependency Property Security</span></span>](dependency-property-security.md)
