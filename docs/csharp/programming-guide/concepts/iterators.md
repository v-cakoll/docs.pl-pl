---
title: Iterowanie przez kolekcje wC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: d47dcf6e7748f85978b1b0bcf739b5d1280263f3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594967"
---
# <a name="iterators-c"></a>Iteratory (C#)

*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.

Metoda iteratora lub `get` akcesor wykonuje niestandardową iterację w kolekcji. Metoda iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz. Po osiągnięciu `yield return` instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Iterator z kodu klienta jest używany przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) lub zapytania LINQ.

W poniższym przykładzie pierwsza iteracja `foreach` pętli powoduje, że wykonywanie jest wykonywane `SomeNumbers` w metodzie iteratora do momentu osiągnięcia `yield return` pierwszej instrukcji. Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana. W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `yield return` instrukcji. Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie. Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.

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

Typem zwracanym metody iteratora `get` lub akcesora może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub. <xref:System.Collections.Generic.IEnumerator%601>

Możesz użyć `yield break` instrukcji, aby zakończyć iterację.

> [!NOTE]
> We wszystkich przykładach w tym temacie oprócz prostego przykładu iteratora [](../../language-reference/keywords/using-directive.md) należy uwzględnić dyrektywy using `System.Collections` dla `System.Collections.Generic` przestrzeni nazw i.

## <a name="simple-iterator"></a>Iterator prosty

Poniższy przykład zawiera pojedynczą `yield return` instrukcję, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) . W `Main`programie każda iteracja `foreach` treści instrukcji tworzy wywołanie funkcji iteratora, która przechodzi do następnej `yield return` instrukcji.

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

W poniższym przykładzie `DaysOfTheWeek` Klasa <xref:System.Collections.IEnumerable> implementuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> interfejs, który wymaga metody. Kompilator niejawnie wywołuje `GetEnumerator` metodę, która <xref:System.Collections.IEnumerator>zwraca.

Metoda zwraca każdy ciąg pojedynczo przy `yield return` użyciu instrukcji. `GetEnumerator`

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

Instrukcja odwołująca się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metodę. `foreach` Instrukcje odwołujące się `Birds` do właściwości `Mammals` i używają `AnimalsForType` nazwanego metody iteratora. `foreach`

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

## <a name="using-iterators-with-a-generic-list"></a>Używanie iteratorów z listą ogólną

W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> Klasa generyczna <xref:System.Collections.Generic.IEnumerable%601> implementuje interfejs generyczny. Metoda przypisuje wartości do tablicy typu `T`. <xref:System.Collections.Generic.Stack%601.Push%2A> Metoda zwraca wartości tablicy przy `yield return` użyciu instrukcji. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>

Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową <xref:System.Collections.IEnumerable.GetEnumerator%2A> . Wynika to z <xref:System.Collections.Generic.IEnumerable%601> faktu <xref:System.Collections.IEnumerable>, że dziedziczy z. Implementacja nieogólna odłożenia do ogólnej implementacji.

W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych. Te nazwane Iteratory to `TopToBottom` właściwości `TopN` i `BottomToTop` i metoda.

Właściwość używa iteratora `get` w metodzie dostępu. `BottomToTop`

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

Iterator może wystąpić jako metoda lub `get` akcesor. Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpienia, konstruktorze statycznym lub niestatycznego finalizatora.

Niejawna konwersja musi istnieć z typu wyrażenia w `yield return` instrukcji do argumentu Type dla elementu IEnumerable\<T > zwróconego przez iterator.

W C#programie Metoda iteratora nie może mieć `in`żadnych `ref`parametrów, `out` , ani.

W C#, "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany przed `return` słowem kluczowym or `break` .

## <a name="technical-implementation"></a>Realizacja techniczna

Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu. Ta klasa śledzi pozycję iteratora, tak długo `foreach` pętla w kodzie klienta jest kontynuowana.

Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który został wygenerowany dla metody iteratora.

Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/keywords/struct.md)nie trzeba implementować całego <xref:System.Collections.IEnumerator> interfejsu. Gdy kompilator wykryje `Current`iterator, automatycznie generuje metody <xref:System.Collections.IEnumerator> , `MoveNext`, <xref:System.Collections.Generic.IEnumerator%601> i `Dispose` interfejsu.

Dla każdej kolejnej iteracji `foreach` pętli (lub bezpośredniego wywołania do `IEnumerator.MoveNext`) Następna treść kodu iteratora zostanie wznowiona po poprzedniej `yield return` instrukcji. Następnie przechodzi do następnej `yield return` instrukcji do momentu osiągnięcia końca treści iteratora lub `yield break` do momentu napotkania instrukcji.

Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Aby wykonać ponowną iterację od początku, należy uzyskać nowy iterator. Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> iteratora zwróconego przez metodę iteratora <xref:System.NotSupportedException>generuje.

Aby uzyskać dodatkowe informacje, zobacz [ C# Specyfikacja języka](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Użycie iteratorów

Iteratory umożliwiają zachowanie prostoty `foreach` pętli, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:

- Zmodyfikuj sekwencję list po pierwszej `foreach` iteracji pętli.

- Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją `foreach` pętli. Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli. Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> Metoda, która implementuje Iteratory w .NET Framework.

- Hermetyzuje Kompilowanie listy w iterator. W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Używanie instrukcji foreach z tablicami](../arrays/using-foreach-with-arrays.md)
- [Typy ogólne](../generics/index.md)
