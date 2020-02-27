---
title: Iterowanie przez kolekcje wC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626273"
---
# <a name="iterators-c"></a>Iteratory (C#)

*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.

Metoda iteratora lub akcesor `get` wykonuje niestandardową iterację w kolekcji. Metoda iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz. Po osiągnięciu instrukcji `yield return` bieżąca lokalizacja w kodzie jest zapamiętywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Iterator z kodu klienta jest używany przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) lub zapytania LINQ.

W poniższym przykładzie pierwsza iteracja pętli `foreach` powoduje, że wykonanie w metodzie iteratora `SomeNumbers` do momentu osiągnięcia pierwszej instrukcji `yield return`. Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana. W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `yield return`. Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie. Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.

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

Typem zwracanym metody iteratora lub metodzie dostępu `get` może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.

Możesz użyć instrukcji `yield break`, aby zakończyć iterację.

> [!NOTE]
> We wszystkich przykładach w tym temacie oprócz prostego przykładu iteratora należy uwzględnić dyrektywy [using](../../language-reference/keywords/using-directive.md) dla przestrzeni nazw `System.Collections` i `System.Collections.Generic`.

## <a name="simple-iterator"></a>Iterator prosty

Poniższy przykład zawiera jedną instrukcję `yield return`, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) . W `Main`każda iteracja treści instrukcji `foreach` tworzy wywołanie funkcji iteratora, która przechodzi do następnej instrukcji `yield return`.

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

W poniższym przykładzie Klasa `DaysOfTheWeek` implementuje interfejs <xref:System.Collections.IEnumerable>, który wymaga metody <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Kompilator niejawnie wywołuje metodę `GetEnumerator`, która zwraca <xref:System.Collections.IEnumerator>.

Metoda `GetEnumerator` zwraca każdy ciąg pojedynczo przy użyciu instrukcji `yield return`.

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

Poniższy przykład tworzy klasę `Zoo`, która zawiera kolekcję zwierząt.

Instrukcja `foreach`, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje metodę `GetEnumerator`. Instrukcje `foreach` odwołujące się do właściwości `Birds` i `Mammals` używają metody iteratora o nazwie `AnimalsForType`.

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

W poniższym przykładzie Klasa generyczna <xref:System.Collections.Generic.Stack%601> implementuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601>. Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> przypisuje wartości do tablicy typu `T`. Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwraca wartości tablicy przy użyciu instrukcji `yield return`.

Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową <xref:System.Collections.IEnumerable.GetEnumerator%2A>. Dzieje się tak, ponieważ <xref:System.Collections.Generic.IEnumerable%601> dziedziczy po <xref:System.Collections.IEnumerable>. Implementacja nieogólna odłożenia do ogólnej implementacji.

W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych. Te nazwane Iteratory są właściwościami `TopToBottom` i `BottomToTop` i metodą `TopN`.

Właściwość `BottomToTop` używa iteratora w metodzie dostępu `get`.

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

Iterator może wystąpić jako metoda dostępu metody lub `get`. Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpienia, konstruktorze statycznym lub niestatycznego finalizatora.

Niejawna konwersja musi istnieć z typu wyrażenia w instrukcji `yield return` do argumentu Type dla `IEnumerable<T>` zwróconego przez iterator.

W C#programie Metoda iteratora nie może mieć żadnych parametrów `in`, `ref`lub `out`.

W C#, `yield` nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany przed słowem kluczowym `return` lub `break`.

## <a name="technical-implementation"></a>Realizacja techniczna

Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu. Ta klasa śledzi pozycję iteratora, tak długo pętla `foreach` w kodzie klienta kontynuuje działanie.

Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który został wygenerowany dla metody iteratora.

Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/builtin-types/struct.md)nie trzeba implementować całego interfejsu <xref:System.Collections.IEnumerator>. Gdy kompilator wykryje iterator, automatycznie generuje metody `Current`, `MoveNext`i `Dispose` interfejsu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601>.

Dla każdej kolejnej iteracji pętli `foreach` (lub bezpośredniego wywołania do `IEnumerator.MoveNext`) Następna treść kodu iteratora zostanie wznowiona po poprzedniej instrukcji `yield return`. Następnie przechodzi do następnej instrukcji `yield return` do momentu osiągnięcia końca treści iteratora lub do momentu napotkania instrukcji `yield break`.

Iteratory nie obsługują metody <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>. Aby wykonać ponowną iterację od początku, należy uzyskać nowy iterator. Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> w iterator zwrócone przez metodę iteratora zgłasza <xref:System.NotSupportedException>.

Aby uzyskać dodatkowe informacje, zobacz [ C# Specyfikacja języka](~/_csharplang/spec/classes.md#iterators).

## <a name="use-of-iterators"></a>Użycie iteratorów

Iteratory umożliwiają zachowanie prostoty pętli `foreach`, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy. Może to być przydatne, gdy chcesz wykonać następujące czynności:

- Zmodyfikuj sekwencję list po pierwszej iteracji pętli `foreach`.

- Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją pętli `foreach`. Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli. Innym przykładem jest metoda <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, która implementuje Iteratory w .NET Framework.

- Hermetyzuje Kompilowanie listy w iterator. W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [yield](../../language-reference/keywords/yield.md)
- [Używanie instrukcji foreach z tablicami](../arrays/using-foreach-with-arrays.md)
- [Typy ogólne](../generics/index.md)
