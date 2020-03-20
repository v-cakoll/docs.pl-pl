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
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Bezpieczne wzorce konstruktora DependencyObjects
Ogólnie rzecz biorąc konstruktory klas nie należy wywoływać wywołania zwrotne, takie jak metody wirtualne lub delegatów, ponieważ konstruktory mogą być wywoływane jako inicjowania podstawowego konstruktorów dla klasy pochodnej. Wprowadzanie wirtualnego może odbywać się w stanie niepełnego inicjowania danego obiektu. Jednak sam system właściwości wywołuje i udostępnia wywołania zwrotne wewnętrznie, jako część systemu właściwości zależności. Tak proste operacji, jak ustawienie wartości <xref:System.Windows.DependencyObject.SetValue%2A> właściwości zależności z wywołaniem potencjalnie zawiera wywołanie zwrotne gdzieś w określaniu. Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości zależności w treści konstruktora, co może stać się problematyczne, jeśli typ jest używany jako klasa podstawowa. Istnieje określony wzorzec <xref:System.Windows.DependencyObject> implementacji konstruktorów, który pozwala uniknąć określonych problemów ze stanami właściwości zależności i nieodłączne wywołania zwrotne, co jest udokumentowane w tym miejscu.  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a>Metody wirtualne systemu właściwości  
 Następujące metody wirtualne lub wywołania zwrotne są <xref:System.Windows.DependencyObject.SetValue%2A> potencjalnie wywoływane podczas obliczeń <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.PropertyChangedCallback>wywołania, które ustawia wartość właściwości zależności: , , <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Każda z tych metod wirtualnych lub wywołania zwrotne służy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] określonego celu w rozwijaniu wszechstronność systemu właściwości i właściwości zależności. Aby uzyskać więcej informacji na temat używania tych wirtualnych do dostosowywania określania wartości właściwości, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności.](dependency-property-callbacks-and-validation.md)  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Wymuszanie reguł FXCop a wirtualne systemu właściwości  
 Jeśli używasz narzędzia Microsoft FXCop jako część procesu kompilacji i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] albo pochodzą z niektórych klas struktury wywołujących konstruktora podstawowego lub zaimplementować własne właściwości zależności na klasy pochodne, może wystąpić naruszenie reguły FXCop określonego. Ciąg nazwy dla tego naruszenia jest:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Jest to reguła, która jest częścią domyślnego zestawu reguł publicznych dla FXCop. Co ta reguła może być raportowanie jest śledzenie za pośrednictwem systemu właściwości zależności, który ostatecznie wywołuje metody wirtualnej systemu właściwości zależności. To naruszenie reguły może nadal pojawiać się nawet po przestrzeganiu zalecanych wzorców konstruktora udokumentowanych w tym temacie, więc może być konieczne wyłączenie lub wyłączenie tej reguły w konfiguracji zestawu reguł FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Większość problemów pochodzi z klas pochodnych, nie używając istniejących klas  
 Problemy zgłaszane przez tę regułę występują, gdy klasa, która implementujesz za pomocą metod wirtualnych w sekwencji konstrukcji jest następnie pochodną. Jeśli uszczelnisz klasę lub w inny sposób wiesz lub wymuszsz, że twoja klasa nie będzie pochodzić z, rozważania wyjaśnione tutaj i problemy, które motywowane regułą FXCop nie mają zastosowania do Ciebie. Jednak jeśli są tworzenie klas w taki sposób, że są one przeznaczone do użycia jako klasy podstawowe, na przykład w przypadku tworzenia szablonów lub rozwijany zestaw biblioteki formantu, należy postępować zgodnie z wzorców zalecanych w tym miejscu dla konstruktorów.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Domyślne konstruktory muszą inicjować wszystkie wartości wymagane przez wywołania zwrotne  
 Wszystkie elementy członkowskie wystąpienia, które są używane przez zastąpienia klasy lub wywołania zwrotne (wywołania zwrotne z listy w sekcji Wirtualne systemu właściwości) muszą być inicjowane w konstruktorze bez parametrów klasy, nawet jeśli niektóre z tych wartości są wypełniane przez "prawdziwe" wartości za pośrednictwem parametrów konstruktorów nieparameterless.  
  
 Poniższy przykładowy kod (i kolejne przykłady) jest przykładem pseudo-C#, który narusza tę regułę i wyjaśnia problem:  
  
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
  
 Gdy wywołano `new MyClass(objectvalue)`kod aplikacji, wywołuje konstruktora bez parametrów i klasy podstawowej konstruktorów. Następnie ustawia `Property1 = object1`, który wywołuje `OnPropertyChanged` metodę wirtualną na posiadanie `MyClass` <xref:System.Windows.DependencyObject>.  Zastąpienie odnosi się do `_myList`, który nie został jeszcze zainicjowany.  
  
 Jednym ze sposobów uniknięcia tych problemów jest upewnienie się, że wywołania zwrotne używają tylko innych właściwości zależności i że każda taka właściwość zależności ma ustaloną wartość domyślną jako część zarejestrowanych metadanych.  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a>Bezpieczne wzory konstruktora  
 Aby uniknąć ryzyka niepełnego inicjowania, jeśli klasa jest używana jako klasa podstawowa, postępuj zgodnie z następującymi wzorcami:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Konstruktory bez parametrów wywołujące inicjowanie podstawowe  
 Zaimplementuj te konstruktory wywołujące domyślne wartości podstawowe:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory inne niż domyślne (wygoda), niepasujące do żadnych podpisów podstawowych  
 Jeśli te konstruktory używają parametrów do ustawiania właściwości zależności w inicjacji, najpierw wywołaj własny konstruktor bez parametrów klasy do inicjowania, a następnie użyj parametrów, aby ustawić właściwości zależności. Mogą to być właściwości zależności zdefiniowane przez klasę lub właściwości zależności dziedziczone z klas podstawowych, ale w obu przypadkach użyj następującego wzorca:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Konstruktory inne niż domyślne (wygoda), które pasują do podpisów podstawowych  
 Zamiast wywoływania konstruktora podstawowego z taką samą parametryzacji, ponownie wywołać własną klasę' konstrukcję bez parametrów. Nie należy wywoływać inicjatora podstawowego; zamiast tego należy `this()`zadzwonić . Następnie odtwórz oryginalne zachowanie konstruktora przy użyciu przekazanych parametrów jako wartości do ustawiania odpowiednich właściwości. Użyj oryginalnej dokumentacji konstruktora podstawowego, aby uzyskać wskazówki dotyczące określania właściwości, które mają ustawić określone parametry:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Musi być zgodna ze wszystkimi podpisami  
 W przypadkach, gdy typ podstawowy ma wiele podpisów, należy celowo dopasować wszystkie możliwe podpisy z implementacją konstruktora, która używa zalecanego wzorca wywoływania konstruktora bez parametrów klasy przed ustawieniem dalej Właściwości.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Ustawianie właściwości zależności za pomocą wartości SetValue  
 Te same wzorce mają zastosowanie, jeśli ustawiasz właściwość, która nie ma <xref:System.Windows.DependencyObject.SetValue%2A>otoki dla wygody ustawiania właściwości, i ustawiasz wartości za pomocą . Wywołania <xref:System.Windows.DependencyObject.SetValue%2A> do tego przechodzą przez parametry konstruktora należy również wywołać klasy' konstruktora bez parametrów do inicjowania.  
  
## <a name="see-also"></a>Zobacz też

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Zabezpieczenie właściwości zależności](dependency-property-security.md)
