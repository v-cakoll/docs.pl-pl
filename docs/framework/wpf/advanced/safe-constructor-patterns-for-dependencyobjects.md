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
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Bezpieczne wzorce konstruktora DependencyObjects
Ogólnie rzecz biorąc, konstruktory klas nie powinny wywoływać wywołań zwrotnych, takich jak metody wirtualne lub Delegaty, ponieważ konstruktory mogą być wywoływane jako podstawowe inicjowanie konstruktorów dla klasy pochodnej. Wprowadzenie do wirtualnego stanu może być wykonywane z niekompletnym stanem inicjalizacji danego obiektu. Jednak sam system właściwości wywołuje i ujawnia wywołania zwrotne wewnętrznie w ramach systemu właściwości zależności. Jako prostą operację, ponieważ ustawienie wartości właściwości zależności z wywołaniem <xref:System.Windows.DependencyObject.SetValue%2A> potencjalnie może zawierać wywołanie zwrotne w miejscu wyznaczania. Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości zależności w treści konstruktora, które mogą stać się problematyczne, jeśli typ jest używany jako klasa bazowa. Istnieje szczególny wzorzec służący do implementowania konstruktorów <xref:System.Windows.DependencyObject>, które unikają określonych problemów ze Stanami właściwości zależności i nieodłącznymi wywołaniami zwrotnymi, które opisano tutaj.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Metody wirtualne systemu właściwości  
 Następujące metody wirtualne lub wywołania zwrotne są potencjalnie wywoływane podczas obliczeń wywołania <xref:System.Windows.DependencyObject.SetValue%2A>, które ustawia wartość właściwości zależności: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Każda z tych metod wirtualnych lub wywołań zwrotnych służy konkretnie do rozwijania uniwersalności właściwości systemu właściwości [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i zależności. Aby uzyskać więcej informacji na temat sposobu użycia tych wirtualnych do dostosowywania określania wartości właściwości, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Wymuszanie reguł FXCop a wirtualne system właściwości  
 Jeśli używasz narzędzia firmy Microsoft FXCop jako części procesu kompilacji i pochodzą z pewnych klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework wywoływanych przez Konstruktor podstawowy lub zaimplementować własne właściwości zależności w klasach pochodnych, może wystąpić naruszenie zasad FXCop. Ciąg nazwy dla tego naruszenia:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Jest to reguła, która jest częścią domyślnego publicznego zestawu reguł dla FXCop. Ta reguła może być raportowana przez system właściwości zależności, który ostatecznie wywołuje metodę wirtualną zależności systemu właściwości. To naruszenie reguły może nadal występować nawet po zastosowaniu zalecanych wzorców konstruktorów udokumentowanych w tym temacie, więc może być konieczne wyłączenie lub pominięcie reguły w konfiguracji zestawu reguł FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Większość problemów pochodzi z klasy wyprowadzania, nie używając istniejących klas  
 Problemy zgłaszane przez tę regułę występuje, gdy Klasa, która jest zaimplementowana przy użyciu metod wirtualnych w jego sekwencji konstrukcji, pochodzi od. W przypadku zapieczętowania klasy lub poznania lub wymuszenia, że Klasa nie zostanie pobrana z, zagadnienia wyjaśnione w tym miejscu i problemy, które zostały omówione przez regułę FXCop, nie mają zastosowania do użytkownika. Jednakże w przypadku tworzenia klas w taki sposób, aby były one przeznaczone do użycia jako klasy bazowe, na przykład w przypadku tworzenia szablonów lub zestawu bibliotek kontrolek rozszerzalnych należy stosować wzorce zalecane w tym miejscu dla konstruktorów.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Domyślne konstruktory muszą inicjować wszystkie wartości żądane przez wywołania zwrotne  
 Każdy element członkowski wystąpienia, który jest używany przez przesłonięcia klasy lub wywołania zwrotne (wywołania zwrotne z listy w sekcji "wirtualne system właściwości") musi być zainicjowany w konstruktorze bez parametrów klasy, nawet jeśli niektóre z tych wartości są wypełnione wartościami "Real" w parametry konstruktorów bez parametrów.  
  
 Poniższy przykładowy kod (i kolejne przykłady) to pseudo-C# przykład, który narusza tę regułę i wyjaśnia problem:  
  
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
  
 Gdy kod aplikacji wywołuje `new MyClass(objectvalue)`, spowoduje to wywołanie konstruktora bez parametrów i konstruktorów klas bazowych. Następnie ustawia `Property1 = object1`, która wywołuje metodę wirtualną `OnPropertyChanged` do <xref:System.Windows.DependencyObject>będących właścicielem `MyClass`.  Zastąpienie odwołuje się do `_myList`, które nie zostało jeszcze zainicjowane.  
  
 Jednym ze sposobów uniknięcia tych problemów jest upewnienie się, że wywołania zwrotne używają tylko innych właściwości zależności i że każda taka właściwość zależności ma ustaloną wartość domyślną jako część zarejestrowanego metadanych.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Wzorce bezpiecznych konstruktorów  
 Aby uniknąć ryzyka niekompletnej inicjalizacji, jeśli klasa jest używana jako klasa bazowa, wykonaj następujące wzorce:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Konstruktory bez parametrów wywołujące podstawową inicjalizację  
 Zaimplementuj te konstruktory wywołujące podstawową wartość domyślną:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory inne niż domyślne (wygoda), niezgodne z żadnymi podpisami podstawowymi  
 Jeśli te konstruktory używają parametrów do ustawiania właściwości zależności podczas inicjowania, najpierw Wywołaj konstruktora bez parametrów klasy do inicjalizacji, a następnie użyj parametrów, aby ustawić właściwości zależności. Mogą to być właściwości zależności zdefiniowane przez klasę lub właściwości zależności dziedziczone z klas bazowych, ale w obu przypadkach używają następującego wzorca:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Konstruktory inne niż domyślne (wygodne), które pasują do sygnatur podstawowych  
 Zamiast wywołania konstruktora podstawowego z tym samym parametryzacja, należy ponownie wywołać Konstruktor bez parametrów klasy. Nie wywołuj inicjatora podstawowego; Zamiast tego należy wywołać `this()`. Następnie Odtwórz oryginalne zachowanie konstruktora przy użyciu parametrów zakończonych jako wartości dla ustawienia odpowiednich właściwości. Użyj oryginalnej dokumentacji konstruktora podstawowego, aby uzyskać wskazówki dotyczące określania właściwości, które mają być ustawione dla określonych parametrów:  
  
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
 W przypadku, gdy typ podstawowy ma wiele podpisów, należy świadomie dopasować wszystkie możliwe podpisy przy użyciu implementacji konstruktora, która używa zalecanego wzorca wywołania konstruktora bez parametrów klasy przed podjęciem dalszych ustawień aœciwoœci.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Ustawianie właściwości zależności przy użyciu wartości SetValue  
 Te same wzorce są stosowane, jeśli ustawiasz właściwość, która nie ma otoki dla wygody ustawienia właściwości, i ustaw wartości przy użyciu <xref:System.Windows.DependencyObject.SetValue%2A>. Wywołania <xref:System.Windows.DependencyObject.SetValue%2A>, które przechodzą przez parametry konstruktora, powinny również wywołać Konstruktor bez parametrów klasy do inicjacji.  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Zabezpieczenia właściwości zależności](dependency-property-security.md)
