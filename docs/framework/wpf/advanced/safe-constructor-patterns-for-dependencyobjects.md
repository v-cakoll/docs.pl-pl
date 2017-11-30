---
title: Bezpieczne wzorce konstruktora DependencyObjects
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43a38406a3c9cc171944448fce2fa2f70c483baa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Bezpieczne wzorce konstruktora DependencyObjects
Ogólnie rzecz biorąc konstruktorów klasy nie powinny wywoływać wywołań zwrotnych, takich jak metody wirtualne lub delegatów, ponieważ konstruktorów można wywołać jako podstawowy inicjowania konstruktorów dla klasy pochodnej. Wprowadzanie wirtualnej może odbywać się w stanie inicjowania niekompletne dowolnego danego obiektu. Jednak sam system właściwości wywołuje i ujawnia wywołania zwrotne wewnętrznie, jako część systemu właściwości zależności. Prosta operacja jako ustawienie wartości właściwości zależności z <xref:System.Windows.DependencyObject.SetValue%2A> wywołanie potencjalnie zawiera wywołanie zwrotne gdzieś w ustalaniu. Z tego powodu należy zachować ostrożność podczas ustawiania wartości właściwości w treści konstruktora, który może stać się problemem, jeśli z danym typem jest używany jako klasa podstawowa zależności. Brak określonego wzorca wykonywania <xref:System.Windows.DependencyObject> konstruktorów, które pozwala uniknąć określonych problemów z stanów właściwości zależności i związanego z używaniem wywołania zwrotne, które opisano w tym miejscu.  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Metody wirtualne właściwości systemu  
 Następujące metody wirtualne lub wywołań zwrotnych potencjalnie wywoływane podczas obliczenia <xref:System.Windows.DependencyObject.SetValue%2A> wywołanie, która ustawia wartości właściwości zależności: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Każdy z tych metod wirtualnych lub wywołań zwrotnych służy określonego celu w rozwinięciu wszechstronność [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości właściwości systemu i zależności. Aby uzyskać więcej informacji na temat tych elementów wirtualnych umożliwia dostosowywanie określenie wartości właściwości, zobacz [wywołania zwrotne właściwości zależności i sprawdzania poprawności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Vs wymuszania reguł programu FXCop. Elementy wirtualne z systemu właściwości  
 Jeśli używasz narzędzia Microsoft FXCop jako część procesu kompilacji i albo pochodzi z niektórych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy framework wywołanie konstruktora podstawowego, lub zaimplementuj właściwości zależności w klasach pochodnych, mogą wystąpić określonego Naruszenie reguł programu FXCop. Ciąg nazwy dla tego naruszenia jest:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Jest to regułę, która jest częścią domyślnego publicznego zestawu reguł dla programu FXCop. Co ta zasada może być raportowanie śledzenia przez system właściwości zależności, który ostatecznie wywołuje metodę wirtualnego systemu właściwości zależności. Naruszenie tej reguły może być nadal wyświetlana mimo opisane w niniejszym dokumencie, więc należy pominąć tej zasady konfiguracji zestaw reguł programu FXCop lub wyłączyć wzorce zalecane konstruktora.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Większość problemów pochodzą z klas pochodnych, nie za pomocą istniejących klas  
 Problemy zgłoszone przez tę regułę wystąpić, gdy następnie jest pochodną klasy, która implementuje za pomocą metod wirtualnych w jego sekwencji konstrukcji. Jeśli zapieczętować klasy, lub w przeciwnym razie wiedzieć lub wymusić, że klasa zostanie nie pochodzi od, zagadnienia omówione i problemów, które uzasadnione reguł programu FXCop można pominąć. Jednak w przypadku tworzenia klasy w taki sposób, że są przeznaczone do użycia jako klasy podstawowej, na przykład jeśli tworzysz szablonów lub biblioteka rozwijania kontrolek, należy wykonać wzorce tutaj zalecana dla konstruktorów.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Konstruktory domyślne muszą zainicjować wszystkich wartości wymaganych przez wywołań zwrotnych  
 Wystąpienia elementów członkowskich, które są używane przez klasę zastąpienia lub wywołania zwrotne (wywołań zwrotnych na liście w sekcji elementów właściwości systemu wirtualnych) musi zostać zainicjowany w klasa Konstruktor domyślny, nawet jeśli niektóre z tych wartości są wypełniane przez "rzeczywiste" wartości za pośrednictwem Parametry konstruktorów niestandardowy.  
  
 Poniższy przykład kodu (i kolejnych przykładów) jest pseudo-C# przykład narusza tę regułę, która wyjaśnia problem:  
  
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
  
 Gdy wywołuje kod aplikacji `new MyClass(objectvalue)`, powoduje to wywołanie konstruktora domyślnego i base klasy konstruktorów. A następnie ustawia `Property1 = object1`, która wywołuje metodę wirtualną `OnPropertyChanged` na będący właścicielem `MyClass` <xref:System.Windows.DependencyObject>.  Zastąpienie odwołuje się do `_myList`, które ma nie została jeszcze zainicjowana.  
  
 Upewnij się, że wywołania zwrotne używać innych właściwości zależności i że każda właściwość zależności ma wartości domyślnej ustalonych jako część zarejestrowanych metadanych jest jeden sposób, aby uniknąć tych problemów.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Wzorce bezpieczne konstruktora  
 Aby uniknąć ryzyka inicjowania niekompletne, jeśli klasa jest używana jako klasa podstawowa, wykonaj te wzorce:  
  
#### <a name="default-constructors-calling-base-initialization"></a>Konstruktory domyślne wywoływania inicjowania podstawowej  
 Implementuje te konstruktorów wywoływania domyślnego podstawowej:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory (wygody) inne niż domyślne, niezgodni żadnych podpisów podstawowej  
 Użycie konstruktorów te parametry można ustawić właściwości zależności w inicjowaniu, pierwsze wywołanie własne klasy domyślnego konstruktora dla inicjowania, a następnie użyj parametrów można ustawić właściwości zależności. Są może być zdefiniowany przez użytkownika klasę właściwości zależności lub odziedziczona z klasy podstawowe właściwości zależności między w obu przypadkach używają następującego wzorca:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Konstruktory (wygody) inne niż domyślne, zgodnych podstawowej podpisów  
 Zamiast kontaktować się z podstawowej konstruktora o tej samej parametryzacja, wywołaj ponownie własne klasy domyślnego konstruktora. Nie wywołuj inicjatora podstawowego; Zamiast tego należy wywołać `this()`. Następnie odtworzyć oryginalne zachowanie konstruktora przy użyciu przekazanych parametrów jako wartości dla odpowiednich właściwości. Przeznaczenie do oryginalnego dokumentacji konstruktora podstawowego wskazówek dotyczących określania właściwości, które są poszczególnych parametrów można ustawić:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Muszą być zgodne wszystkie podpisy  
 W przypadkach, gdy typ podstawowy ma wiele sygnatur celowo musi odpowiadać wszystkie podpisy możliwe z implementacji konstruktora własny używającej zalecane wzorzec wywołanie domyślnego konstruktora klasy przed ustawieniem dodatkowe właściwości.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Ustawianie właściwości zależności z SetValue  
 Te same wzory zastosowania po ustawieniu właściwości, która nie ma otoki dla wygody ustawienie właściwości i wartości z <xref:System.Windows.DependencyObject.SetValue%2A>. Wywołaniami <xref:System.Windows.DependencyObject.SetValue%2A> przez parametrami konstruktora również powinny wywoływać tej klasy domyślnego konstruktora dla inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości niestandardowe zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Zabezpieczenia właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
