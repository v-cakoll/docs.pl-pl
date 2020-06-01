---
title: 'Iterowanie za poorednictwem kolekcji w języku C #'
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 15b77fd11c0ff606119425ec7aae8e7127315e82
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240697"
---
# <a name="iterators-c"></a>Iteratory (C#)

*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.

Metoda iteratora lub `get` akcesor wykonuje niestandardową iterację w kolekcji. Metoda iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz. Po `yield return` osiągnięciu instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Iterator z kodu klienta jest używany przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) lub zapytania LINQ.

W poniższym przykładzie pierwsza iteracja pętli powoduje, że `foreach` wykonywanie jest wykonywane w `SomeNumbers` metodzie iteratora do momentu `yield return` osiągnięcia pierwszej instrukcji. Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana. W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `yield return` instrukcji. Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie. Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.

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

Typem zwracanym metody iteratora lub `get` akcesora może być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> , lub <xref:System.Collections.Generic.IEnumerator%601> .

Możesz użyć instrukcji, `yield break` Aby zakończyć iterację.

> [!NOTE]
> We wszystkich przykładach w tym temacie oprócz prostego przykładu iteratora [using](../../language-reference/keywords/using-directive.md) należy uwzględnić dyrektywy using `System.Collections` dla `System.Collections.Generic` przestrzeni nazw i.

## <a name="simple-iterator"></a>Iterator prosty

Poniższy przykład zawiera pojedynczą `yield return` instrukcję, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) . W programie `Main` każda iteracja `foreach` treści instrukcji tworzy wywołanie funkcji iteratora, która przechodzi do następnej `yield return` instrukcji.

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

W poniższym przykładzie `DaysOfTheWeek` Klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. Kompilator niejawnie wywołuje `GetEnumerator` metodę, która zwraca <xref:System.Collections.IEnumerator> .

`GetEnumerator`Metoda zwraca każdy ciąg pojedynczo przy użyciu `yield return` instrukcji.

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

`foreach`Instrukcja odwołująca się do wystąpienia klasy ( `theZoo` ) niejawnie wywołuje `GetEnumerator` metodę. `foreach`Instrukcje odwołujące się do `Birds` `Mammals` właściwości i używają `AnimalsForType` nazwanego metody iteratora.

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

W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> Klasa generyczna implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny. <xref:System.Collections.Generic.Stack%601.Push%2A>Metoda przypisuje wartości do tablicy typu `T` . <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Metoda zwraca wartości tablicy przy użyciu `yield return` instrukcji.

Oprócz <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody ogólnej <xref:System.Collections.IEnumerable.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową. Wynika to z faktu, że <xref:System.Collections.Generic.IEnumerable%601> dziedziczy z <xref:System.Collections.IEnumerable> . Implementacja nieogólna odłożenia do ogólnej implementacji.

W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych. Te nazwane Iteratory to `TopToBottom` właściwości i i `BottomToTop` `TopN` Metoda.

`BottomToTop`Właściwość używa iteratora w `get` metodzie dostępu.

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

Niejawna konwersja musi istnieć z typu wyrażenia w `yield return` instrukcji do argumentu typu `IEnumerable<T>` zwracanego przez iterator.

W języku C# Metoda iteratora nie może mieć `in` żadnych `ref` parametrów,, ani `out` .

W języku C#, `yield` nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany `return` przed `break` słowem kluczowym or.

## <a name="technical-implementation"></a>Realizacja techniczna

Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu. Ta klasa śledzi pozycję iteratora, tak długo `foreach` Pętla w kodzie klienta jest kontynuowana.

Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który został wygenerowany dla metody iteratora.

Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/builtin-types/struct.md)nie trzeba implementować całego <xref:System.Collections.IEnumerator> interfejsu. Gdy kompilator wykryje iterator, automatycznie generuje `Current` `MoveNext` metody,, i `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> interfejsu.

Dla każdej kolejnej iteracji `foreach` pętli (lub bezpośredniego wywołania do `IEnumerator.MoveNext` ) Następna treść kodu iteratora zostanie wznowiona po poprzedniej `yield return` instrukcji. Następnie przechodzi do następnej `yield return` instrukcji do momentu osiągnięcia końca treści iteratora lub do momentu `yield break` napotkania instrukcji.

Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Aby wykonać ponowną iterację od początku, należy uzyskać nowy iterator. Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> iteratora zwróconego przez metodę iteratora generuje <xref:System.NotSupportedException> .

Aby uzyskać dodatkowe informacje, zobacz [specyfikację języka C#](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Użycie iteratorów

Iteratory umożliwiają zachowanie prostoty `foreach` pętli, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:

- Zmodyfikuj sekwencję list po pierwszej `foreach` iteracji pętli.

- Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją `foreach` pętli. Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli. Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> Metoda, która implementuje Iteratory w programie .NET.

- Hermetyzuje Kompilowanie listy w iterator. W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Używanie instrukcji foreach z tablicami](../arrays/using-foreach-with-arrays.md)
- [Typy ogólne](../generics/index.md)
