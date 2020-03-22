---
title: Programowanie obiektowe
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400688"
---
# <a name="object-oriented-programming-visual-basic"></a>Programowanie obiektowe (Visual Basic)

Visual Basic zapewnia pełną obsługę programowania obiektowego, w tym hermetyzacji, dziedziczenia i polimorfizmu.

 *Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich są traktowane jako pojedyncza jednostka lub obiekt.

 *Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.

 *Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.

 W tej sekcji opisano następujące pojęcia:

- [Klasy i obiekty](#classes-and-objects)
  - [Elementy klasy](#class-members)
    - [Właściwości i pola](#properties-and-fields)
    - [Metody](#methods)
    - [Konstruktory](#constructors)
    - [Destruktory](#destructors)
    - [Zdarzenia](#events)
    - [Klasy zagnieżdżone](#nested-classes)
  - [Modyfikatory dostępu i poziomy dostępu](#access-modifiers-and-access-levels)
    - [Tworzenie lekcji tworzenia wystąpienia](#instantiating-classes)
    - [Wspólne zajęcia i członkowie](#shared-classes-and-members)
    - [Typy anonimowe](#anonymous-types)
- [Dziedziczenie](#inheritance)
  - [Zastępowanie członków](#overriding-members)
- [Interfejsy](#interfaces)
- [Typy ogólne](#generics)
- [Delegaty](#delegates)

## <a name="classes-and-objects"></a>Klasy i obiekty

*Klasy* i *obiektu* terminów są czasami używane zamiennie, ale w rzeczywistości klasy opisują *typ* obiektów, podczas gdy obiekty są *użytecznymi wystąpieniami* klas. Tak więc, akt tworzenia obiektu jest nazywany *wystąpienia*. Przy użyciu analogii planu, klasa jest planem, a obiekt jest budynkiem wykonanym z tego planu.

Aby zdefiniować klasę:

```vb
Class SampleClass
End Class
```

Visual Basic zapewnia również lekką wersję klas o nazwie *struktur,* które są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i nie chcesz zużywać zbyt dużo pamięci do tego.

Aby zdefiniować strukturę, należy:

```vb
Structure SampleStructure
End Structure
```

Aby uzyskać więcej informacji, zobacz:

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure — Instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Elementy klasy

Każda klasa może mieć różne *elementy członkowskie klasy,* które zawierają właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.

#### <a name="properties-and-fields"></a>Właściwości i pola

Pola i właściwości reprezentują informacje zawarte w obiekcie. Pola są jak zmienne, ponieważ można je odczytać lub ustawić bezpośrednio.

Aby zdefiniować pole, należy:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Właściwości mają get i ustawić procedury, które zapewniają większą kontrolę nad jak wartości są ustawiane lub zwracane.

Visual Basic umożliwia utworzenie pola prywatnego do przechowywania wartości właściwości lub użycie tak zwanych właściwości automatycznie implementowanych, które automatycznie tworzą to pole za kulisami i zapewniają podstawową logikę dla procedur właściwości.

Aby zdefiniować właściwości zaimplementowane automatycznie:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Jeśli trzeba wykonać kilka dodatkowych operacji do odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę przechowywania i pobierania:

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

Większość właściwości mają metody lub procedury, aby ustawić i uzyskać wartość właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby ograniczyć ich możliwość modyfikowanie lub odczytywanie. W języku Visual `ReadOnly` Basic `WriteOnly` można używać i słów kluczowych. Jednak właściwości automatycznie implementowane nie mogą być tylko do odczytu lub tylko do zapisu.

Aby uzyskać więcej informacji, zobacz:

- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Metody

 *Metoda* jest akcją, którą obiekt może wykonać.

> [!NOTE]
> W języku Visual Basic istnieją dwa sposoby `Sub` tworzenia metody: instrukcja jest używana, jeśli metoda nie zwraca wartości; instrukcja `Function` jest używana, jeśli metoda zwraca wartość.

Aby zdefiniować metodę klasy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Klasa może mieć kilka implementacji lub *przeciążenia*, tej samej metody, które różnią się liczbą parametrów lub typów parametrów.

Aby przeciążyć metodę:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

W większości przypadków deklarujesz metodę w definicji klasy. Jednak Visual Basic obsługuje również *metody rozszerzenia,* które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicję klasy.

Aby uzyskać więcej informacji, zobacz:

- [Instrukcja funkcji](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Konstruktorów

Konstruktory są metody klasy, które są wykonywane automatycznie podczas tworzenia obiektu danego typu. Konstruktory zwykle inicjują elementy członkowskie danych nowego obiektu. Konstruktor można uruchomić tylko raz podczas tworzenia klasy. Ponadto kod w konstruktorze zawsze działa przed innym kodem w klasie. Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób, jak w przypadku każdej innej metody.

Aby zdefiniować konstruktor dla klasy:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Aby uzyskać więcej informacji, zobacz: [Okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory

Destruktory są używane do destrukcji wystąpień klas. W .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i zwalniania pamięci dla obiektów zarządzanych w aplikacji. Jednak nadal może być konieczne destruktory, aby oczyścić wszelkie niezarządzane zasoby, które tworzy aplikacja. Może istnieć tylko jeden destruktor dla klasy.

Aby uzyskać więcej informacji na temat destruktorów i wyrzucania elementów bezużytecznych w ramach .NET Framework, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Zdarzenia

Zdarzenia umożliwiają klasy lub obiektu powiadamiać inne klasy lub obiekty, gdy wystąpi coś interesującego. Klasa, która wysyła (lub wywołuje) zdarzenie jest nazywany *wydawcą* i klasy, które odbierają (lub dojdą) zdarzenie są nazywane *subskrybentów.* Aby uzyskać więcej informacji o zdarzeniach, sposób ich wywoływania i obsługi, zobacz [Zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenia, należy użyć [instrukcji zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).

- Aby podnieść zdarzenia, użyj [RaiseEvent Instrukcji](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Aby określić programy obsługi zdarzeń przy użyciu deklaratywny sposób, należy użyć [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrukcji i [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.

- Aby móc dynamicznie dodawać, usuwać i zmieniać program obsługi zdarzeń skojarzony ze zdarzeniem, należy użyć [instrukcji AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) i [Instrukcji RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) wraz z [operatorem AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Klasy zagnieżdżone

Klasa zdefiniowana w innej klasie jest *nazywana zagnieżdżoną*. Domyślnie klasa zagnieżdżona jest prywatna.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, po której następuje kropka, a następnie następuje nazwa klasy zagnieżdżonej:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modyfikatory dostępu i poziomy dostępu

Wszystkie klasy i członkowie klasy mogą określić, jaki poziom dostępu zapewniają innym klasom za pomocą *modyfikatorów dostępu.*

Dostępne są następujące modyfikatory dostępu:

|Modyfikator języka Visual Basic|Definicja|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|Typ lub element członkowski mogą być dostępne przez inny kod w tym samym zestawie lub innego zestawu, który odwołuje się do niego.|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|Dostęp do typu lub elementu członkowskiego można uzyskać tylko za pomocą kodu w tej samej klasie.|
|[Chronione](../../../visual-basic/language-reference/modifiers/protected.md)|Dostęp do typu lub elementu członkowskiego można uzyskać tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Typ lub element członkowski mogą być dostępne przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.|
|`Protected Friend`|Typ lub element członkowski są dostępne za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.|

Aby uzyskać więcej informacji, zobacz [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Tworzenie lekcji tworzenia wystąpienia

Aby utworzyć obiekt, należy utworzyć wystąpienie klasy lub utworzyć wystąpienie klasy.

```vb
Dim sampleObject as New SampleClass()
```

Po wystąpieniu klasy można przypisać wartości do właściwości i pól wystąpienia i wywołać metody klasy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, użyj inicjatorów obiektów:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz:

- [Nowy operator](../../../visual-basic/language-reference/operators/new-operator.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Wspólne zajęcia i członkowie

 Udostępniony element członkowski klasy jest właściwością, procedurą lub polem współużytkowane przez wszystkie wystąpienia klasy.

 Aby zdefiniować współużytkowane elementu członkowskiego:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Aby uzyskać dostęp do udostępnionego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:

```vb
MsgBox(SampleClass.SampleString)
```

 Udostępnione moduły w języku Visual Basic mają tylko współużytkowanych elementów członkowskich i nie można utworzyć wystąpienia. Współdzielonych członków również nie można uzyskać dostępu do nieudzielonych właściwości, pól lub metod

 Aby uzyskać więcej informacji, zobacz:

- [Udostępnione](../../../visual-basic/language-reference/modifiers/shared.md)
- [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez zapisywania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma nazwy użytkowej i zawiera właściwości określone podczas deklarowania obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dziedziczenie

Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie, które jest zdefiniowane w innej klasie. Klasa, której członkowie są dziedziczone jest nazywany *klasy podstawowej*, a klasa, która dziedziczy tych członków jest nazywany *klasy pochodnej*. Jednak wszystkie klasy w języku Visual <xref:System.Object> Basic niejawnie dziedziczą z klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.

> [!NOTE]
> Visual Basic nie obsługuje wielu dziedziczenia. Oznacza to, że można określić tylko jedną klasę podstawową dla klasy pochodnej.

Aby dziedziczyć z klasy podstawowej:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Domyślnie wszystkie klasy mogą być dziedziczone. Można jednak określić, czy klasa nie może być używana jako klasa podstawowa, czy też utworzyć klasę, która może być używana tylko jako klasa podstawowa.

Aby określić, że klasa nie może być używana jako klasa podstawowa:

```vb
NotInheritable Class SampleClass
End Class
```

Aby określić, że klasa może być używana tylko jako klasa podstawowa i nie można jej utworzyć wystąpienia:

```vb
MustInherit Class BaseClass
End Class
```

Aby uzyskać więcej informacji, zobacz:

- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Zastępowanie członków

Domyślnie klasa pochodna dziedziczy wszystkie elementy członkowskie z klasy podstawowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić. Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.

Następujące modyfikatory są używane do kontrolowania, jak właściwości i metody są zastępowane:

|Modyfikator języka Visual Basic|Definicja|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Umożliwia element członkowski klasy, które mają zostać zastąpione w klasie pochodnej.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Zastępuje wirtualny (nadpisalny) element członkowski zdefiniowany w klasie podstawowej.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Zapobiega element członkowski z nadrzędnego w klasie dziedziczącej.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Wymaga, aby element członkowski klasy został zastąpiony w klasie pochodnej.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Ukrywa element członkowski odziedziczony po klasie podstawowej|

## <a name="interfaces"></a>Interfejsy

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Ale w przeciwieństwie do klas interfejsy nie zapewniają implementacji. Są one implementowane przez klasy i definiowane jako oddzielne jednostki z klas. Interfejs reprezentuje kontrakt, w tym klasy, która implementuje interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.

Aby zdefiniować interfejs:

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

Klasy, struktury, interfejsy i metody w .NET mogą zawierać *parametry typu,* które definiują typy obiektów, które mogą przechowywać lub używać. Najczęstszym przykładem generics jest kolekcja, gdzie można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę rodzajową:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Aby utworzyć wystąpienie klasy ogólnej:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Aby uzyskać więcej informacji, zobacz:

- [Typy ogólne](../../../standard/generics/index.md)
- [Typy ogólne w języku Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegaty

 *Pełnomocnik* jest typem, który definiuje podpis metody i może zapewnić odwołanie do dowolnej metody z zgodnym podpisem. Można wywołać (lub wywołać) metodę za pośrednictwem pełnomocnika. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
> Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji na temat używania pełnomocników w obsłudze zdarzeń, zobacz [Zdarzenia](../../../standard/events/index.md).

Aby utworzyć pełnomocnika:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Aby utworzyć odwołanie do metody zgodnej z podpisem określonym przez pełnomocnika:

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

- [Delegaty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w Visual Basic](../../../visual-basic/programming-guide/index.md)
