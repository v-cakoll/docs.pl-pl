---
title: 'Iterate przez kolekcje w C #'
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626273"
---
# <a name="iterators-c"></a>Iterytory (C#)

*Iterator* może służyć do kroku kolekcji, takich jak listy i tablice.

Metoda iterator `get` lub akcesor wykonuje niestandardowe iteracji za pomocą kolekcji. Metoda iterator używa [yield return](../../language-reference/keywords/yield.md) instrukcji do zwrócenia każdego elementu po jednym na raz. Po `yield return` osiągnięciu instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie. Wykonywanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji sterująca.

Użyj iterator z kodu klienta przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji lub przy użyciu kwerendy LINQ.

W poniższym przykładzie pierwsza iteracja `foreach` pętli powoduje wykonanie, `SomeNumbers` aby kontynuować w metodzie iteratorem, aż do osiągnięcia pierwszej `yield return` instrukcji. Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratorem jest zachowywana. W następnej iteracji pętli wykonanie w metodzie iteratorem jest kontynuowane od miejsca, `yield return` w którym zostało wyłączone, ponownie zatrzymując się po osiągnięciu instrukcji. Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratorem jest ponownie zachowywana. Pętla kończy się po osiągnięciu końca metody iterator.

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

Zwracany typ metody iteratorego `get` lub <xref:System.Collections.IEnumerable>akcesora może być , <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.

Można użyć `yield break` instrukcji, aby zakończyć iterację.

> [!NOTE]
> Dla wszystkich przykładów w tym temacie z wyjątkiem prostego iterator przykład, obejmują [przy użyciu](../../language-reference/keywords/using-directive.md) dyrektyw dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.

## <a name="simple-iterator"></a>Prosty iterator

Poniższy przykład ma `yield return` jedną instrukcję, która znajduje się wewnątrz [for](../../language-reference/keywords/for.md) pętli. W `Main`, każda iteracja treści `foreach` instrukcji tworzy wywołanie funkcji iterator, `yield return` która przechodzi do następnej instrukcji.

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a>Tworzenie klasy kolekcji

W poniższym `DaysOfTheWeek` przykładzie klasa implementuje <xref:System.Collections.IEnumerable> interfejs, <xref:System.Collections.IEnumerable.GetEnumerator%2A> który wymaga metody. Kompilator niejawnie wywołuje `GetEnumerator` metodę, która zwraca . <xref:System.Collections.IEnumerator>

Metoda `GetEnumerator` zwraca każdy ciąg jeden na `yield return` raz przy użyciu instrukcji.

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

Poniższy przykład tworzy `Zoo` klasę, która zawiera kolekcję zwierząt.

Instrukcja, `foreach` która odwołuje się`theZoo`do wystąpienia klasy `GetEnumerator` ( ) niejawnie wywołuje metodę. Instrukcje, `foreach` które odwołują `Birds` się do i `Mammals` właściwości użyć `AnimalsForType` metody o nazwie iterator.

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a>Korzystanie z iteratorów z listą ogólną

W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> implementuje interfejs ogólny. Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> przypisuje wartości do tablicy `T`typu . Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwraca wartości tablicy `yield return` przy użyciu instrukcji.

Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również <xref:System.Collections.IEnumerable.GetEnumerator%2A> wdrożyć metodę nierodzajową. Dzieje się <xref:System.Collections.Generic.IEnumerable%601> tak, <xref:System.Collections.IEnumerable>ponieważ dziedziczy z . Implementacja nierodzajowa odracza implementację ogólne.

W przykładzie używa nazwanych iteratorów do obsługi różnych sposobów iteracji za pośrednictwem tego samego zbierania danych. Te nazwane iteratory są `TopToBottom` `BottomToTop` i właściwości i `TopN` metody.

Właściwość `BottomToTop` używa iteratorem `get` w akcesorze.

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a>Informacje składni

Iterator może wystąpić jako `get` metoda lub akcesor. Iteratora nie może wystąpić w przypadku, konstruktora wystąpienia, konstruktora statycznego lub statycznego finalizatora.

Konwersja niejawna musi istnieć `yield return` od typu wyrażenia `IEnumerable<T>` w instrukcji do argumentu typu dla zwracanego przez iterator.

W języku C#, metoda iterator nie może mieć żadnych `in`, `ref`lub `out` parametry.

W języku `yield` C#, nie jest słowem zastrzeżonym `return` i `break` ma specjalne znaczenie tylko wtedy, gdy jest używany przed lub słowa kluczowego.

## <a name="technical-implementation"></a>Realizacja techniczna

Mimo że piszesz sterujące jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest w rzeczywistości maszyną stanu. Ta klasa śledzi położenie iterator tak długo, jak pętla `foreach` w kodzie klienta trwa.

Aby zobaczyć, co robi kompilator, można użyć narzędzia Ildasm.exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który jest generowany dla metody iteratora.

Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/builtin-types/struct.md)nie trzeba implementować <xref:System.Collections.IEnumerator> całego interfejsu. Gdy kompilator wykryje iterator, automatycznie `Current`generuje `MoveNext`, `Dispose` i metody <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> lub interfejsu.

Przy każdej kolejnej `foreach` iteracji pętli (lub `IEnumerator.MoveNext`bezpośredniego wywołania ), następna treść `yield return` kodu iteratora zostanie wznowiona po poprzedniej instrukcji. Następnie kontynuuje do `yield return` następnej instrukcji do końca treści iteratości zostanie `yield break` osiągnięty lub do momentu napotkania instrukcji.

Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Aby powtórzyć od samego początku, należy uzyskać nowy iterator. Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> iterator zwrócony metodą iteratorem <xref:System.NotSupportedException>wyrzuca .

For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Korzystanie z iteratorów

Iteratory umożliwiają zachowanie prostoty `foreach` pętli, gdy trzeba użyć złożonego kodu do wypełnienia sekwencji listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:

- Zmodyfikuj sekwencję listy po pierwszej `foreach` iteracji pętli.

- Należy unikać pełnego ładowania dużej listy przed `foreach` pierwszą iteracją pętli. Przykładem jest stronicowane pobieranie, aby załadować partię wierszy tabeli. Innym przykładem <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> jest metoda, która implementuje iteratory w ramach .NET Framework.

- Hermetyzować tworzenie listy w iteratorze. W metodzie iteratora można utworzyć listę, a następnie przynieść każdy wynik w pętli.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Używanie instrukcji foreach z tablicami](../arrays/using-foreach-with-arrays.md)
- [Typy ogólne](../generics/index.md)
