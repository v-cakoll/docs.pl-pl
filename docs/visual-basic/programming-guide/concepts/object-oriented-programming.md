---
title: Programowanie zorientowane obiektowo
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: f7e222cde8ce80d4c52cc8b4b111c576eb4041b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413196"
---
# <a name="object-oriented-programming-visual-basic"></a>Programowanie zorientowane obiektowo (Visual Basic)

Visual Basic zapewnia pełną obsługę programowania zorientowanego obiektowo, w tym hermetyzację, dziedziczenie i polimorfizm.

 *Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich jest traktowana jako pojedyncza jednostka lub obiekt.

 *Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.

 *Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, nawet jeśli każda klasa implementuje te same właściwości lub metody na różne sposoby.

 W tej sekcji opisano następujące pojęcia:

- [Klasy i obiekty](#classes-and-objects)
  - [Elementy członkowskie klasy](#class-members)
    - [Właściwości i pola](#properties-and-fields)
    - [Metody](#methods)
    - [Konstruktory](#constructors)
    - [Destruktory](#destructors)
    - [Zdarzenia](#events)
    - [Klasy zagnieżdżone](#nested-classes)
  - [Modyfikatory dostępu i poziomy dostępu](#access-modifiers-and-access-levels)
    - [Tworzenie wystąpień klas](#instantiating-classes)
    - [Udostępnione klasy i składowe](#shared-classes-and-members)
    - [Typy anonimowe](#anonymous-types)
- [Dziedziczenie](#inheritance)
  - [Zastępowanie elementów członkowskich](#overriding-members)
- [Interfejsy](#interfaces)
- [Typy ogólne](#generics)
- [Delegaci](#delegates)

## <a name="classes-and-objects"></a>Klasy i obiekty

Terminy *Klasa* i *obiekt* są czasami używane zamiennie, ale w rzeczywistości klasy opisują *Typ* obiektów, natomiast obiekty są użyteczne *wystąpienia* klas. W związku z tym czynność tworzenia obiektu jest nazywana *tworzeniem wystąpień*. Korzystając z strategii analogowej, Klasa jest planem, a obiekt jest kompilacją utworzoną z tego planu.

Aby zdefiniować klasę:

```vb
Class SampleClass
End Class
```

Visual Basic udostępnia również uproszczoną wersję klas o nazwie *Structures* , które są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i nie należy zużywać zbyt dużej ilości pamięci.

Aby zdefiniować strukturę:

```vb
Structure SampleStructure
End Structure
```

Aby uzyskać więcej informacji, zobacz:

- [Class, instrukcja](../../language-reference/statements/class-statement.md)
- [Structure — Instrukcja](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Elementy członkowskie klasy

Każda klasa może mieć różne *składowe klasy* , które zawierają właściwości opisujące dane klasy, metody definiujące zachowanie klasy oraz zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.

#### <a name="properties-and-fields"></a>Właściwości i pola

Pola i właściwości reprezentują informacje, które zawiera obiekt. Pola są podobne do zmiennych, ponieważ mogą być odczytywane lub ustawiane bezpośrednio.

Aby zdefiniować pole:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Właściwości mają procedury pobierania i ustawiania, które zapewniają większą kontrolę nad sposobem ustawiania lub zwracania wartości.

Visual Basic umożliwia utworzenie prywatnego pola do przechowywania wartości właściwości lub użycie, tak zwane automatycznie implementowane właściwości, które tworzą to pole automatycznie w tle i zapewniają podstawową logikę dla procedur właściwości.

Aby zdefiniować zaimplementowaną Właściwość:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Jeśli trzeba wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, Zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę do przechowywania i pobierania:

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

Większość właściwości ma metody lub procedury ustawiające i pobierające wartość właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie. W Visual Basic można używać `ReadOnly` `WriteOnly` słów kluczowych i. Jednak właściwości zaimplementowane domyślnie nie mogą być tylko do odczytu lub tylko do zapisu.

Aby uzyskać więcej informacji, zobacz:

- [Property — Instrukcja](../../language-reference/statements/property-statement.md)
- [Get — Instrukcja](../../language-reference/statements/get-statement.md)
- [Set — Instrukcja](../../language-reference/statements/set-statement.md)
- [Trybie](../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Metody

 *Metoda* jest akcją, którą obiekt może wykonać.

> [!NOTE]
> W Visual Basic istnieją dwa sposoby tworzenia metody: `Sub` instrukcja jest używana, jeśli metoda nie zwraca wartości; `Function` instrukcja jest używana, jeśli metoda zwraca wartość.

Aby zdefiniować metodę klasy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.

Aby przeciążyć metodę:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

W większości przypadków deklaruje metodę w ramach definicji klasy. Jednak Visual Basic obsługuje również *metody rozszerzające* , które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.

Aby uzyskać więcej informacji, zobacz:

- [Function, instrukcja](../../language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../language-reference/statements/sub-statement.md)
- [Przeciążenia](../../language-reference/modifiers/overloads.md)
- [Metody rozszerzające](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu. Konstruktory zazwyczaj inicjują elementy członkowskie danych nowego obiektu. Konstruktor można uruchomić tylko raz podczas tworzenia klasy. Ponadto kod w konstruktorze zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie. Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku innych metod.

Aby zdefiniować konstruktora dla klasy:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Aby uzyskać więcej informacji, zobacz: [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory

Destruktory są używane do destruktora wystąpień klas. W .NET Framework Moduł wyrzucania elementów bezużytecznych automatycznie zarządza alokacją i ilością pamięci dla obiektów zarządzanych w aplikacji. Jednak nadal mogą być potrzebne destruktory do czyszczenia wszystkich niezarządzanych zasobów tworzonych przez aplikację. Może istnieć tylko jeden destruktor dla klasy.

Aby uzyskać więcej informacji na temat destruktorów i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Zdarzenia

Zdarzenia umożliwiają klasie lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania. Klasa, która wysyła (lub podnosi) zdarzenie, jest nazywana *wydawcą* i klasy, które odbierają (lub obsługują) zdarzenie są nazywane *subskrybentami*. Aby uzyskać więcej informacji o zdarzeniach, sposobie ich podniesienia i obsłudze, zobacz [zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenia, należy użyć [instrukcji zdarzenia](../../language-reference/statements/event-statement.md).

- Aby zgłosić zdarzenia, należy użyć [instrukcji RaiseEvent](../../language-reference/statements/raiseevent-statement.md).

- Aby określić programy obsługi zdarzeń przy użyciu deklaratywnej metody, należy użyć instrukcji [WithEvents](../../language-reference/modifiers/withevents.md) i klauzuli [Handles](../../language-reference/statements/handles-clause.md) .

- Aby możliwe było dynamiczne dodawanie, usuwanie i zmienianie procedury obsługi zdarzeń skojarzonej ze zdarzeniem, należy użyć instrukcji [AddHandler](../../language-reference/statements/addhandler-statement.md) i [RemoveHandler](../../language-reference/statements/removehandler-statement.md) razem z [operatorem AddressOf](../../language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Klasy zagnieżdżone

Klasa zdefiniowana w innej klasie jest nazywana *zagnieżdżoną*. Domyślnie Klasa zagnieżdżona jest prywatna.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Aby utworzyć wystąpienie klasy zagnieżdżonej, użyj nazwy klasy kontenera, po której następuje kropka, a następnie po której następuje nazwa klasy zagnieżdżonej:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modyfikatory dostępu i poziomy dostępu

Wszystkie klasy i elementy członkowskie klasy mogą określać poziom dostępu udostępniany innym klasom przy użyciu *modyfikatorów dostępu*.

Dostępne są następujące Modyfikatory dostępu:

|Modyfikator Visual Basic|Definicja|
|---------------------------|----------------|
|[Społeczeństwo](../../language-reference/modifiers/public.md)|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego.|
|[Użytek](../../language-reference/modifiers/private.md)|Do typu lub elementu członkowskiego można uzyskać dostęp tylko w kodzie w tej samej klasie.|
|[Chronione](../../language-reference/modifiers/protected.md)|Do typu lub elementu członkowskiego można uzyskać dostęp tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.|
|[Osoby](../../language-reference/modifiers/friend.md)|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.|
|`Protected Friend`|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.|

Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Tworzenie wystąpień klas

Aby utworzyć obiekt, należy utworzyć wystąpienie klasy, lub stworzyć wystąpienia klasy.

```vb
Dim sampleObject as New SampleClass()
```

Po utworzeniu wystąpienia klasy można przypisać wartości do właściwości i pól wystąpienia oraz wywołać metody klasy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatorów obiektów:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz:

- [Operator new](../../language-reference/operators/new-operator.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Udostępnione klasy i składowe

 Współużytkowany element członkowski klasy jest właściwością, procedurą lub polem, które są współużytkowane przez wszystkie wystąpienia klasy.

 Aby zdefiniować współużytkowany element członkowski:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Aby uzyskać dostęp do udostępnionego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:

```vb
MsgBox(SampleClass.SampleString)
```

 Moduły udostępnione w Visual Basic mają tylko udostępnione elementy członkowskie i nie można utworzyć jego wystąpienia. Udostępnione elementy członkowskie nie mogą również uzyskiwać dostępu do nieudostępnionych właściwości, pól lub metod

 Aby uzyskać więcej informacji, zobacz:

- [Shared](../../language-reference/modifiers/shared.md)
- [Module — Instrukcja](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznej nazwy i zawiera właściwości określone w deklaracji obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dziedziczenie

Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie zdefiniowane w innej klasie. Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*. Jednak wszystkie klasy w Visual Basic niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.

> [!NOTE]
> Visual Basic nie obsługuje dziedziczenia wielokrotnego. Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.

Aby dziedziczyć z klasy bazowej:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Domyślnie wszystkie klasy mogą być dziedziczone. Można jednak określić, czy Klasa nie może być używana jako klasa bazowa, ani utworzyć klasy, która może być używana tylko jako klasa bazowa.

Aby określić, że Klasa nie może być używana jako klasa bazowa:

```vb
NotInheritable Class SampleClass
End Class
```

Aby określić, że Klasa może być używana tylko jako klasa bazowa i nie można utworzyć wystąpienia:

```vb
MustInherit Class BaseClass
End Class
```

Aby uzyskać więcej informacji, zobacz:

- [Inherits — Instrukcja](../../language-reference/statements/inherits-statement.md)
- [NotInheritable](../../language-reference/modifiers/notinheritable.md)
- [MustInherit](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Zastępowanie elementów członkowskich

Domyślnie Klasa pochodna dziedziczy wszystkich członków z jej klasy bazowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić. Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.

Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:

|Modyfikator Visual Basic|Definicja|
|---------------------------|----------------|
|[Overridable](../../language-reference/modifiers/overridable.md)|Zezwala na przesłanianie składowej klasy w klasie pochodnej.|
|[Przesłonięcia](../../language-reference/modifiers/overrides.md)|Przesłania element członkowski wirtualny (zastępujący) zdefiniowany w klasie bazowej.|
|[NotOverridable](../../language-reference/modifiers/notoverridable.md)|Zapobiega zastąpieniu elementu członkowskiego w klasie dziedziczenia.|
|[MustOverride](../../language-reference/modifiers/mustoverride.md)|Wymaga, aby element członkowski klasy był zastępowany w klasie pochodnej.|
|[Shadows](../../language-reference/modifiers/shadows.md)|Ukrywa składową dziedziczoną z klasy bazowej|

## <a name="interfaces"></a>Interfejsy

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Ale w przeciwieństwie do klas, interfejsy nie zapewniają implementacji. Są one implementowane przez klasy i zdefiniowane jako osobne jednostki z klas. Interfejs reprezentuje kontrakt, w którym Klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.

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

- [Interfejsy](../language-features/interfaces/index.md)
- [Interface, instrukcja](../../language-reference/statements/interface-statement.md)
- [Implements — Instrukcja](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a>Typy ogólne

Klasy, struktury, interfejsy i metody w programie .NET mogą zawierać *parametry typu* , które definiują typy obiektów, które mogą być przechowywane lub używane. Najbardziej typowym przykładem typów ogólnych jest kolekcja, w której można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę generyczną:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Aby utworzyć wystąpienie klasy generycznej:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Aby uzyskać więcej informacji, zobacz:

- [Typy ogólne](../../../standard/generics/index.md)
- [Typy ogólne w Visual Basic](../language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegaci

 *Delegat* jest typem, który definiuje sygnaturę metody i może podać odwołanie do dowolnej metody ze zgodną sygnaturą. Metodę można wywołać (lub wywołać) za pomocą delegata. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
> Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).

Aby utworzyć delegata:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Aby utworzyć odwołanie do metody, która jest zgodna z sygnaturą określoną przez delegata:

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

- [Delegaci](../language-features/delegates/index.md)
- [Delegate — Instrukcja](../../language-reference/statements/delegate-statement.md)
- [AddressOf, operator](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w Visual Basic](../index.md)
