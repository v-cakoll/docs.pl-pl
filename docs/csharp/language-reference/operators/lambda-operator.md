---
title: =&gt; Operator - C# odwołania
ms.custom: seodec18
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: c193a91eaffe2e56a5df2afa8d66989981123a48
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238796"
---
# <a name="gt-operator-c-reference"></a>=&gt; Operator (odwołanie w C#)

`=>` Operator może być używany na dwa sposoby, w języku C#:

- Jako [operatora lambda](#lamba-operator) w [wyrażenia lambda](../../lambda-expressions.md), z treści lambda są dzielone zmienne wejściowe.
 
- W [definicja treści wyrażenia](#expression-body-definition), nazwa elementu członkowskiego rozdziela od implementacji elementu członkowskiego. 

## <a name="lambda-operator"></a>Lambda operator

`=>` Wywołanie operatora lambda tokenu. Jest on używany w *wyrażeń lambda* do oddzielania zmienne wejściowe po lewej stronie z treści lambda po prawej stronie. Wyrażenia lambda są wbudowane wyrażenia podobne do metod anonimowych, ale bardziej elastyczne. one są często używane w zapytaniach LINQ, które są wyrażone w składni metody. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Poniższy przykład przedstawia dwa sposoby, aby znaleźć i wyświetlić długość ciągu najkrótszej w tablicy ciągów. Pierwsza część przykładu stosuje się do wyrażenia lambda (`w => w.Length`) do każdego elementu `words` tablicy, a następnie używa <xref:System.Linq.Enumerable.Min%2A> metody do znalezienia najmniejszej długości. Dla porównania druga część przykład pokazuje dłużej rozwiązanie, które używa składni zapytań, aby zrobić to samo.  
  
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
 `=>` Operator ma takie samo pierwszeństwo jak operator przypisania (`=`) i jest zespolony z prawej.  
  
 Możesz jawnie określić typ zmienna wejściowa lub pozwolić kompilatorowi wydedukować w obu przypadkach zmienna zdecydowanie jest wpisane w czasie kompilacji. Po określeniu typu, należy ująć nazwę typu, a nazwa zmiennej w nawiasach, co ilustruje poniższy przykład.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyrażenia lambda przeciążenie metody standardowego operatora zapytania <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> która przyjmuje dwa argumenty. Ponieważ wyrażenie lambda ma więcej niż jeden parametr, parametry muszą być ujęte w nawiasy. Drugi parametr `index`, reprezentuje indeks bieżącego elementu w kolekcji. `Where` Wyrażenie zwraca wszystkie ciągi, których długości jest mniejsza od ich pozycji indeksu w tablicy.  
  
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
## <a name="expression-body-definition"></a>Definicja treści wyrażenia

Definicja treści wyrażenia dostarcza implementację elementu członkowskiego w wysoce skróconego postaci umożliwiającej odczyt. Ma następującej składni ogólnej:

```csharp
member => expression;
```
gdzie *wyrażenie* jest prawidłowym wyrażeniem. Należy pamiętać, że *wyrażenie* może być *wyrażenie instrukcji* tylko jeśli element członkowski zwracany typ jest `void`, lub, jeśli element jest konstruktor lub finalizatora.

Definicje treści wyrażenia dla metod i właściwości, instrukcje get są obsługiwane, począwszy od C# 6. Definicje treści wyrażenia dla konstruktorów finalizatorów, ustawić właściwości instrukcji, a indeksatory są obsługiwane, począwszy od C# 7.

Oto definicja treści wyrażenia dla `Person.ToString` metody:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Jest wersją skróconą następującą definicję metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
Aby uzyskać szczegółowe informacje na temat definicji treści wyrażenia, zobacz [elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)   
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)   
- [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- [Elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).