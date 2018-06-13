---
title: Programowanie zorientowane obiektowo (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: e8936eb9031ef68ea333835d8433e1ba1a45990f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655970"
---
# <a name="object-oriented-programming-visual-basic"></a>Programowanie zorientowane obiektowo (Visual Basic)
Programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizm Visual Basic zapewnia pełną obsługę.  
  
 *Hermetyzacja* oznacza, że grupy powiązane właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.  
  
 *Dziedziczenie* opisuje może tworzyć nowe klasy oparte na istniejącej klasy.  
  
 *Polimorfizm* oznacza, że może mieć wielu klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.  
  
 W tej sekcji opisano następujące kwestie:  
  
-   [Klasy i obiekty](#classes-and-objects)  
  
    -   [Członkowie klasy](#members)  
  
         [Właściwości i pola](#properties-and-fields)  
  
         [Metody](#methods)  
  
         [Konstruktory](#constructors)  
  
         [Destruktory](#destructors)  
  
         [Zdarzenia](#events)  
  
         [Klasy zagnieżdżone](#nested-classes)  
  
    -   [Modyfikatory dostępu i poziomy dostępu](#access-modifiers-and-access-levels)  
  
    -   [Utworzenie wystąpienia klasy](#instantiating-classes)  
  
    -   [Udostępniony klas i członków](#shared-classes-and-members)  
  
    -   [Typy anonimowe](#anonymous-types)  
  
-   [Dziedziczenie](#inheritance)  
  
    -   [Zastępowanie elementów członkowskich](#overriding-members)  
  
-   [Interfejsy](#interfaces)  
  
-   [Typy ogólne](#generics)  
  
-   [Delegaci](#delegates)  
  
## <a name="classes-and-objects"></a>Klasy i obiekty  
Warunki *klasy* i *obiektu* są czasami używane zamiennie, ale w rzeczywistości opisano klasy *typu* obiektów, gdy obiekty są użyteczne  *wystąpienia* klas. Dlatego utworzenie obiektu jest nazywany *wystąpienia*. Przy użyciu odpowiednio planu, klasa to umożliwi, a obiekt jest budynku z tego planu.

Aby zdefiniować klasy:

```vb  
Class SampleClass
End Class
```

Visual Basic dostarcza również światła wersję klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i chcesz używać zbyt dużej ilości pamięci do tego.

Aby zdefiniować strukturę:  

```vb
Structure SampleStructure
End Structure
```

Aby uzyskać więcej informacji, zobacz:

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)

- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Członkowie klasy
Każda klasa może mieć różne *klasy elementów członkowskich* zawierające właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnych klas i obiektów.

#### <a name="properties-and-fields"></a>Właściwości i pola
Pola i właściwości reprezentują informacje, która zawiera obiekt. Pola są podobne do zmiennych, ponieważ może być odczytany lub ustawić bezpośrednio.

Aby zdefiniować pola:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Właściwości mają get i ustaw procedur, które zapewniają większą kontrolę w sposób ustawiona lub zwrócona wartości.

Visual Basic służy do utworzenia prywatnej pola do przechowywania wartości właściwości lub użyj tak zwane właściwości zaimplementowane automatycznie utworzyć w tym polu automatycznie w tle, które zapewniają podstawowa logika procedury właściwości.

Aby zdefiniować właściwości zaimplementowane automatycznie:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Jeśli musisz wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawowa logika do przechowywania i pobierania jej:

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

Większość właściwości mają metody lub procedury zarówno Ustawianie i pobieranie wartości właściwości. Można jednak utworzyć właściwości tylko do odczytu lub w trybie tylko do zapisu, aby uniemożliwić ich modyfikacji lub odczytu. W języku Visual Basic można użyć `ReadOnly` i `WriteOnly` słów kluczowych. Jednak automatycznie implementowane właściwości nie może być tylko do odczytu lub w trybie tylko do zapisu.

Aby uzyskać więcej informacji, zobacz:
  
-   [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a>Metody  
 A *metody* to operacja, którą można wykonać obiektu.  

> [!NOTE]
>  W języku Visual Basic, istnieją dwa sposoby tworzenia metody: `Sub` używana jest instrukcja, jeśli metoda nie zwraca wartości; `Function` używana jest instrukcja, jeśli metoda zwróci wartość.

Aby zdefiniować metody klasy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Klasa może mieć wielu implementacji lub *przeciążenia*, metody różne liczby parametrów ani typów parametrów.

Aby można było przeciążyć metodę:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

W większości przypadków należy zadeklarować metody w ramach definicji klasy. Jednak obsługuje również Visual Basic *metody rozszerzenia* umożliwiające dodawanie metody do istniejącej klasy poza rzeczywiste definicji klasy.

Aby uzyskać więcej informacji, zobacz:

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a>Konstruktorów  
Konstruktory są metody klasy, które są wykonywane automatycznie, gdy utworzono obiekt danego typu. Konstruktory zainicjować zazwyczaj elementy członkowskie danych nowego obiektu. Konstruktor można uruchomić tylko raz, podczas tworzenia klasy. Ponadto w Konstruktorze kod zawsze uruchamiany przed innymi kod w klasie. Jednak w taki sam sposób jak w przypadku innych metod, można utworzyć wielu przeciążeń konstruktora.

Aby zdefiniować konstruktora dla klasy:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

Aby uzyskać więcej informacji, zobacz: [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory
Destruktory służą do destruct wystąpień klas. W programie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i wersji pamięci dla zarządzanych obiektów w aplikacji. Jednakże nadal może być konieczne destruktory Aby oczyścić wszelkie niezarządzane zasoby, tworzonych przez aplikację. Może istnieć tylko jeden destruktora dla klasy.

Aby uzyskać więcej informacji na temat destruktory i wyrzucanie elementów bezużytecznych w programie .NET Framework, zobacz [wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Zdarzenia
Zdarzenia włączyć klasę lub obiekt, aby powiadomić innych grup lub obiektów, kiedy coś odsetek występuje. Klasa, która wysyła (lub zgłasza) zdarzenia jest nazywany *wydawcy* i klasy, które odbierać (lub dojścia) zdarzenia są nazywane *subskrybentów*. Aby uzyskać więcej informacji o zdarzeniach, sposób ich pojawienia się i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenia, użyj [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).

- Aby wywołać zdarzenia, użyj [RaiseEvent — instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Aby określić przy użyciu na deklaratywne procedury obsługi zdarzeń, użyj [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrukcji i [obsługuje](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.

- Aby mieć możliwość dynamicznego dodawania, usuwania i zmień skojarzone ze zdarzeniem programu obsługi zdarzeń, należy użyć [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md) i [RemoveHandler — instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md) razem z [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Klasy zagnieżdżone  
Nosi nazwę klasy zdefiniowanej w klasie innej *zagnieżdżonych*. Domyślnie zagnieżdżona klasa jest prywatne.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Można utworzyć wystąpienia klasy zagnieżdżonej, należy użyć nazwy klasy kontenera znak kropki (.) i po niej nazwę klasy zagnieżdżonej:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modyfikatory dostępu i poziomy dostępu  
Wszystkie klasy i elementów członkowskich klasy można określić poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.

Dostępne są następujące modyfikatorów dostępu:

|Modyfikator Visual Basic|Definicja|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|Typ lub element członkowski jest możliwy przez inny kod, w tym samym zestawie lub innego zestawu, który odwołuje się on.|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy.|
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy lub w klasie pochodnej.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Typ lub element członkowski jest możliwy przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.|
|`Protected Friend`|Typ lub element członkowski jest dostępna przez dowolny kod w tym samym zestawie lub dowolnej klasy pochodnej w innym zestawie.|

Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Utworzenie wystąpienia klasy  
Do utworzenia obiektu, należy utworzyć wystąpienia klasy lub utworzyć wystąpienia klasy.

```vb
Dim sampleObject as New SampleClass()
```

Po utworzenie wystąpienia klasy, można przypisać wartości do właściwości i pola wystąpienia i wywołania metody klasy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatory obiektów:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz:

- [Operator New](../../../visual-basic/language-reference/operators/new-operator.md)

- [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <a name="Static"></a> Udostępniony klas i członków  
 Udostępnionego elementu członkowskiego klasy jest właściwość, procedura lub pola, które jest współużytkowana przez wszystkie wystąpienia klasy.  
  
 Aby zdefiniować udostępnionego elementu członkowskiego:  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 Aby uzyskać dostęp do udostępnionego elementu członkowskiego, użyj nazwy klasy bez tworzenia obiektu tej klasy:  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 Udostępniony moduły w języku Visual Basic udostępnionego tylko elementy członkowskie i nie można utworzyć wystąpienia. Udostępniane elementy członkowskie także nie może uzyskać dostępu właściwości nieudostępnione, pola lub metody  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a>Typy anonimowe  
Typy anonimowe umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma używać nazwy i zawiera właściwości, które określisz w odwołaniu do obiektu.

Można utworzyć wystąpienia typu anonimowego:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dziedziczenie
Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa rozszerza i modyfikuje zachowanie, który jest zdefiniowany w innej klasy. Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*, i nosi nazwę klasy, która dziedziczy tych członków *klasy*. Jednak wszystkie klasy w Visual Basic niejawnie dziedziczyć <xref:System.Object> klasy, która obsługuje hierarchii klas .NET i udostępnia usługi niskiego poziomu dla wszystkich klas.

> [!NOTE]
>  Visual Basic nie obsługuje wielu dziedziczenia. Oznacza to można określić tylko jedną klasę podstawową dla klasy pochodnej.

Dziedziczenie z klasy podstawowej:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Domyślnie wszystkie klasy mogą być dziedziczone. Jednak można określić, czy nie mogą być używane jako klasę podstawową klasy lub utworzyć klasę, która może służyć jako klasę podstawową tylko.

Aby określić, że klasa nie można użyć jako klasy podstawowej:

```vb
NotInheritable Class SampleClass
End Class
```

Aby określić, że klasa może służyć jako klasę podstawową tylko i nie można utworzyć wystąpienia:

```vb
MustInherit Class BaseClass
End Class
```

Aby uzyskać więcej informacji, zobacz:

- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Zastępowanie elementów członkowskich
Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie ze swojej klasy podstawowej. Aby zmienić zachowanie dziedziczony element członkowski, należy go zastąpić. Oznacza to można zdefiniować nowej implementacji metody, właściwości lub zdarzenia w klasie pochodnej.

Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:

|Modyfikator Visual Basic|Definicja|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Umożliwia elementu członkowskiego klasy do zastąpienia w klasie pochodnej.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Zastępuje członka wirtualnego (możliwym do zastąpienia) zdefiniowana w klasie podstawowej.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Element członkowski zapobiega zastępowaniu klasy dziedziczące.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Wymaga, aby element członkowski klasy do zastąpienia w klasie pochodnej.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Ukrywa element członkowski dziedziczona z klasy podstawowej|

## <a name="interfaces"></a>Interfejsy
Interfejsy, takich jak klasy, zdefiniuj zbiór właściwości, metod i zdarzeń. Jednak w przeciwieństwie do klasy, interfejsy nie dostarcza implementacji. Są implementowane przez klasy i zdefiniowane jako osobne jednostki z klas. Interfejs reprezentuje kontraktu, w tym klasy, która implementuje interfejs musi implementować każdego aspektu ten interfejs, dokładnie tak, jak jest zdefiniowany.

Aby zdefiniować interfejsu:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Aby zaimplementować interfejs w klasie:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Aby uzyskać więcej informacji, zobacz:

- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  

- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a>Typy ogólne
Klasy, struktury, interfejsy i metody w środowisku .NET mogą obejmować *parametry typu* definiującą typów obiektów, które mogą przechowywać lub użyć. Najbardziej typowym przykładem typów ogólnych jest kolekcją, w którym można określić typ obiektów, które mają być przechowywane w kolekcji.  

Aby zdefiniować klasy ogólnej:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Można utworzyć wystąpienia klasy generycznej:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Aby uzyskać więcej informacji, zobacz:

- [Typy ogólne](~/docs/standard/generics/index.md)

- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegaty
 A *delegować* jest typ, który określa podpis metody i można udostępnić odwołanie do dowolnej metody zgodnego podpisu. Można wywołać (lub wywołać) metoda za pośrednictwem pełnomocnika. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
>  Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).

Do utworzenia delegata:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Aby utworzyć odwołanie do metody, która odpowiada podpisu określony na podstawie delegata:

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

Aby uzyskać więcej informacji, zobacz:

- [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)

- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Zobacz także
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
