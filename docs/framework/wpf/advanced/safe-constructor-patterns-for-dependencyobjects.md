---
title: Bezpieczne wzorce konstruktora DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: ba8b0a48b2b75a9191553392d5ec0a1f66575807
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086731"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="f1356-102">Bezpieczne wzorce konstruktora DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="f1356-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="f1356-103">Ogólnie rzecz biorąc Konstruktory klasy nie powinien wywoływać wywołań zwrotnych, takie jak metody wirtualne lub delegatów, ponieważ Konstruktory mogą być wywoływane jako podstawowy inicjowania konstruktora dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f1356-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="f1356-104">Wprowadzanie wirtualnego może odbywać się w stanie inicjowania niekompletne dowolnego danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1356-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="f1356-105">Jednak sam system właściwość wywołania i udostępnia wywołania zwrotne wewnętrznie jako część systemu właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="f1356-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="f1356-106">Proste operacji, ponieważ ustawienie wartości właściwości zależności za pomocą <xref:System.Windows.DependencyObject.SetValue%2A> wywołanie potencjalnie zawiera wywołanie zwrotne gdzieś w ustalaniu.</span><span class="sxs-lookup"><span data-stu-id="f1356-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="f1356-107">Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości w treści konstruktora, który może stać się problemem, jeśli danego typu jest używana jako klasa bazowa zależności.</span><span class="sxs-lookup"><span data-stu-id="f1356-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="f1356-108">Brak określonego wzorca Implementowanie <xref:System.Windows.DependencyObject> konstruktorów, które pozwala uniknąć określonych problemów z stany właściwości zależności i używaniem wywołania zwrotne, które są opisane tutaj.</span><span class="sxs-lookup"><span data-stu-id="f1356-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="f1356-109">Metody wirtualne właściwości systemu</span><span class="sxs-lookup"><span data-stu-id="f1356-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="f1356-110">Poniższych metod wirtualnych lub wywołań zwrotnych potencjalnie są wywoływane podczas obliczeń z <xref:System.Windows.DependencyObject.SetValue%2A> wywołania, która ustawia wartości właściwości zależności: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1356-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="f1356-111">Każda z tych metod wirtualnych lub wywołań zwrotnych służy określonego celu rozszerzanie uniwersalność [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości właściwości systemu i zależności.</span><span class="sxs-lookup"><span data-stu-id="f1356-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="f1356-112">Aby uzyskać więcej informacji na temat korzystania z tych elementów wirtualnych dostosować określenie wartości właściwości, zobacz [zależność wartości wywołania zwrotnego i walidacji](dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="f1356-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="f1356-113">Vs wymuszania reguł programu FXCop. Elementy wirtualne System właściwości</span><span class="sxs-lookup"><span data-stu-id="f1356-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="f1356-114">Jeśli używasz narzędzia Microsoft FXCop jako część procesu kompilacji, i albo pochodzi z niektórych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy framework wywołanie konstruktora podstawowego lub implementować własne właściwości zależności w klasach pochodnych, mogą wystąpić określonego Naruszenie reguły programu FXCop.</span><span class="sxs-lookup"><span data-stu-id="f1356-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="f1356-115">Ciąg nazwy dla tego naruszenia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="f1356-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="f1356-116">To jest reguła, która jest częścią domyślnej publicznej zestawu reguł dla programu FXCop.</span><span class="sxs-lookup"><span data-stu-id="f1356-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="f1356-117">Co ta reguła może zgłaszać śledzenia za pośrednictwem systemu właściwości zależności, który ostatecznie wywołuje metodę wirtualną systemu właściwość zależności.</span><span class="sxs-lookup"><span data-stu-id="f1356-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="f1356-118">Naruszenie tej reguły, mogą w dalszym ciągu następować po elemencie następujące wzorce konstruktora zalecane, opisane w tym temacie, więc czasami trzeba wyłączyć lub blokować tej reguły w swojej konfiguracji zestawu reguł programu FXCop.</span><span class="sxs-lookup"><span data-stu-id="f1356-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="f1356-119">Większość problemów pochodzą z klas pochodnych, nie przy użyciu istniejących klas</span><span class="sxs-lookup"><span data-stu-id="f1356-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="f1356-120">Problemy zgłaszane przez tę regułę wystąpić, gdy następnie pochodną klasę, która implementuje za pomocą metod wirtualnych, w kolejności ich konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="f1356-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="f1356-121">Jeśli zapieczętować swojej klasy lub w przeciwnym razie wiedzieć lub wymusić, że klasa nie będzie pochodzi od, zagadnienia omówione i problemów, które uzasadnione reguł programu FXCop nie dotyczyć.</span><span class="sxs-lookup"><span data-stu-id="f1356-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="f1356-122">Jednak w przypadku tworzenia klasy w taki sposób, że są przeznaczone do służyć jako klay bazowe, na przykład jeśli tworzysz szablonów lub biblioteki formantu można rozwijać, należy przestrzegać wzorców zalecanych w tym miejscu dla konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="f1356-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="f1356-123">Konstruktory domyślne muszą zainicjować wszystkie wartości, żądane przez wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="f1356-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="f1356-124">Wystąpienia elementów członkowskich, które są używane przez klasy zastąpienia lub wywołania zwrotne (wywołań zwrotnych na liście w sekcji elementów właściwości systemu wirtualnych) musi zostać zainicjowany w swojej domyślny konstruktor klasy, nawet jeśli niektóre z tych wartości są wypełniane przez "członu real" wartości za pomocą Parametry konstruktory inną niż domyślna.</span><span class="sxs-lookup"><span data-stu-id="f1356-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="f1356-125">Poniższy przykład kodu (i następnych przykładach) jest pseudo -C# przykład narusza tę regułę, która wyjaśnia problem:</span><span class="sxs-lookup"><span data-stu-id="f1356-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```  
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
  
 <span data-ttu-id="f1356-126">Kiedy wywołuje kod aplikacji `new MyClass(objectvalue)`, powoduje to wywołanie konstruktora domyślnego i podstawowej klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="f1356-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="f1356-127">A następnie ustawia `Property1 = object1`, które wywołuje metodę wirtualną `OnPropertyChanged` na będącej właścicielem `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="f1356-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="f1356-128">Zastąpienie odwołuje się do `_myList`, który ma nie został jeszcze zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="f1356-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="f1356-129">Jednym ze sposobów, aby uniknąć tych problemów jest upewnij się, że wywołania zwrotne używać innych właściwości zależności i że każda właściwość zależności ma jako wartość domyślna ustanowionych jako część jego metadane zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="f1356-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="f1356-130">Bezpieczne wzorce konstruktora</span><span class="sxs-lookup"><span data-stu-id="f1356-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="f1356-131">Aby uniknąć ryzyka inicjowania niekompletne, jeśli klasa jest używana jako klasa bazowa, wykonaj te wzorce:</span><span class="sxs-lookup"><span data-stu-id="f1356-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="f1356-132">Konstruktory domyślne wywołanie inicjalizacji podstawowy</span><span class="sxs-lookup"><span data-stu-id="f1356-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="f1356-133">Implementuje te konstruktory wywoływania bazowy domyślną:</span><span class="sxs-lookup"><span data-stu-id="f1356-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="f1356-134">Konstruktory inne niż domyślne (wygody), nie pasują żadnych podpisów podstawowy</span><span class="sxs-lookup"><span data-stu-id="f1356-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="f1356-135">Użycie konstruktorów te parametry można ustawić właściwości zależności podczas inicjowania, należy najpierw wywołać konstruktora domyślnego własne klasy inicjowania, a następnie użyj parametrów, można ustawić właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="f1356-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="f1356-136">Te mogą być właściwości zależności definicją klasy lub właściwości zależności dziedziczone z klasy bazowej ale w obu przypadkach należy użyć następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="f1356-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="f1356-137">Konstruktory inne niż domyślne (wygody), odpowiadających podstawowy podpisów</span><span class="sxs-lookup"><span data-stu-id="f1356-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="f1356-138">Zamiast wywoływania konstruktora bazowego, przy użyciu tego samego parametryzacji, wywołaj ponownie własne klasy domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f1356-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="f1356-139">Nie wywołuj inicjatora podstawowego; Zamiast tego należy wywołać `this()`.</span><span class="sxs-lookup"><span data-stu-id="f1356-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="f1356-140">Następnie odtworzenia zachować oryginalne zachowanie konstruktora przy użyciu parametrów przekazanych jako wartości ustawienia odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1356-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="f1356-141">Użyj oryginalnej dokumentacji konstruktora podstawowego, aby uzyskać wskazówki dotyczące określania właściwości, które są poszczególne parametry przeznaczone do zestawu:</span><span class="sxs-lookup"><span data-stu-id="f1356-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="f1356-142">Musi być zgodna wszystkich podpisów</span><span class="sxs-lookup"><span data-stu-id="f1356-142">Must match all signatures</span></span>  
 <span data-ttu-id="f1356-143">W przypadkach, w której typ podstawowy ma wiele sygnatur celowo musi być zgodna wszystkich możliwych podpisów przy użyciu implementacji konstruktora własne używającej zalecany wzorzec wywołanie domyślnego konstruktora klasy przed ustawieniem dalsze właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1356-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="f1356-144">Ustawianie właściwości zależności za pomocą SetValue</span><span class="sxs-lookup"><span data-stu-id="f1356-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="f1356-145">Te same wzory zastosowania po ustawieniu właściwości, które nie mają otoki dla wygody ustawienie właściwości i ustaw wartości z <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1356-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="f1356-146">Wywołania względem <xref:System.Windows.DependencyObject.SetValue%2A> przez parametry konstruktora powinien także wywołać konstruktor domyślny klasy inicjowania.</span><span class="sxs-lookup"><span data-stu-id="f1356-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1356-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1356-147">See also</span></span>

- [<span data-ttu-id="f1356-148">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f1356-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="f1356-149">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f1356-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="f1356-150">Zabezpieczenia właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f1356-150">Dependency Property Security</span></span>](dependency-property-security.md)
