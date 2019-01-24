---
title: 'Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 0c90e869c3d56696a072585cca7282b459b39e07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540731"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (C#)
Można rozszerzyć zbiór metod, które służy do zapytań LINQ, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład oprócz standardowych średnia lub maksymalna operacje, możesz utworzyć niestandardowe metody agregacji do obliczenia pojedynczej wartości z sekwencji wartości. Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcenia danych określonego dla sekwencji wartości i zwraca nową sekwencję. Przykłady takich metod <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu swoje niestandardowe metody można zastosować do kolekcji wyliczenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Dodawanie metody agregacji  
 Metoda agregacji oblicza pojedynczej wartości z zestawu wartości. LINQ zapewnia kilka metod agregacji, takich jak <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Max%2A>. Metoda agregacji można utworzyć, dodając metodę rozszerzenia, aby <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Median` można obliczyć mediany sekwencji liczb typu `double`.  
  
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
  
 Chcesz wywołać tę metodę rozszerzenia dla dowolnej kolekcji wyliczalny tak samo jak inne metody agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 Poniższy przykład kodu pokazuje sposób użycia `Median` metodę dla tablicy typu `double`.  
  
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
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Przeciążenie to metoda agregacji do akceptowania różnych typów  
 Metoda agregacji można przeciążać tak, aby go akceptuje sekwencje różnych typów. Jest standardowego podejścia do tworzenia przeciążenia dla każdego typu. Innym rozwiązaniem jest tworzenie przeciążenia, które będą typu ogólnego i przekonwertować go do określonego typu za pomocą delegata. Można także połączyć oba podejścia.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Aby utworzyć przeciążenia dla każdego typu  
 Można utworzyć określonego przeciążenia dla każdego typu, które mają być obsługiwane. Poniższy przykład kodu pokazuje przeciążenie `Median` metodę `integer` typu.  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 Teraz można wywołać `Median` przeciążenia dla obu `integer` i `double` typów, jak pokazano w poniższym kodzie:  
  
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

#### <a name="to-create-a-generic-overload"></a>Aby utworzyć przeciążenie ogólne  
 Można również utworzyć przeciążenie, które akceptuje sekwencji ogólnych obiektów. Tego przeciążenia przyjmuje jako parametr delegata i używa go w celu konwersji sekwencji obiektów typu ogólnego dla określonego typu.  
  
 Poniższy kod pokazuje przeciążenie `Median` metody, która przyjmuje <xref:System.Func%602> delegować jako parametr. Ten delegat przyjmuje obiekt ogólny typ T i zwraca obiekt typu `double`.  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Teraz można wywołać `Median` metodę sekwencji obiektów dowolnego typu. Jeśli typ nie ma swój własny przeciążenia metody, należy przekazać parametr delegata. W języku C#, w tym celu można użyć wyrażenia lambda. Ponadto tylko w Visual Basic Jeśli używasz `Aggregate` lub `Group By` klauzuli zamiast wywołania metody które można przekazać dowolna wartość lub wyrażenie, który znajduje się w zakresie tej klauzuli.  
  
 Poniższy przykład kodu pokazuje sposób wywoływania `Median` Metoda tablicy liczb całkowitych i tablicę ciągów. Dla ciągów mediana dla długości ciągów w tablicy jest obliczana. W przykładzie pokazano sposób przekazywania <xref:System.Func%602> parametru, aby delegować `Median` metody dla każdego przypadku.  
  
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
## <a name="adding-a-method-that-returns-a-collection"></a>Dodawanie metody, które zwraca kolekcję  
 Możesz rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> interfejs za pomocą metody niestandardowe zapytanie, która zwraca sekwencję wartości. W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>. Takie metody może służyć do zastosowania przekształcenia danych lub filtrów do sekvence hodnot.  
  
 Poniższy przykład pokazuje, jak utworzyć metodę rozszerzenia o nazwie `AlternateElements` zwracającego każdy inny element w kolekcji, począwszy od pierwszego elementu.  
  
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
 Chcesz wywołać tę metodę rozszerzenia dla dowolnego wyliczalny kolekcji, tak samo, jak możesz wywołać innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.IEnumerable%601>
- [Metody rozszerzeń](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
