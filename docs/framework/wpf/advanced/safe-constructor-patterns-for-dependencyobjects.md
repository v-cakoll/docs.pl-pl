---
title: Bezpieczne wzorce konstruktora DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 03615c1c49f2acf2a7c7f0910860f36de0a4f2d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="35338-102">Bezpieczne wzorce konstruktora DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="35338-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="35338-103">Ogólnie rzecz biorąc konstruktorów klasy nie powinny wywoływać wywołań zwrotnych, takich jak metody wirtualne lub delegatów, ponieważ konstruktorów można wywołać jako podstawowy inicjowania konstruktorów dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="35338-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="35338-104">Wprowadzanie wirtualnej może odbywać się w stanie inicjowania niekompletne dowolnego danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="35338-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="35338-105">Jednak sam system właściwości wywołuje i ujawnia wywołania zwrotne wewnętrznie, jako część systemu właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="35338-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="35338-106">Prosta operacja jako ustawienie wartości właściwości zależności z <xref:System.Windows.DependencyObject.SetValue%2A> wywołanie potencjalnie zawiera wywołanie zwrotne gdzieś w ustalaniu.</span><span class="sxs-lookup"><span data-stu-id="35338-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="35338-107">Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości w treści konstruktora, który może stać się problemem, jeśli z danym typem jest używany jako klasa podstawowa zależności.</span><span class="sxs-lookup"><span data-stu-id="35338-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="35338-108">Brak określonego wzorca wykonywania <xref:System.Windows.DependencyObject> konstruktorów, które pozwala uniknąć określonych problemów z stanów właściwości zależności i związanego z używaniem wywołania zwrotne, które opisano w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="35338-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="35338-109">Metody wirtualne właściwości systemu</span><span class="sxs-lookup"><span data-stu-id="35338-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="35338-110">Następujące metody wirtualne lub wywołań zwrotnych potencjalnie wywoływane podczas obliczenia <xref:System.Windows.DependencyObject.SetValue%2A> wywołanie, która ustawia wartości właściwości zależności: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="35338-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="35338-111">Każdy z tych metod wirtualnych lub wywołań zwrotnych służy określonego celu w rozwinięciu wszechstronność [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości właściwości systemu i zależności.</span><span class="sxs-lookup"><span data-stu-id="35338-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="35338-112">Aby uzyskać więcej informacji na temat tych elementów wirtualnych umożliwia dostosowywanie określenie wartości właściwości, zobacz [wywołania zwrotne właściwości zależności i sprawdzania poprawności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="35338-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="35338-113">Vs wymuszania reguł programu FXCop. Elementy wirtualne z systemu właściwości</span><span class="sxs-lookup"><span data-stu-id="35338-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="35338-114">Jeśli używasz narzędzia Microsoft FXCop jako część procesu kompilacji i albo pochodzi z niektórych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy framework wywołanie konstruktora podstawowego, lub zaimplementuj właściwości zależności w klasach pochodnych, mogą wystąpić określonego Naruszenie reguł programu FXCop.</span><span class="sxs-lookup"><span data-stu-id="35338-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="35338-115">Ciąg nazwy dla tego naruszenia jest:</span><span class="sxs-lookup"><span data-stu-id="35338-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="35338-116">Jest to regułę, która jest częścią domyślnego publicznego zestawu reguł dla programu FXCop.</span><span class="sxs-lookup"><span data-stu-id="35338-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="35338-117">Co ta zasada może być raportowanie śledzenia przez system właściwości zależności, który ostatecznie wywołuje metodę wirtualnego systemu właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="35338-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="35338-118">Naruszenie tej reguły może być nadal wyświetlana mimo opisane w niniejszym dokumencie, więc należy pominąć tej zasady konfiguracji zestaw reguł programu FXCop lub wyłączyć wzorce zalecane konstruktora.</span><span class="sxs-lookup"><span data-stu-id="35338-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="35338-119">Większość problemów pochodzą z klas pochodnych, nie za pomocą istniejących klas</span><span class="sxs-lookup"><span data-stu-id="35338-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="35338-120">Problemy zgłoszone przez tę regułę wystąpić, gdy następnie jest pochodną klasy, która implementuje za pomocą metod wirtualnych w jego sekwencji konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="35338-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="35338-121">Jeśli zapieczętować klasy, lub w przeciwnym razie wiedzieć lub wymusić, że klasa zostanie nie pochodzi od, zagadnienia omówione i problemów, które uzasadnione reguł programu FXCop można pominąć.</span><span class="sxs-lookup"><span data-stu-id="35338-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="35338-122">Jednak w przypadku tworzenia klasy w taki sposób, że są przeznaczone do użycia jako klasy podstawowej, na przykład jeśli tworzysz szablonów lub biblioteka rozwijania kontrolek, należy wykonać wzorce tutaj zalecana dla konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="35338-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="35338-123">Konstruktory domyślne muszą zainicjować wszystkich wartości wymaganych przez wywołań zwrotnych</span><span class="sxs-lookup"><span data-stu-id="35338-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="35338-124">Wystąpienia elementów członkowskich, które są używane przez klasę zastąpienia lub wywołania zwrotne (wywołań zwrotnych na liście w sekcji elementów właściwości systemu wirtualnych) musi zostać zainicjowany w klasa Konstruktor domyślny, nawet jeśli niektóre z tych wartości są wypełniane przez "rzeczywiste" wartości za pośrednictwem Parametry konstruktorów niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="35338-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="35338-125">Poniższy przykład kodu (i kolejnych przykładów) jest pseudo-C# przykład narusza tę regułę, która wyjaśnia problem:</span><span class="sxs-lookup"><span data-stu-id="35338-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="35338-126">Gdy wywołuje kod aplikacji `new MyClass(objectvalue)`, powoduje to wywołanie konstruktora domyślnego i base klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="35338-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="35338-127">A następnie ustawia `Property1 = object1`, która wywołuje metodę wirtualną `OnPropertyChanged` na będący właścicielem `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="35338-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="35338-128">Zastąpienie odwołuje się do `_myList`, które ma nie została jeszcze zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="35338-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="35338-129">Upewnij się, że wywołania zwrotne używać innych właściwości zależności i że każda właściwość zależności ma wartości domyślnej ustalonych jako część zarejestrowanych metadanych jest jeden sposób, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="35338-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="35338-130">Wzorce bezpieczne konstruktora</span><span class="sxs-lookup"><span data-stu-id="35338-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="35338-131">Aby uniknąć ryzyka inicjowania niekompletne, jeśli klasa jest używana jako klasa podstawowa, wykonaj te wzorce:</span><span class="sxs-lookup"><span data-stu-id="35338-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="35338-132">Konstruktory domyślne wywoływania inicjowania podstawowej</span><span class="sxs-lookup"><span data-stu-id="35338-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="35338-133">Implementuje te konstruktorów wywoływania domyślnego podstawowej:</span><span class="sxs-lookup"><span data-stu-id="35338-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="35338-134">Konstruktory (wygody) inne niż domyślne, niezgodni żadnych podpisów podstawowej</span><span class="sxs-lookup"><span data-stu-id="35338-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="35338-135">Użycie konstruktorów te parametry można ustawić właściwości zależności w inicjowaniu, pierwsze wywołanie własne klasy domyślnego konstruktora dla inicjowania, a następnie użyj parametrów można ustawić właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="35338-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="35338-136">Są może być zdefiniowany przez użytkownika klasę właściwości zależności lub odziedziczona z klasy podstawowe właściwości zależności między w obu przypadkach używają następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="35338-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="35338-137">Konstruktory (wygody) inne niż domyślne, zgodnych podstawowej podpisów</span><span class="sxs-lookup"><span data-stu-id="35338-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="35338-138">Zamiast kontaktować się z podstawowej konstruktora o tej samej parametryzacja, wywołaj ponownie własne klasy domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="35338-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="35338-139">Nie wywołuj inicjatora podstawowego; Zamiast tego należy wywołać `this()`.</span><span class="sxs-lookup"><span data-stu-id="35338-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="35338-140">Następnie odtworzyć oryginalne zachowanie konstruktora przy użyciu przekazanych parametrów jako wartości dla odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="35338-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="35338-141">Przeznaczenie do oryginalnego dokumentacji konstruktora podstawowego wskazówek dotyczących określania właściwości, które są poszczególnych parametrów można ustawić:</span><span class="sxs-lookup"><span data-stu-id="35338-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="35338-142">Muszą być zgodne wszystkie podpisy</span><span class="sxs-lookup"><span data-stu-id="35338-142">Must match all signatures</span></span>  
 <span data-ttu-id="35338-143">W przypadkach, gdy typ podstawowy ma wiele sygnatur celowo musi odpowiadać wszystkie podpisy możliwe z implementacji konstruktora własny używającej zalecane wzorzec wywołanie domyślnego konstruktora klasy przed ustawieniem dodatkowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="35338-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="35338-144">Ustawianie właściwości zależności z SetValue</span><span class="sxs-lookup"><span data-stu-id="35338-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="35338-145">Te same wzory zastosowania po ustawieniu właściwości, która nie ma otoki dla wygody ustawienie właściwości i wartości z <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="35338-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="35338-146">Wywołaniami <xref:System.Windows.DependencyObject.SetValue%2A> przez parametrami konstruktora również powinny wywoływać tej klasy domyślnego konstruktora dla inicjowania.</span><span class="sxs-lookup"><span data-stu-id="35338-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35338-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35338-147">See Also</span></span>  
 [<span data-ttu-id="35338-148">Niestandardowe właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="35338-148">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="35338-149">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="35338-149">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="35338-150">Zabezpieczenia właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="35338-150">Dependency Property Security</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
