---
title: Iterowania przez kolekcje w języku C#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: d8a39569df517dffa8ff4b2f638f089f420e44c7
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508648"
---
# <a name="iterators-c"></a>Iteratory (C#)

*Iteratora* może służyć do kroku za pomocą kolekcji, takie jak listy i tablic.

Metody iteratora lub `get` akcesor wykonuje niestandardowych iteracji przez kolekcję. Wykorzystuje metodę iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcja zwraca każdy element w danym momencie. Gdy `yield return` osiągnięciu instrukcji zapamiętanych bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.

Korzystać z iteratora, z poziomu kodu klienta za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub za pomocą zapytań LINQ.

W poniższym przykładzie pierwszej iteracji `foreach` pętli powoduje wykonanie przejść w `SomeNumbers` metody iteratora, do momentu pierwszego `yield return` osiągnięta zostanie instrukcja. Tej iteracji zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana. Na następnej iteracji pętli wykonywania w metodzie iteratora jest kontynuowane od miejsca zostało przerwane, zatrzymywane ponownie po osiągnięciu `yield return` instrukcji. Tej iteracji zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora ponownie jest zachowywana. Pętla zostanie ukończone, gdy zostanie osiągnięty koniec metody iteratora.

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

Zwracany typ metody iteratora lub `get` dostępu mogą być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.

Możesz użyć `yield break` instrukcję, aby zakończyć iterację.

> [!NOTE]
> Wszystkie przykłady w tym temacie, chyba że w przykładzie prostego iteratora, obejmują [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.

## <a name="simple-iterator"></a>Prostego iteratora

W poniższym przykładzie przedstawiono jeden `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli. W `Main`, każda iteracja `foreach` treść instrukcji tworzy wywołanie funkcji iteratora, który przechodzi do następnej `yield return` instrukcji.

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

W poniższym przykładzie `DaysOfTheWeek` klasy implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. Kompilator niejawnie wywołuje `GetEnumerator` metody, która zwraca <xref:System.Collections.IEnumerator>.

`GetEnumerator` Metoda zwraca każdego ciągu, jeden w czasie za pomocą `yield return` instrukcji.

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

`foreach` Instrukcję, która odnosi się do wystąpienia klasy (`theZoo`) wywołuje niejawnie `GetEnumerator` metody. `foreach` Instrukcji odwołujących się do `Birds` i `Mammals` Użyj właściwości `AnimalsForType` o nazwie metody iteratora.

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

## <a name="using-iterators-with-a-generic-list"></a>Iteratory przy użyciu listy ogólnej

W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> implementuje klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny. <xref:System.Collections.Generic.Stack%601.Push%2A> Metoda przypisuje wartości do tablicy typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda zwraca wartości tablicy przy użyciu `yield return` instrukcji.

Oprócz ogólnego <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody, inną niż ogólna <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda również musi być implementowana. Jest to spowodowane <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable>. Implementacja nieogólnego różni się ogólną implementację.

W przykładzie użyto nazwanego Iteratory do obsługi różnych sposobów iteracji w tej samej kolekcji danych. O nazwie Iteratory są `TopToBottom` i `BottomToTop` właściwości, a `TopN` metody.

`BottomToTop` Właściwość używa iteratora w `get` metody dostępu.

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

## <a name="syntax-information"></a>Informacje o składni

Iterator może wystąpić jako metodę lub `get` metody dostępu. Iterator nie może wystąpić w zdarzeń, konstruktora wystąpienia, statyczny Konstruktor lub finalizatora statyczne.

Typ wyrażenia w musi istnieć niejawna konwersja `yield return` instrukcję, aby typ argumentu dla IEnumerable<T> zwrócony przez iterator.

W języku C#, metoda iteratora jest nie może zawierać żadnych `in`, `ref`, lub `out` parametrów.

W języku C# "yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używana przed `return` lub `break` — słowo kluczowe.

## <a name="technical-implementation"></a>Realizacja techniczna

Mimo, że piszesz iteratora jako metodę, kompilator tłumaczy je na klasę zagnieżdżoną oznacza to, w efekcie automatu stanów. Ta klasa śledzi informacje o położenie iteratora, jak długo `foreach` pętli w kodzie klienta będzie kontynuowane.

Aby zobaczyć, kompilator wykonuje, narzędzie Ildasm.exe służy również do wyświetlania kodu języka pośredniego firmy Microsoft, który jest generowany dla metody iteratora.

Po utworzeniu iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), nie trzeba implementować całego <xref:System.Collections.IEnumerator> interfejsu. Gdy kompilator wykryje iteratora, automatycznie generuje `Current`, `MoveNext`, i `Dispose` metody <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> interfejsu.

Na każdą kolejną iteracją z `foreach` pętli (lub bezpośrednie wywołanie `IEnumerator.MoveNext`), treść kodu następnego iteratora wznawia działanie po poprzedniej `yield return` instrukcji. Następnie będzie kontynuowane do następnego `yield return` instrukcji, dopóki nie zostanie osiągnięty koniec treści iteratora, lub do momentu `yield break` napotkania instrukcji.

Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Przypomnę od samego początku, należy pobrać nowe iteratora. Wywoływanie <xref:System.Collections.IEnumerator.Reset%2A> na zwracany przez metodę iteratora iterator zgłasza <xref:System.NotSupportedException>.

Aby uzyskać więcej informacji, zobacz [specyfikacji języka C#](../../../csharp/language-reference/language-specification/index.md).

## <a name="use-of-iterators"></a>Użyj Iteratory

Iteratory pozwalają zachować prostotę `foreach` pętli, gdy trzeba użyć złożonego kodu do wypełniania kolejność listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:

- Zmodyfikuj listę sekwencji po pierwszym `foreach` iteracji w pętli.

- Nie pełni ładował dużej listy przed pierwszą iteracją z `foreach` pętli. Przykładem jest stronicowane pobierania załadować partii wierszy tabeli. Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody, która implementuje Iteratory w ramach programu .NET Framework.

- Hermetyzuj, tworzenie listy dla iteratorów. W metodzie iteratora można tworzyć listy i następnie uzyskanie każdy wynik w pętli.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)
- [yield](../../../csharp/language-reference/keywords/yield.md)
- [Używanie instrukcji foreach z tablicami](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)