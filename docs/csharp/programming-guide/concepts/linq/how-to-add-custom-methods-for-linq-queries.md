---
title: Jak dodać metody niestandardowe dla zapytań LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141471"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Jak dodać metody niestandardowe dla zapytań LINQ (C#)

Można rozszerzyć zestaw metod, które można użyć dla kwerend LINQ, <xref:System.Collections.Generic.IEnumerable%601> dodając metody rozszerzenia do interfejsu. Na przykład oprócz standardowych operacji średniej lub maksymalnej można utworzyć niestandardową metodę agregacji, aby obliczyć pojedynczą wartość z sekwencji wartości. Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcenie określonych danych dla sekwencji wartości i zwraca nową sekwencję. Przykładami takich metod <xref:System.Linq.Enumerable.Distinct%2A>są <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.Reverse%2A>i .

Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu, można zastosować metody niestandardowe do dowolnej kolekcji wyliczania. Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Dodawanie metody agregowanej

Metoda agregująca oblicza pojedynczą wartość z zestawu wartości. LINQ udostępnia kilka metod <xref:System.Linq.Enumerable.Average%2A>agregacji, w tym , <xref:System.Linq.Enumerable.Min%2A>i <xref:System.Linq.Enumerable.Max%2A>. Można utworzyć własną metodę agregacji, <xref:System.Collections.Generic.IEnumerable%601> dodając metodę rozszerzenia do interfejsu.

W poniższym przykładzie kodu pokazano, `Median` jak utworzyć metodę rozszerzenia o `double`nazwie obliczyć medianę dla sekwencji liczb typu .

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        if (source.Count() == 0)
        {
            throw new InvalidOperationException("Cannot compute median for an empty set.");
        }

        var sortedList = from number in source
                         orderby number
                         select number;

        int itemIndex = (int)sortedList.Count() / 2;

        if (sortedList.Count() % 2 == 0)
        {
            // Even number of items.
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList.ElementAt(itemIndex);
        }
    }
}
```

Ta metoda rozszerzenia dla każdej kolekcji wyliczania w taki sam <xref:System.Collections.Generic.IEnumerable%601> sposób można wywołać inne metody agregacji z interfejsu.

W poniższym przykładzie kodu `Median` pokazano, jak `double`używać metody dla tablicy typu .

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Przeciążenie metody agregacji do akceptowania różnych typów

Można przeciążać metodę agregacji, tak aby akceptuje sekwencje różnych typów. Standardowe podejście jest, aby utworzyć przeciążenie dla każdego typu. Innym podejściem jest utworzenie przeciążenia, które zajmie typ ogólny i przekonwertować go na określony typ przy użyciu pełnomocnika. Można również połączyć oba podejścia.

#### <a name="to-create-an-overload-for-each-type"></a>Aby utworzyć przeciążenie dla każdego typu

Można utworzyć określone przeciążenie dla każdego typu, który ma być obsługiwany. Poniższy przykład kodu pokazuje przeciążenie `Median` metody `integer` dla typu.

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

Teraz można wywołać `Median` przeciążenia dla obu `integer` i `double` typów, jak pokazano w następującym kodzie:

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a>Aby utworzyć ogólne przeciążenie

Można również utworzyć przeciążenie, które akceptuje sekwencję obiektów ogólnych. To przeciążenie przyjmuje delegata jako parametr i używa go do konwersji sekwencji obiektów typu ogólnego do określonego typu.

Poniższy kod pokazuje przeciążenie `Median` metody, <xref:System.Func%602> która przyjmuje delegata jako parametr. Ten pełnomocnik przyjmuje obiekt typu ogólnego T i `double`zwraca obiekt typu .

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

Teraz można wywołać `Median` metodę sekwencji obiektów dowolnego typu. Jeśli typ nie ma własnego przeciążenia metody, należy przekazać parametr delegata. W języku C#, można użyć wyrażenia lambda w tym celu. Ponadto tylko w języku Visual `Aggregate` Basic, jeśli używasz lub `Group By` klauzuli zamiast wywołania metody, można przekazać dowolną wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.

Poniższy przykładowy kod pokazuje, `Median` jak wywołać metodę dla tablicy liczb całkowitych i tablicy ciągów. W przypadku ciągów obliczana jest mediana długości ciągów w tablicy. W przykładzie pokazano, <xref:System.Func%602> jak przekazać `Median` parametr delegata do metody dla każdego przypadku.

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a>Dodawanie metody, która zwraca kolekcję

Interfejs można <xref:System.Collections.Generic.IEnumerable%601> rozszerzyć za pomocą niestandardowej metody kwerendy, która zwraca sekwencję wartości. W takim przypadku metoda musi zwrócić <xref:System.Collections.Generic.IEnumerable%601>kolekcję typu . Takie metody mogą służyć do stosowania filtrów lub przekształcadanych danych do sekwencji wartości.

W poniższym przykładzie pokazano, `AlternateElements` jak utworzyć metodę rozszerzenia o nazwie, która zwraca co drugi element w kolekcji, począwszy od pierwszego elementu.

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

Tę metodę rozszerzenia można wywołać dla dowolnej kolekcji numerowanej, tak <xref:System.Collections.Generic.IEnumerable%601> jak można wywołać inne metody z interfejsu, jak pokazano w poniższym kodzie:

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic.IEnumerable%601>
- [Metody rozszerzeń](../../classes-and-structs/extension-methods.md)
