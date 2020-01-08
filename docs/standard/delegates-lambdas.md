---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak Delegaty definiują typ, który określa określoną sygnaturę metody, która może być wywoływana bezpośrednio lub przekazywać do innej metody i wywoływana.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 0abcc73e31eab89c422513acf778bc8bd092e788
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345550"
---
# <a name="delegates-and-lambdas"></a>Delegaci i wyrażenia lambda

Delegaty definiują typ, który określa określoną sygnaturę metody. Metoda (statyczna lub wystąpienie), która spełnia tę sygnaturę, może być przypisana do zmiennej tego typu, a następnie wywoływana bezpośrednio (z odpowiednimi argumentami) lub przekazana jako argument do innej metody, a następnie wywołana. Poniższy przykład demonstruje użycie delegata.

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* Wiersz `public delegate string Reverse(string s);` tworzy typ delegata o określonej sygnaturze, w tym przypadku metodę, która przyjmuje parametr ciągu, a następnie zwraca parametr ciągu.
* Metoda `static string ReverseString(string s)`, która ma dokładnie taki sam podpis jak zdefiniowany typ delegata, implementuje delegata.
* Wiersz `Reverse rev = ReverseString;` pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.
* W wierszu `Console.WriteLine(rev("a string"));` pokazano, jak używać zmiennej typu delegata do wywołania delegata.

Aby usprawnić proces opracowywania, platforma .NET zawiera zestaw typów delegatów, które programiści mogą ponownie wykorzystać i nie muszą tworzyć nowych typów. Są one `Func<>`, `Action<>` i `Predicate<>`i mogą być używane w różnych miejscach interfejsów API platformy .NET bez konieczności definiowania nowych typów delegatów. Oczywiście istnieją pewne różnice między trzema takimi elementami, jak w ich podpisach, które przede wszystkim mają być używane:

* `Action<>` jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata.
* `Func<>` jest używany zwykle w przypadku przekształcania, to oznacza, że należy przekształcić argumenty delegata na inny wynik. Projekcje są głównym przykładem.
* `Predicate<>` jest używany, gdy konieczne jest określenie, czy argument spełnia warunek delegata. Można go również napisać jako `Func<T, bool>`.

Teraz możemy skorzystać z naszego powyższego przykładu i napisać go ponownie przy użyciu delegata `Func<>` zamiast typu niestandardowego. Program będzie działał dokładnie tak samo.

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

W tym prostym przykładzie posiadanie metody zdefiniowanej poza metodą `Main` wydaje się nieco zbędne. Wynika to z tego, że .NET Framework 2,0 wprowadza koncepcję **anonimowych delegatów**. Dzięki obsłudze można tworzyć delegatów "inline" bez konieczności określania dodatkowego typu lub metody. Po prostu utworzysz definicję delegata, gdzie go potrzebujesz.

Na przykład przełączymy ją i użyjemy anonimowego delegata, aby odfiltrować listę tylko parzystych liczb, a następnie wydrukować je w konsoli programu.

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

Jak widać, treść delegata jest tylko zestawem wyrażeń, jak każdy inny delegat. Ale zamiast tego nie jest to osobna definicja, wprowadziliśmy ją _ad hoc_ w wywołaniu metody <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType>.

Jednak nawet w przypadku tego podejścia nadal istnieje dużo kodu, który możemy zgłosić. Jest to miejsce, w którym **wyrażenia lambda** są odtwarzane.

Wyrażenia lambda lub tylko "lambda" są krótkie, najpierw wprowadzane w C# 3,0, jako jeden z podstawowych bloków konstrukcyjnych języka (LINQ). Jest to tylko bardziej wygodna Składnia służąca do używania delegatów. Deklarują sygnaturę i treść metody, ale nie mają formalnej tożsamości własnej, chyba że są przypisane do delegata. W przeciwieństwie do delegatów, można bezpośrednio przypisywać je po lewej stronie rejestracji zdarzeń lub w różnych klauzulach i metodach LINQ.

Ponieważ wyrażenie lambda jest już innym sposobem określania delegata, powinno być możliwe przepisanie powyższego przykładu, aby użyć wyrażenia lambda zamiast anonimowego delegata.

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

W poprzednim przykładzie użyte wyrażenie lambda jest `i => i % 2 == 0`. Ponownie jest to tylko **bardzo** wygodna Składnia służąca do używania delegatów, co się dzieje w obszarze okładek, podobnie jak w przypadku delegata anonimowego.

Ponownie wyrażenia lambda są tylko delegatami, co oznacza, że mogą być używane jako program obsługi zdarzeń bez żadnych problemów, co ilustruje poniższy fragment kodu.

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

Operator `+=` w tym kontekście jest używany do subskrybowania [zdarzenia](../../docs/csharp/language-reference/keywords/event.md). Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Dalsze odczytywanie i zasoby

* [Delegaci](../../docs/csharp/programming-guide/delegates/index.md)
* [Funkcje anonimowe](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Wyrażenia lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
