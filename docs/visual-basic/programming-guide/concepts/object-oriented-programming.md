---
title: Programowanie zorientowane obiektowo (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153932"
---
# <a name="object-oriented-programming-visual-basic"></a>Programowanie zorientowane obiektowo (Visual Basic)

Visual Basic zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizmu.

 *Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.

 *Dziedziczenie* opisuje zdolność do tworzenia nowych klas w oparciu o istniejącą klasą.

 *Polimorfizm* oznacza, że może mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody w różny sposób.

 W tej sekcji opisano następujące pojęcia:

- [Klasy i obiekty](#classes-and-objects)
  - [Elementy członkowskie klasy](#class-members)
    - [Właściwości i pola](#properties-and-fields)
    - [Metody](#methods)
    - [Konstruktory](#constructors)
    - [Destruktory](#destructors)
    - [Zdarzenia](#events)
    - [Klasy zagnieżdżone](#nested-classes)
  - [Modyfikatory dostępu oraz poziomy dostępu](#access-modifiers-and-access-levels)
    - [Tworzenie wystąpienia klasy](#instantiating-classes)
    - [Udostępnione klas i składowych](#shared-classes-and-members)
    - [Typy anonimowe](#anonymous-types)
- [Dziedziczenie](#inheritance)
  - [Zastępowanie elementów członkowskich](#overriding-members)
- [Interfejsy](#interfaces)
- [Typy ogólne](#generics)
- [Delegaty](#delegates)

## <a name="classes-and-objects"></a>Klasy i obiekty

Warunki *klasy* i *obiektu* są czasami stosowane zamiennie, jednak w rzeczywistości klasy opisują *typu* obiektów, podczas gdy obiekty to użytkowe  *wystąpienia* klas. Więc, akt tworzenia obiektu jest nazywany *wystąpienia*. Korzystając z analogii planu, klasa to plan, a obiekt to budynek utworzony z tego planu.

Aby zdefiniować klasę:

```vb
Class SampleClass
End Class
```

Visual Basic oferuje również uproszczonej wersji klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć duże tablice obiektów i czy chcesz zużyć do tego zbyt dużej ilości pamięci.

Aby zdefiniować strukturę:

```vb
Structure SampleStructure
End Structure
```

Aby uzyskać więcej informacji, zobacz:

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Elementy członkowskie klasy

Każda klasa może mieć różne *elementy członkowskie klasy* którzy zawierają właściwości, które opisują dane klasy, metody, które definiują zachowanie klasy i wydarzenia, które zapewniają komunikację między różnych klasami i obiektami.

#### <a name="properties-and-fields"></a>Właściwości i pola

Pola i właściwości reprezentują informacje zawarte w obiekcie. Pola przypominają zmienne, ponieważ można je odczytać lub ustawić bezpośrednio.

Aby zdefiniować pole:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Właściwości mają get i ustawić procedur, które zapewniają większą kontrolę nad jak ustawiania lub zwracania wartości.

Visual Basic zezwala na tworzenie prywatnego pola do przechowywania wartości właściwości lub użyć tzw automatycznie implementowanych właściwości, które tworzą to pole automatycznie w tle i ustanowiają podstawowe logiki dla procedur właściwość.

Aby zdefiniować automatycznie implementowanej właściwości:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Jeśli musisz wykonać kilka dodatkowych operacji odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i Zaoferuj podstawową logikę do przechowywania i pobierania:

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

Większość właściwości posiada metody lub procedury do ustawiania i pobierania wartości właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie. W języku Visual Basic można użyć `ReadOnly` i `WriteOnly` słów kluczowych. Jednak automatycznie implementowanych właściwości nie może być tylko do odczytu lub tylko do zapisu.

Aby uzyskać więcej informacji, zobacz:

- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Metody

 A *metoda* to działanie, którą obiekt może wykonywać.

> [!NOTE]
> W języku Visual Basic, istnieją dwa sposoby tworzenia metody: `Sub` instrukcja jest używane, jeśli metoda nie zwraca wartości; `Function` instrukcja jest używane, jeśli metoda zwraca wartość.

Aby zdefiniować metodę klasy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Klasa może mieć kilka implementacji lub *przeciążenia*, z tej samej metody, które różnią się liczbą typów parametru lub parametrów.

Aby przeciążyć metodę

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

W większości przypadków użytkownik deklaruje metodę w ramach definicji klasy. Jednak języka Visual Basic obsługuje również *metody rozszerzenia* umożliwiającą dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.

Aby uzyskać więcej informacji, zobacz:

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Konstruktorów

Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu. Konstruktory zwykle inicjują członków danych nowego obiektu. Konstruktor można uruchomić tylko raz, po utworzeniu klasy. Ponadto kod w Konstruktorze zawsze jest uruchamiany przed innymi kodami w klasie. Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku każdej innej metody.

Aby zdefiniować Konstruktor dla klasy:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Aby uzyskać więcej informacji, zobacz: [Okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory

Destruktory są używane do niszczenia wystąpień klas. W .NET Framework moduł odśmiecania pamięci automatycznie zarządza alokacją i zwolnieniem pamięci dla obiektów zarządzanych w Twojej aplikacji. Jednakże nadal może być konieczne usunięcie przez destruktory niezarządzanych zasobów tworzonych przez aplikację. Może istnieć jedynie jeden destruktor klasy.

Aby uzyskać więcej informacji dotyczących destruktorów i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Zdarzenia

Zdarzenie pozwala klasie lub obiektowi powiadomić inne klasy lub obiektów, kiedy stanie się coś istotnego. Nosi nazwę klasy, która wysyła (lub generuje) zdarzenie *wydawcy* i klasy, otrzymywać (lub uchwyt) zdarzenia, które są nazywane *subskrybentów*. Aby uzyskać więcej informacji na temat zdarzeń, jak ich wywoływania i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenia, użyj [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).

- Aby wywołać zdarzenia, należy użyć [RaiseEvent — instrukcja](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Aby określić obsługę zdarzenia przy użyciu deklaratywną metodę, należy użyć [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrukcji i [obsługuje](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.

- Aby mieć możliwość dynamicznego dodawania, usuwania i zmiany obsługi zdarzenia powiązanego ze zdarzeniem, użyj [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md) i [RemoveHandler — instrukcja](../../../visual-basic/language-reference/statements/removehandler-statement.md) wraz z [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Klasy zagnieżdżone

Nosi nazwę klasy zdefiniowanej w ramach innej klasy *zagnieżdżonych*. Domyślnie zagnieżdżona klasa jest prywatna.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, następuje kropki (.), a następnie według nazwy zagnieżdżonej klasy:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modyfikatory dostępu oraz poziomy dostępu

Wszystkie klasy i składowych klasy, można określić poziom dostępu, jaki stanowią dla innych klas przy użyciu *modyfikatorach dostępu*.

Dostępne są następujące modyfikatory dostępu:

|Modyfikator Visual Basic|Definicja|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|Typ lub element członkowski może zostać oceniony przez inny kod, w tym samym zestawie lub w innym zestawie, który odwołuje się do niej.|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy.|
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy lub w klasie pochodnej.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Typ lub element członkowski może zostać oceniony przez każdy kod z tego samego zestawu, ale nie z innego zestawu.|
|`Protected Friend`|Typ lub element członkowski jest możliwy przez każdy kod z tego samego zestawu lub każdą pochodną klasę w innym zestawie.|

Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Tworzenie wystąpienia klasy

Aby utworzyć obiekt, należy utworzyć wystąpienia klasy lub utworzyć wystąpienie klasy.

```vb
Dim sampleObject as New SampleClass()
```

Po utworzeniu wystąpienia klasy, można przypisać wartości do pól i właściwości instancji i wywołania metod klasy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Aby przypisać wartości do właściwości w procesie tworzenia wystąpienia klasy, użyj inicjalizatorów obiektów:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz:

- [New, operator](../../../visual-basic/language-reference/operators/new-operator.md)
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Udostępnione klas i składowych

 Udostępnione składową klasy jest właściwość, procedura lub pole, który jest współużytkowany przez wszystkie wystąpienia klasy.

 Aby zdefiniować udostępnionego elementu członkowskiego:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Aby uzyskać dostęp do udostępnionej składowej, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:

```vb
MsgBox(SampleClass.SampleString)
```

 Udostępnione moduły w języku Visual Basic zostały udostępnione tylko elementy członkowskie i nie można utworzyć wystąpienia. Udostępniane elementy członkowskie także nie może uzyskać dostępu nieudostępnione właściwości, pól ani metod

 Aby uzyskać więcej informacji, zobacz:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznych nazw i zawiera właściwości, które określisz w odwołaniu do obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dziedziczenie

Dziedziczenie umożliwia utworzenie nowej klasy, która używa, rozszerza i modyfikuje zachowanie, która jest zdefiniowana w innej klasy. Nosi nazwę klasy, której członkowie są dziedziczeni *klasy bazowej*, a klasa, która dziedziczy tych członków, jest nazywana *klasy pochodnej*. Jednakże wszystkie klasy w języku Visual Basic niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia niskopoziomowe usługi dla wszystkich klas.

> [!NOTE]
> Język Visual Basic nie obsługuje wielokrotne dziedziczenie. Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.

Dziedziczenie z klasy bazowej:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Domyślnie wszystkie klasy mogą być dziedziczone. Można jednak określić klasy nie może być używany jako klasa bazowa, czy utworzyć klasę, która może służyć jako klasę bazową tylko.

Aby określić, że klasa nie można użyć jako klasa bazowa:

```vb
NotInheritable Class SampleClass
End Class
```

Aby określić, że klasa może służyć jako klasę bazową tylko i nie można utworzyć wystąpienia:

```vb
MustInherit Class BaseClass
End Class
```

Aby uzyskać więcej informacji, zobacz:

- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Zastępowanie elementów członkowskich

Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie w swojej klasie podstawowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, należy go zastąpić. Oznacza to można zdefiniować nową metodę implementacji metody, właściwości lub zdarzenia w klasie pochodnej.

Następujące Modyfikatory są używane do kontrolowania, jak zastąpić właściwości i metod:

|Modyfikator Visual Basic|Definicja|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Zezwala na element członkowski klasy został nadpisany w klasie pochodnej.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Zastępuje wirtualny element członkowski (przesłanialny) zdefiniowany w klasie bazowej.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Element członkowski zapobiega zastępowaniu w klasie dziedziczącej.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Wymaga, aby element członkowski klasy został nadpisany w klasie pochodnej.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Ukrywa członka dziedziczonego z klasy bazowej|

## <a name="interfaces"></a>Interfejsy

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Jednak w przeciwieństwie do klasy, interfejsy nie zapewniają implementacji. One są implementowane przez klasy i definiowane jako osobne jednostki od klas. Interfejs reprezentuje kontrakt, w tym, że klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu, dokładnie tak, jak jest zdefiniowany.

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
- [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>Typy ogólne

Klasy, struktury, interfejsy i metody na platformie .NET mogą obejmować *parametry typu* który definiują typy obiektów, które można przechowywać lub używać. Najbardziej typowym przykładem typów ogólnych jest kolekcja, której można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę ogólną:

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
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegaty

 A *delegować* to typ, który definiuje podpis metody i można podać odwołanie do dowolnej metody mającą zgodny podpis. Można wywołać (lub wywołać) metodę przez delegat. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
> Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji dotyczących używania delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).

Aby utworzyć delegat:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Aby utworzyć odwołanie do metody, która pasuje do oznaczenia określonego przez delegat:

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

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
