---
title: 'Instrukcje: dodawanie metod niestandardowych do zapytań LINQ'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 55004441d2d1d74556da6841f28d113b876d1048
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400607"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Instrukcje: dodawanie metod niestandardowych dla zapytań LINQ (Visual Basic)

Można rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzających do <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład oprócz standardowej średniej lub maksymalnej operacji można utworzyć niestandardową metodę agregującą, aby obliczyć pojedynczą wartość z sekwencji wartości. Możesz również utworzyć metodę, która działa jako filtr niestandardowy lub Przekształć dane dla sekwencji wartości i zwraca nową sekwencję. Przykładami takich metod są <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> , i <xref:System.Linq.Enumerable.Reverse%2A> .

Rozszerzając <xref:System.Collections.Generic.IEnumerable%601> interfejs, można zastosować niestandardowe metody do dowolnej wyliczalnej kolekcji. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../language-features/procedures/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Dodawanie metody agregującej

Metoda agregująca oblicza pojedynczą wartość z zestawu wartości. LINQ zawiera kilka metod agregujących, w tym <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> i <xref:System.Linq.Enumerable.Max%2A> . Można utworzyć własną metodę agregującą, dodając metodę rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.

Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia wywołana, `Median` Aby obliczyć medianę dla sekwencji liczb typu `double` .

```vb
Imports System.Runtime.CompilerServices

Module LINQExtension

    ' Extension method for the IEnumerable(of T) interface.
    ' The method accepts only values of the Double type.
    <Extension()>
    Function Median(ByVal source As IEnumerable(Of Double)) As Double
        If source.Count = 0 Then
            Throw New InvalidOperationException("Cannot compute median for an empty set.")
        End If

        Dim sortedSource = From number In source
                           Order By number

        Dim itemIndex = sortedSource.Count \ 2

        If sortedSource.Count Mod 2 = 0 Then
            ' Even number of items in list.
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2
        Else
            ' Odd number of items in list.
            Return sortedSource(itemIndex)
        End If
    End Function
End Module
```

Ta metoda rozszerzenia jest wywoływana dla każdej wyliczalnej kolekcji w taki sam sposób, w jaki wywołujemy inne metody agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.

> [!NOTE]
> W Visual Basic można użyć wywołania metody lub standardowej składni zapytania dla `Aggregate` `Group By` klauzuli OR. Aby uzyskać więcej informacji, zobacz [klauzula agregująca](../../../language-reference/queries/aggregate-clause.md) i [klauzula GROUP by](../../../language-reference/queries/group-by-clause.md).

Poniższy przykład kodu pokazuje, jak używać `Median` metody dla tablicy typu `double` .

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Przeciążanie metody agregującej w celu zaakceptowania różnych typów

Można przeciążyć metodę agregacji, aby akceptować sekwencje różnych typów. Standardowe podejście polega na utworzeniu przeciążenia dla każdego typu. Innym rozwiązaniem jest utworzenie przeciążenia, które będzie miało typ ogólny i przekonwertować go na określony typ za pomocą delegata. Można również połączyć oba podejścia.

#### <a name="to-create-an-overload-for-each-type"></a>Aby utworzyć Przeciążenie dla każdego typu

Można utworzyć określone Przeciążenie dla każdego typu, który ma być obsługiwany. Poniższy przykład kodu przedstawia Przeciążenie `Median` metody dla `integer` typu.

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

Teraz można wywoływać `Median` przeciążenia dla obu `integer` typów i `double` typy, jak pokazano w poniższym kodzie:

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
Dim numbers2() As Integer = {1, 2, 3, 4, 5}

Dim query2 = Aggregate num In numbers2 Into Median()

Console.WriteLine("Integer: Median = " & query2)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
' Integer: Median = 3
```

#### <a name="to-create-a-generic-overload"></a>Aby utworzyć Przeciążenie ogólne

Można również utworzyć Przeciążenie, które akceptuje sekwencję obiektów ogólnych. To przeciążenie przyjmuje delegat jako parametr i używa go do konwersji sekwencji obiektów typu ogólnego do określonego typu.

Poniższy kod przedstawia Przeciążenie `Median` metody, która przyjmuje <xref:System.Func%602> Delegat jako parametr. Ten delegat pobiera obiekt typu ogólnego T i zwraca obiekt typu `double` .

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

Teraz można wywołać `Median` metodę dla sekwencji obiektów dowolnego typu. Jeśli typ nie ma własnego przeciążenia metody, należy przekazać parametr delegata. W Visual Basic można użyć wyrażenia lambda do tego celu. Ponadto, jeśli używasz `Aggregate` `Group By` klauzuli or zamiast wywołania metody, można przekazać dowolną wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.

Poniższy przykładowy kod pokazuje, jak wywołać `Median` metodę dla tablicy liczb całkowitych i tablicy ciągów. Dla ciągów, mediany dla długości ciągów w tablicy jest obliczany. W przykładzie pokazano, jak przekazać <xref:System.Func%602> parametr delegata do `Median` metody dla każdego przypadku.

```vb
Dim numbers3() As Integer = {1, 2, 3, 4, 5}

' You can use num as a parameter for the Median method
' so that the compiler will implicitly convert its value to double.
' If there is no implicit conversion, the compiler will
' display an error message.

Dim query3 = Aggregate num In numbers3 Into Median(num)

Console.WriteLine("Integer: Median = " & query3)

Dim numbers4() As String = {"one", "two", "three", "four", "five"}

' With the generic overload, you can also use numeric properties of objects.

Dim query4 = Aggregate str In numbers4 Into Median(str.Length)

Console.WriteLine("String: Median = " & query4)

' This code produces the following output:
'
' Integer: Median = 3
' String: Median = 4
```

## <a name="adding-a-method-that-returns-a-collection"></a>Dodawanie metody zwracającej kolekcję

Interfejs można rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> za pomocą niestandardowej metody zapytania, która zwraca sekwencję wartości. W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601> . Takie metody mogą służyć do zastosowania filtrów lub transformacji danych do sekwencji wartości.

Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements` , która zwraca każdy inny element w kolekcji, rozpoczynając od pierwszego elementu.

```vb
' Extension method for the IEnumerable(of T) interface.
' The method returns every other element of a sequence.

<Extension()>
Function AlternateElements(Of T)(
    ByVal source As IEnumerable(Of T)
    ) As IEnumerable(Of T)

    Dim list As New List(Of T)
    Dim i = 0
    For Each element In source
        If (i Mod 2 = 0) Then
            list.Add(element)
        End If
        i = i + 1
    Next
    Return list
End Function
```

Można wywołać tę metodę rozszerzenia dla każdej wyliczalnej kolekcji tak samo jak w przypadku wywołania innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:

```vb
Dim strings() As String = {"a", "b", "c", "d", "e"}

Dim query = strings.AlternateElements()

For Each element In query
    Console.WriteLine(element)
Next

' This code produces the following output:
'
' a
' c
' e
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic.IEnumerable%601>
- [Metody rozszerzające](../../language-features/procedures/extension-methods.md)
