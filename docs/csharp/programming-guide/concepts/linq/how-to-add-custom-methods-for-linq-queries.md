---
title: 'Porady: dodawanie metod niestandardowych do kwerend LINQ (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: cd282b4b8ee4add759070317d9dbc3f78c07abf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Porady: dodawanie metod niestandardowych do kwerend LINQ (C#)
Można rozszerzyć zestaw metod, których można używać do kwerend LINQ przez dodanie metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład oprócz standardowych średniej lub maksymalna operacji, można tworzyć niestandardowe metody agregacji do obliczenia wartości jednego z sekwencji wartości. Można również utworzyć metodę, która działa jako filtr niestandardowy lub przekształcania określonych danych sekwencji wartości i zwraca nową sekwencję. Przykłady takich metod <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Po rozszerzeniu <xref:System.Collections.Generic.IEnumerable%601> interfejsu, niestandardowe metody można zastosować do żadnej kolekcji wyliczalny. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Dodawanie metody agregacji  
 Metoda agregacji oblicza pojedynczą wartość z zestawu wartości. LINQ udostępnia kilka metod agregacji, w tym <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Max%2A>. Łączny metodę można utworzyć przez dodanie metody rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia metodę rozszerzenia o nazwie `Median` można obliczyć mediany sekwencji liczb typu `double`.  
  
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
  
 Wywołanie tej metody rozszerzenia dla dowolnej kolekcji wyliczalny w taki sam sposób wywołania innych metod agregacji z <xref:System.Collections.Generic.IEnumerable%601> interfejsu.  
  
 Poniższy przykładowy kod przedstawia sposób użycia `Median` metodę dla tablicy typu `double`.  
  
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
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Przeładowanie metody agregacji do akceptowania różnych typów  
 Można przeciążać metodę agregacji, tak, aby akceptowane sekwencji różnych typów. Standardowa podejście jest tworzenie przeciążenia dla każdego typu. Innym rozwiązaniem jest tworzenie przeciążenia, które otrzymuje typu ogólnego i przekonwertować go do określonego typu za pomocą delegata. Można także połączyć obu podejść.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Aby utworzyć przeciążenia dla każdego typu  
 Można utworzyć określonego przeciążenia dla poszczególnych typów, które mają być obsługiwane. Poniższy przykład kodu pokazuje przeciążenia `Median` metodę `integer` typu.  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 Można teraz wywołać `Median` przeciążenia dla obu `integer` i `double` typy, jak pokazano w poniższym kodzie:  
  
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

#### <a name="to-create-a-generic-overload"></a>Aby utworzyć ogólnego przeciążenia  
 Można również utworzyć przeciążenia, które akceptuje sekwencji ogólnych obiektów. To przeciążenie delegata jako parametr przyjmuje i używa go do konwersji sekwencji obiektów typu ogólnego określonego typu.  
  
 Poniższy kod przedstawia przeciążenia `Median` metody pobierającej <xref:System.Func%602> delegata jako parametr. Ten delegat przyjmuje ogólnego typu T obiektu i zwraca obiekt typu `double`.  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Można teraz wywołać `Median` metody sekwencji obiekty dowolnego typu. Jeśli typ nie ma własną przeciążenie metody, należy przekazać parametr delegata. W języku C# w tym celu można użyć wyrażenia lambda. Ponadto w języku Visual Basic tylko jeśli używasz `Aggregate` lub `Group By` klauzuli zamiast wywołania metody, można przekazać dowolna wartość lub wyrażenie, które znajduje się w zakresie tej klauzuli.  
  
 Poniższy przykład kodu pokazuje sposób wywoływania `Median` Metoda tablicy liczb całkowitych i Tablica ciągów. Ciągi jest obliczana mediana dla długości ciągów w tablicy. W przykładzie pokazano sposób przekazywania <xref:System.Func%602> przekazać parametr `Median` metody dla każdego przypadku.  
  
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
 Można rozszerzyć <xref:System.Collections.Generic.IEnumerable%601> interfejsu za pomocą metody niestandardowe zapytanie zwracające sekwencję wartości. W tym przypadku metoda musi zwracać kolekcję typu <xref:System.Collections.Generic.IEnumerable%601>. Tych metod można zastosować filtry lub danych transformacje z wartości sekwencji.  
  
 Poniższy przykład przedstawia sposób tworzenia metodę rozszerzenia o nazwie `AlternateElements` zwracającą każdego innego elementu w kolekcji, rozpoczynając od pierwszego elementu.  
  
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
 Można wywołać tej metody rozszerzenia dla dowolnej kolekcji wyliczalny tak samo, jak możesz wywołać innych metod z <xref:System.Collections.Generic.IEnumerable%601> interfejsu, jak pokazano w poniższym kodzie:  
  
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
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Metody rozszerzeń](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
