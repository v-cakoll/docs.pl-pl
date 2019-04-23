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
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Bezpieczne wzorce konstruktora DependencyObjects
Ogólnie rzecz biorąc Konstruktory klasy nie powinien wywoływać wywołań zwrotnych, takie jak metody wirtualne lub delegatów, ponieważ Konstruktory mogą być wywoływane jako podstawowy inicjowania konstruktora dla klasy pochodnej. Wprowadzanie wirtualnego może odbywać się w stanie inicjowania niekompletne dowolnego danego obiektu. Jednak sam system właściwość wywołania i udostępnia wywołania zwrotne wewnętrznie jako część systemu właściwość zależności. Proste operacji, ponieważ ustawienie wartości właściwości zależności za pomocą <xref:System.Windows.DependencyObject.SetValue%2A> wywołanie potencjalnie zawiera wywołanie zwrotne gdzieś w ustalaniu. Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości w treści konstruktora, który może stać się problemem, jeśli danego typu jest używana jako klasa bazowa zależności. Brak określonego wzorca Implementowanie <xref:System.Windows.DependencyObject> konstruktorów, które pozwala uniknąć określonych problemów z stany właściwości zależności i używaniem wywołania zwrotne, które są opisane tutaj.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Metody wirtualne właściwości systemu  
 Poniższych metod wirtualnych lub wywołań zwrotnych potencjalnie są wywoływane podczas obliczeń z <xref:System.Windows.DependencyObject.SetValue%2A> wywołania, która ustawia wartości właściwości zależności: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Każda z tych metod wirtualnych lub wywołań zwrotnych służy określonego celu rozszerzanie uniwersalność [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości właściwości systemu i zależności. Aby uzyskać więcej informacji na temat korzystania z tych elementów wirtualnych dostosować określenie wartości właściwości, zobacz [zależność wartości wywołania zwrotnego i walidacji](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Vs wymuszania reguł programu FXCop. Elementy wirtualne System właściwości  
 Jeśli używasz narzędzia Microsoft FXCop jako część procesu kompilacji, i albo pochodzi z niektórych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy framework wywołanie konstruktora podstawowego lub implementować własne właściwości zależności w klasach pochodnych, mogą wystąpić określonego Naruszenie reguły programu FXCop. Ciąg nazwy dla tego naruszenia jest następujący:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 To jest reguła, która jest częścią domyślnej publicznej zestawu reguł dla programu FXCop. Co ta reguła może zgłaszać śledzenia za pośrednictwem systemu właściwości zależności, który ostatecznie wywołuje metodę wirtualną systemu właściwość zależności. Naruszenie tej reguły, mogą w dalszym ciągu następować po elemencie następujące wzorce konstruktora zalecane, opisane w tym temacie, więc czasami trzeba wyłączyć lub blokować tej reguły w swojej konfiguracji zestawu reguł programu FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Większość problemów pochodzą z klas pochodnych, nie przy użyciu istniejących klas  
 Problemy zgłaszane przez tę regułę wystąpić, gdy następnie pochodną klasę, która implementuje za pomocą metod wirtualnych, w kolejności ich konstrukcji. Jeśli zapieczętować swojej klasy lub w przeciwnym razie wiedzieć lub wymusić, że klasa nie będzie pochodzi od, zagadnienia omówione i problemów, które uzasadnione reguł programu FXCop nie dotyczyć. Jednak w przypadku tworzenia klasy w taki sposób, że są przeznaczone do służyć jako klay bazowe, na przykład jeśli tworzysz szablonów lub biblioteki formantu można rozwijać, należy przestrzegać wzorców zalecanych w tym miejscu dla konstruktorów.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Konstruktory domyślne muszą zainicjować wszystkie wartości, żądane przez wywołania zwrotne  
 Wystąpienia elementów członkowskich, które są używane przez klasy zastąpienia lub wywołania zwrotne (wywołań zwrotnych na liście w sekcji elementów właściwości systemu wirtualnych) musi zostać zainicjowany w swojej domyślny konstruktor klasy, nawet jeśli niektóre z tych wartości są wypełniane przez "członu real" wartości za pomocą Parametry konstruktory inną niż domyślna.  
  
 Poniższy przykład kodu (i następnych przykładach) jest pseudo -C# przykład narusza tę regułę, która wyjaśnia problem:  
  
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
  
 Kiedy wywołuje kod aplikacji `new MyClass(objectvalue)`, powoduje to wywołanie konstruktora domyślnego i podstawowej klasy konstruktorów. A następnie ustawia `Property1 = object1`, które wywołuje metodę wirtualną `OnPropertyChanged` na będącej właścicielem `MyClass` <xref:System.Windows.DependencyObject>.  Zastąpienie odwołuje się do `_myList`, który ma nie został jeszcze zainicjowany.  
  
 Jednym ze sposobów, aby uniknąć tych problemów jest upewnij się, że wywołania zwrotne używać innych właściwości zależności i że każda właściwość zależności ma jako wartość domyślna ustanowionych jako część jego metadane zarejestrowane.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Bezpieczne wzorce konstruktora  
 Aby uniknąć ryzyka inicjowania niekompletne, jeśli klasa jest używana jako klasa bazowa, wykonaj te wzorce:  
  
#### <a name="default-constructors-calling-base-initialization"></a>Konstruktory domyślne wywołanie inicjalizacji podstawowy  
 Implementuje te konstruktory wywoływania bazowy domyślną:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory inne niż domyślne (wygody), nie pasują żadnych podpisów podstawowy  
 Użycie konstruktorów te parametry można ustawić właściwości zależności podczas inicjowania, należy najpierw wywołać konstruktora domyślnego własne klasy inicjowania, a następnie użyj parametrów, można ustawić właściwości zależności. Te mogą być właściwości zależności definicją klasy lub właściwości zależności dziedziczone z klasy bazowej ale w obu przypadkach należy użyć następującego wzorca:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Konstruktory inne niż domyślne (wygody), odpowiadających podstawowy podpisów  
 Zamiast wywoływania konstruktora bazowego, przy użyciu tego samego parametryzacji, wywołaj ponownie własne klasy domyślnego konstruktora. Nie wywołuj inicjatora podstawowego; Zamiast tego należy wywołać `this()`. Następnie odtworzenia zachować oryginalne zachowanie konstruktora przy użyciu parametrów przekazanych jako wartości ustawienia odpowiednich właściwości. Użyj oryginalnej dokumentacji konstruktora podstawowego, aby uzyskać wskazówki dotyczące określania właściwości, które są poszczególne parametry przeznaczone do zestawu:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Musi być zgodna wszystkich podpisów  
 W przypadkach, w której typ podstawowy ma wiele sygnatur celowo musi być zgodna wszystkich możliwych podpisów przy użyciu implementacji konstruktora własne używającej zalecany wzorzec wywołanie domyślnego konstruktora klasy przed ustawieniem dalsze właściwości.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Ustawianie właściwości zależności za pomocą SetValue  
 Te same wzory zastosowania po ustawieniu właściwości, które nie mają otoki dla wygody ustawienie właściwości i ustaw wartości z <xref:System.Windows.DependencyObject.SetValue%2A>. Wywołania względem <xref:System.Windows.DependencyObject.SetValue%2A> przez parametry konstruktora powinien także wywołać konstruktor domyślny klasy inicjowania.  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Zabezpieczenia właściwości zależności](dependency-property-security.md)
