---
title: Iteratory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: f9d5a976badc80c5ce00258f46e1d347f20be2f3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583347"
---
# <a name="iterators-visual-basic"></a>Iteratory (Visual Basic)

*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.

Metoda iteratora lub akcesor `get` wykonuje niestandardową iterację w kolekcji. Metoda iterator używa instrukcji [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) do zwrócenia każdego elementu w czasie. Po osiągnięciu instrukcji `Yield` bieżąca lokalizacja w kodzie jest zapamiętywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Iterator z kodu klienta jest używany przez [... Następna](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcja lub przy użyciu zapytania LINQ.

W poniższym przykładzie pierwsza iteracja pętli `For Each` powoduje, że wykonanie w metodzie iteratora `SomeNumbers` do momentu osiągnięcia pierwszej instrukcji `Yield`. Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana. W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `Yield`. Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie. Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

Typem zwracanym metody iteratora lub metodzie dostępu `get` może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601>.

Aby zakończyć iterację, można użyć instrukcji `Exit Function` lub `Return`.

Funkcja iteratora Visual Basic lub Deklaracja metody dostępu `get` zawiera modyfikator [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md) .

Iteratory zostały wprowadzone w Visual Basic w programie Visual Studio 2012.

**W tym temacie**

- [Iterator prosty](#BKMK_SimpleIterator)

- [Tworzenie klasy kolekcji](#BKMK_CollectionClass)

- [Bloki try](#BKMK_TryBlocks)

- [Metody anonimowe](#BKMK_AnonymousMethods)

- [Używanie iteratorów z listą ogólną](#BKMK_GenericList)

- [Informacje o składni](#BKMK_SyntaxInformation)

- [Implementacja techniczna](#BKMK_Technical)

- [Użycie iteratorów](#BKMK_UseOfIterators)

> [!NOTE]
> Wszystkie przykłady w temacie z wyjątkiem prostego przykładu iteratora zawierają instrukcje [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla przestrzeni nazw `System.Collections` i `System.Collections.Generic`.

## <a name="BKMK_SimpleIterator"></a>Iterator prosty

Poniższy przykład zawiera jedną instrukcję `Yield`, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. W `Main` każda iteracja treści instrukcji `For Each` tworzy wywołanie funkcji iteratora, która przechodzi do następnej instrukcji `Yield`.

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="BKMK_CollectionClass"></a>Tworzenie klasy kolekcji

W poniższym przykładzie Klasa `DaysOfTheWeek` implementuje interfejs <xref:System.Collections.IEnumerable>, który wymaga metody <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Kompilator niejawnie wywołuje metodę `GetEnumerator`, która zwraca <xref:System.Collections.IEnumerator>.

Metoda `GetEnumerator` zwraca każdy ciąg pojedynczo przy użyciu instrukcji `Yield` i modyfikator `Iterator` jest w deklaracji funkcji.

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

Poniższy przykład tworzy klasę `Zoo`, która zawiera kolekcję zwierząt.

Instrukcja `For Each`, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje metodę `GetEnumerator`. Instrukcje `For Each` odwołujące się do właściwości `Birds` i `Mammals` używają metody iteratora o nazwie `AnimalsForType`.

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="BKMK_TryBlocks"></a>Bloki try

Visual Basic zezwala na instrukcję `Yield` w bloku `Try` [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Blok `Try`, który zawiera instrukcję `Yield` może mieć `Catch` bloków i może mieć blok `Finally`.

Poniższy przykład zawiera `Try`, `Catch` i `Finally` bloków w funkcji iteratora. Blok `Finally` w funkcji iteratora jest wykonywany przed zakończeniem `For Each` iteracji.

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

Instrukcja `Yield` nie może znajdować się wewnątrz bloku `Catch` lub bloku `Finally`.

Jeśli treść `For Each` (zamiast metody iteratora) zgłasza wyjątek, blok `Catch` w funkcji iteratora nie zostanie wykonany, ale jest wykonywany blok `Finally` w funkcji iteratora. Blok `Catch` wewnątrz funkcji iteratora przechwytuje tylko wyjątki występujące wewnątrz funkcji iteratora.

## <a name="BKMK_AnonymousMethods"></a>Metody anonimowe

W Visual Basic funkcja anonimowa może być funkcją iteratora. Ilustruje to poniższy przykład.

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

Poniższy przykład ma metodę nieiteracyjną, która weryfikuje argumenty. Metoda zwraca wynik iteratora anonimowego, który opisuje elementy kolekcji.

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

Jeśli walidacja jest w funkcji iteratora, walidacja nie może zostać wykonana do momentu rozpoczęcia pierwszej iteracji treści `For Each`.

## <a name="BKMK_GenericList"></a>Używanie iteratorów z listą ogólną

W poniższym przykładzie Klasa generyczna `Stack(Of T)` implementuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601>. Metoda `Push` przypisuje wartości do tablicy typu `T`. Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwraca wartości tablicy przy użyciu instrukcji `Yield`.

Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Dzieje się tak, ponieważ <xref:System.Collections.Generic.IEnumerable%601> dziedziczy po <xref:System.Collections.IEnumerable>. Implementacja nieogólna odłożenia do ogólnej implementacji.

W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych. Te nazwane Iteratory są właściwościami `TopToBottom` i `BottomToTop` i metodą `TopN`.

Deklaracja właściwości `BottomToTop` zawiera słowo kluczowe `Iterator`.

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="BKMK_SyntaxInformation"></a>Informacje o składni

Iterator może wystąpić jako metoda dostępu metody lub `get`. Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.

Niejawna konwersja musi istnieć z typu wyrażenia w instrukcji `Yield` na zwracany typ iteratora.

W Visual Basic Metoda iteratora nie może mieć żadnych parametrów `ByRef`.

W Visual Basic "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używana w metodzie `Iterator` lub metodzie dostępu `get`.

## <a name="BKMK_Technical"></a>Implementacja techniczna

Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu. Ta klasa śledzi pozycję iteratora, tak długo pętla `For Each...Next` w kodzie klienta kontynuuje działanie.

Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który jest generowany dla metody iterator.

Podczas tworzenia iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md)nie trzeba implementować całego interfejsu <xref:System.Collections.IEnumerator>. Gdy kompilator wykryje iterator, automatycznie generuje metody `Current`, `MoveNext` i `Dispose` interfejsu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601>.

Dla każdej kolejnej iteracji pętli `For Each…Next` (lub bezpośredniego wywołania do `IEnumerator.MoveNext`) Następna treść kodu iteratora zostanie wznowiona po poprzedniej instrukcji `Yield`. Następnie przechodzi do następnej instrukcji `Yield` do momentu osiągnięcia końca treści iteratora lub do momentu napotkania instrukcji `Exit Function` lub `Return`.

Iteratory nie obsługują metody <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>. Aby ponownie wykonać iterację od początku, należy uzyskać nowy iterator.

Aby uzyskać dodatkowe informacje, zobacz [Specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).

## <a name="BKMK_UseOfIterators"></a>Użycie iteratorów

Iteratory umożliwiają zachowanie prostoty pętli `For Each`, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:

- Zmodyfikuj sekwencję list po pierwszej iteracji pętli `For Each`.

- Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją pętli `For Each`. Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli. Innym przykładem jest metoda <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, która implementuje Iteratory w .NET Framework.

- Hermetyzuje Kompilowanie listy w iterator. W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Yield, instrukcja](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
