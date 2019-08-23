---
title: Iteratory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: db84e5d7956f0b160520fa831607e3f7548fc976
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913154"
---
# <a name="iterators-visual-basic"></a>Iteratory (Visual Basic)
*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.  
  
 Metoda iteratora lub `get` akcesor wykonuje niestandardową iterację w kolekcji. Metoda iterator używa instrukcji [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) do zwrócenia każdego elementu w czasie. Po osiągnięciu `Yield` instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Iterator z kodu klienta jest używany przez [... Następna](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcja lub przy użyciu zapytania LINQ.  
  
 W poniższym przykładzie pierwsza iteracja `For Each` pętli powoduje, że wykonywanie jest wykonywane `SomeNumbers` w metodzie iteratora do momentu osiągnięcia `Yield` pierwszej instrukcji. Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana. W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `Yield` instrukcji. Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie. Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.  
  
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
  
 Typem zwracanym metody iteratora `get` lub akcesora może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub. <xref:System.Collections.Generic.IEnumerator%601>  
  
 Możesz użyć `Exit Function` instrukcji lub `Return` , aby zakończyć iterację.  
  
 Funkcja iteratora Visual Basic lub `get` Deklaracja metody dostępu zawiera [](../../../visual-basic/language-reference/modifiers/iterator.md) modyfikator iteratora.  
  
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
> Wszystkie przykłady w temacie z wyjątkiem prostego przykładu iteratora zawierają instrukcje [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.  
  
## <a name="BKMK_SimpleIterator"></a>Iterator prosty  
 Poniższy przykład zawiera pojedynczą `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. W `Main`programie każda iteracja `For Each` treści instrukcji tworzy wywołanie funkcji iteratora, która przechodzi do następnej `Yield` instrukcji.  
  
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
 W poniższym przykładzie `DaysOfTheWeek` Klasa <xref:System.Collections.IEnumerable> implementuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> interfejs, który wymaga metody. Kompilator niejawnie wywołuje `GetEnumerator` metodę, która <xref:System.Collections.IEnumerator>zwraca.  
  
 Metoda zwraca każdy ciąg pojedynczo przy `Yield` użyciu instrukcji, a `Iterator` modyfikator jest w deklaracji funkcji. `GetEnumerator`  
  
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
  
 Poniższy przykład tworzy `Zoo` klasę, która zawiera kolekcję zwierząt.  
  
 Instrukcja odwołująca się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metodę. `For Each` Instrukcje odwołujące się `Birds` do właściwości `Mammals` i używają `AnimalsForType` nazwanego metody iteratora. `For Each`  
  
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
 Visual Basic zezwala `Yield` instrukcji `Try` w bloku [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Blok, który `Yield` ma instrukcję, może mieć `Catch` bloki i może mieć `Finally` blok. `Try`  
  
 Poniższy przykład zawiera `Try`bloki, `Catch`, i `Finally` w funkcji iteratora. Blok w funkcji iterator jest wykonywany `For Each` przed ukończeniem iteracji. `Finally`  
  
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
  
 Instrukcja nie może znajdować się `Catch` wewnątrz bloku lub `Finally` bloku. `Yield`  
  
 Jeśli treść (zamiast metody iteratora) zgłasza wyjątek `Catch` , blok w funkcji iteratora `Finally` nie zostanie wykonany, ale jest wykonywany blok w funkcji iteratora. `For Each` `Catch` Blok wewnątrz funkcji iteratora przechwytuje tylko wyjątki, które występują wewnątrz funkcji iteratora.  
  
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
  
 Jeśli walidacja jest w funkcji iteratora, walidacja nie może zostać wykonana do momentu rozpoczęcia pierwszej iteracji `For Each` treści.  
  
## <a name="BKMK_GenericList"></a>Używanie iteratorów z listą ogólną  
 W poniższym przykładzie `Stack(Of T)` Klasa generyczna <xref:System.Collections.Generic.IEnumerable%601> implementuje interfejs generyczny. Metoda przypisuje wartości do tablicy typu `T`. `Push` Metoda zwraca wartości tablicy przy `Yield` użyciu instrukcji. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>  
  
 Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową <xref:System.Collections.IEnumerable.GetEnumerator%2A> . Wynika to z <xref:System.Collections.Generic.IEnumerable%601> faktu <xref:System.Collections.IEnumerable>, że dziedziczy z. Implementacja nieogólna odłożenia do ogólnej implementacji.  
  
 W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych. Te nazwane Iteratory to `TopToBottom` właściwości `TopN` i `BottomToTop` i metoda.  
  
 Deklaracja `BottomToTop` właściwości `Iterator` zawiera słowo kluczowe.  
  
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
 Iterator może wystąpić jako metoda lub `get` akcesor. Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.  
  
 Niejawna konwersja musi istnieć z typu wyrażenia w `Yield` instrukcji do zwracanego typu iteratora.  
  
 W Visual Basic Metoda iteratora nie może mieć żadnych `ByRef` parametrów.  
  
 W Visual Basic "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany w `Iterator` metodzie lub `get` akcesorze.  
  
## <a name="BKMK_Technical"></a>Implementacja techniczna  
 Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu. Ta klasa śledzi pozycję iteratora, tak długo `For Each...Next` pętla w kodzie klienta jest kontynuowana.  
  
 Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który jest generowany dla metody iterator.  
  
 Podczas tworzenia iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md)nie trzeba implementować całego <xref:System.Collections.IEnumerator> interfejsu. Gdy kompilator wykryje `Current`iterator, automatycznie generuje metody <xref:System.Collections.IEnumerator> , `MoveNext`, <xref:System.Collections.Generic.IEnumerator%601> i `Dispose` interfejsu.  
  
 Dla każdej kolejnej iteracji `For Each…Next` pętli (lub bezpośredniego wywołania do `IEnumerator.MoveNext`) Następna treść kodu iteratora zostanie wznowiona po poprzedniej `Yield` instrukcji. Następnie przechodzi do następnej `Yield` instrukcji do momentu osiągnięcia końca treści iteratora lub `Exit Function` do momentu napotkania instrukcji lub `Return` .  
  
 Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Aby ponownie wykonać iterację od początku, należy uzyskać nowy iterator.  
  
 Aby uzyskać dodatkowe informacje, zobacz [Specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
## <a name="BKMK_UseOfIterators"></a>Użycie iteratorów  
 Iteratory umożliwiają zachowanie prostoty `For Each` pętli, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:  
  
- Zmodyfikuj sekwencję list po pierwszej `For Each` iteracji pętli.  
  
- Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją `For Each` pętli. Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli. Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> Metoda, która implementuje Iteratory w .NET Framework.  
  
- Hermetyzuje Kompilowanie listy w iterator. W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Yield, instrukcja](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
