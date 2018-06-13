---
title: Iteratory (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: ecc48ad5bbddc82457a8d6cc8e60ee419fb593fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643929"
---
# <a name="iterators-visual-basic"></a>Iteratory (Visual Basic)
*Iterator* może służyć do kroków opisanych w kolekcji, takie jak listy i stałych.  
  
 Metody iterator lub `get` akcesor wykonuje niestandardowych iteracji w kolekcji. Iterator — metoda korzysta z [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element jednym naraz. Gdy `Yield` osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie. Wykonanie jest uruchamiany ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.  
  
 Korzystać z iteratora z kodu klienta za pomocą [For Each... Następny](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrukcji, lub za pomocą zapytania LINQ.  
  
 W poniższym przykładzie pierwszej iteracji `For Each` pętli powoduje wykonanie kontynuować w `SomeNumbers` metody iteracyjnej do pierwszego `Yield` osiągnięciu instrukcji. Tą iterację zwraca wartość 3 i są przechowywane w bieżącej lokalizacji w metodzie iteracyjnej. Przy następnej iteracji pętli, wykonywanie w metodzie iteracyjnej będzie kontynuowane z, w którym ją przerwał pracę, ponownie zatrzymywanie po osiągnięciu `Yield` instrukcji. Tą iterację zwraca wartość 5, a bieżącą lokalizację w metodzie iteracyjnej ponownie zostanie zachowane. Pętla działanie jest kończone po osiągnięciu na końcu metody iteracyjnej.  
  
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
  
 Zwracany typ metody iterator lub `get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Można użyć `Exit Function` lub `Return` instrukcji, aby zakończyć iterację.  
  
 Funkcja iteratora języka Visual Basic lub `get` deklaracja dostępu zawiera [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modyfikator.  
  
 Iteratory zostały wprowadzone w języku Visual Basic w programie Visual Studio 2012.  
  
 **W tym temacie**  
  
-   [Prostego iteratora](#BKMK_SimpleIterator)  
  
-   [Tworzenie klasy kolekcji](#BKMK_CollectionClass)  
  
-   [Bloki try](#BKMK_TryBlocks)  
  
-   [Metody anonimowe](#BKMK_AnonymousMethods)  
  
-   [Przy użyciu Iteratory z listą ogólnych](#BKMK_GenericList)  
  
-   [Informacje o składni](#BKMK_SyntaxInformation)  
  
-   [Implementacja techniczna](#BKMK_Technical)  
  
-   [Użyj Iteratory](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Wszystkie przykłady w tym temacie, z wyjątkiem przykład prostego iteratora, obejmują [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcje dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.  
  
##  <a name="BKMK_SimpleIterator"></a> Prostego iteratora  
 W poniższym przykładzie przedstawiono jeden `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. W `Main`, każdej iteracji `For Each` treść instrukcji tworzy wywołanie funkcji iteracyjnej, który przechodzi do następnego `Yield` instrukcji.  
  
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
  
##  <a name="BKMK_CollectionClass"></a> Tworzenie klasy kolekcji  
 W poniższym przykładzie `DaysOfTheWeek` klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. Kompilator niejawnie wywołuje `GetEnumerator` metody, która zwraca <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Metoda zwraca każdego jednego ciągu w czasie przy użyciu `Yield` instrukcji i `Iterator` jest modyfikatora w deklaracji funkcji.  
  
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
  
 Poniższy przykład tworzy `Zoo` klasy, która zawiera kolekcję zwierząt.  
  
 `For Each` Instrukcji, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metody. `For Each` Instrukcje odwołujące się do `Birds` i `Mammals` Użyj właściwości `AnimalsForType` o nazwie metody iteracyjnej.  
  
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
  
##  <a name="BKMK_TryBlocks"></a> Bloki try  
 Visual Basic umożliwia `Yield` instrukcji w `Try` zablokować z [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` bloku, który ma `Yield` instrukcja może mieć `Catch` blokuje i może mieć `Finally` bloku.  
  
 Poniższy przykład zawiera `Try`, `Catch`, i `Finally` bloki w funkcji iteracyjnej. `Finally` Bloku w funkcji iteracyjnej wykonuje przed `For Each` zakończenie iteracji.  
  
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
  
 A `Yield` instrukcja nie może być wewnątrz `Catch` bloku lub `Finally` bloku.  
  
 Jeśli `For Each` treści (zamiast metody iterator) zgłasza wyjątek, `Catch` bloku w funkcji iteracyjnej nie została wykonana, ale `Finally` wykonaniu bloku w funkcji iteracyjnej. A `Catch` bloku wewnątrz funkcji iteracyjnej przechwytuje tylko wyjątki, które występuje wewnątrz funkcji iteracyjnej.  
  
##  <a name="BKMK_AnonymousMethods"></a> Metody anonimowe  
 W języku Visual Basic funkcji anonimowej może być funkcji iteracyjnej. Ilustruje to poniższy przykład.  
  
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
  
 W poniższym przykładzie przedstawiono metodę iteratora nie sprawdza poprawność argumentów. Metoda zwraca wynik anonimowe iteratora opisujący elementów kolekcji.  
  
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
  
 Jeśli weryfikacja jest wewnątrz funkcji iteracyjnej, do momentu rozpoczęcia pierwszej iteracji nie można wykonać walidacji `For Each` treści.  
  
##  <a name="BKMK_GenericList"></a> Przy użyciu Iteratory z listą ogólnych  
 W poniższym przykładzie `Stack(Of T)` implementuje klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny. `Push` Metody przypisuje wartości do tablicy typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda zwraca wartości w tablicy przy użyciu `Yield` instrukcji.  
  
 Oprócz ogólnego <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, inny niż ogólny <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda musi zostać wdrożona. Jest to spowodowane <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable>. Implementację nieogólnego różni się do ogólnego implementacji.  
  
 W przykładzie użyto nazwanego Iteratory do obsługi różnych sposobów iteracji w tej samej kolekcji danych. Są one o nazwie Iteratory `TopToBottom` i `BottomToTop` właściwości oraz `TopN` metody.  
  
 `BottomToTop` Obejmuje deklaracja właściwości `Iterator` — słowo kluczowe.  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a> Informacje o składni  
 Iteratora może wystąpić jako metody lub `get` dostępu. Iterator nie może wystąpić w zdarzenia, konstruktora wystąpienia, statycznego konstruktora lub destruktora statycznych.  
  
 Niejawna konwersja musi istnieć od typ wyrażenia w `Yield` instrukcji, aby zwracany typ iteratora.  
  
 W języku Visual Basic, metody iteracyjne nie mogą zawierać `ByRef` parametrów.  
  
 W języku Visual Basic "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest on używany w `Iterator` metody lub `get` dostępu.  
  
##  <a name="BKMK_Technical"></a> Implementacja techniczna  
 Mimo że pisania iteratora jako metoda kompilator tłumaczy go na zagnieżdżona klasa oznacza to, w efekcie automatu stanów. Ta klasa przechowuje informacje o pozycja iteratora, jak długo `For Each...Next` nadal pętli w kodzie klienta.  
  
 Aby zobaczyć, co oznacza kompilatora, narzędzie Ildasm.exe służy do wyświetlania kod języka pośredniego firmy Microsoft, który jest generowany dla metody iterator.  
  
 Po utworzeniu iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), nie masz do zaimplementowania całości <xref:System.Collections.IEnumerator> interfejsu. Kompilator wykrycie iteratora automatycznie generuje `Current`, `MoveNext`, i `Dispose` metody <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> interfejsu.  
  
 W każdej iteracji kolejnych `For Each…Next` pętli (lub bezpośrednie wywołanie `IEnumerator.MoveNext`), treść kodu dalej iteratora zostanie wznowione po poprzedniej `Yield` instrukcji. Następnie jest kontynuowana do następnego `Yield` instrukcji, dopóki nie zostanie osiągnięty koniec treści iteratora, lub do czasu `Exit Function` lub `Return` napotkano instrukcji.  
  
 Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Aby ponownie przejść od początku, należy uzyskać nowe iteratora.  
  
 Aby uzyskać dodatkowe informacje, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
##  <a name="BKMK_UseOfIterators"></a> Użyj Iteratory  
 Iteratory umożliwiają zachować prostotę `For Each` pętli, gdy musisz użyć złożonego kodu do wypełniania kolejność listy. Może to być przydatne, jeśli chcesz wykonać następujące czynności:  
  
-   Zmodyfikuj kolejność listy po pierwszym `For Each` iteracji pętli.  
  
-   Unikaj pełni ładowania dużych listy przed pierwszym iteracji `For Each` pętli. Przykładem jest stronicowana pobierania załadować partii wierszy tabeli. Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodę, która implementuje Iteratory w programie .NET Framework.  
  
-   Hermetyzuj Tworzenie listy w iteratora. W metodzie iteracyjnej można utworzyć listy i instrukcji yield każdy wynik w pętli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Yield, instrukcja](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
