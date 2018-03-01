---
title: "=&gt;Operator (odwołanie w C#)"
ms.date: 10/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44cb0485aefa8b0ab10a00ae0525180020ce436d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="gt-operator-c-reference"></a>=&gt;Operator (odwołanie w C#)

`=>` Operator może być używany na dwa sposoby w języku C#:

- Jako [operatora lambda](#lamba-operator) w [wyrażenia lambda](../../lambda-expressions.md), zmienne wejściowe go oddziela od treści lambda.
 
- W [definicja treść wyrażenia](#expression-body-definition), jego oddziela nazwę elementu członkowskiego z implementacją elementu. 

## <a name="lambda-operator"></a>Lambda operator

`=>` Token jest nazywany operatora lambda. Jest on używany w *wyrażenia lambda* do oddzielania zmienne wejściowe po lewej stronie z treści lambda po prawej stronie. Wyrażenia lambda są wbudowane wyrażenia podobna do metody anonimowe, ale bardziej elastyczne. są często używane w zapytań LINQ, które są wyrażane w składni metody. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Poniższy przykład przedstawia dwa sposoby, aby znaleźć i wyświetlić długość ciągu najkrótszy w tablicy ciągów. Pierwsza część przykładzie zastosowanie wyrażenia lambda (`w => w.Length`) do każdego elementu `words` tablicy, a następnie używa <xref:System.Linq.Enumerable.Min%2A> metody do znalezienia najmniejszej długości. Do porównania drugiej części przykładzie pokazano dłużej używaną do tak samo postąpić w składni zapytania.  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a>Uwagi  
 `=>` Operator ma takie samo pierwszeństwo jako operator przypisania (`=`) i jest łączny prawo.  
  
 Można jawnie określić typ zmiennej wejściowy lub pozwolić kompilatora wnioskować w obu przypadkach zmienna jest silnie typizowane w czasie kompilacji. Po określeniu typu, należy ująć w nazwy typu i nazwy zmiennych w nawiasach, jak przedstawiono na poniższym przykładzie.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wyrażenia lambda przeciążenia operatora standardowej kwerendy <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> który przyjmuje dwa argumenty. Wyrażenie lambda ma więcej niż jeden parametr, parametry muszą być ujęte w nawiasy. Drugi parametr `index`, reprezentuje indeks bieżącego elementu w kolekcji. `Where` Wyrażenie zwraca wszystkie ciągi o długości są mniejsze niż ich położenia indeks w tablicy.  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a>Definicja treść wyrażenia

Definicja treść wyrażenia udostępnia implementację elementu członkowskiego w postaci wysokiej skrócone, czytelne. Ma następującą składnię ogólne:

```csharp
member => expression;
```
gdzie *wyrażenie* jest prawidłowym wyrażeniem. Należy pamiętać, że *wyrażenie* może być *wyrażenia instrukcji* tylko jeśli element członkowski zwracany typ jest `void`, lub jeśli element jest konstruktorem lub finalizatora.

Definicje treść wyrażenia metody i instrukcje get właściwości są obsługiwane począwszy od języka C# 6. Wyrażenie treści definicji dla konstruktorów, finalizatory, instrukcje ustawić właściwości i indeksatorów są obsługiwane w programie C# 7.

Poniżej znajduje się definicja treść wyrażenia `Person.ToString` metody:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Jest to wersja skrócona definicji następujące metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
Aby uzyskać bardziej szczegółowe informacje dotyczące definicji treść wyrażenia, zobacz [zabudowanych wyrażenia elementów członkowskich](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Zobacz też  
[Odwołanie w C#](../../../csharp/language-reference/index.md)   
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)   
[Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
[Członkowie zabudowanych wyrażenia](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).