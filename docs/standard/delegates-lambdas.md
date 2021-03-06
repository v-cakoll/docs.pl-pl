---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, w jaki sposób Delegaty definiujące typ określający konkretny podpis metody można wywołać bezpośrednio lub przesłać do innej metody i wywołać metodę.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 184c9f61fd8456b22e8ecb262c131793160b49b0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244013"
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

* `public delegate string Reverse(string s);`Wiersz tworzy typ delegata o określonej sygnaturze, w tym przypadku metodę, która przyjmuje parametr String, a następnie zwraca parametr ciągu.
* `static string ReverseString(string s)`Metoda, która ma dokładnie taki sam podpis, jak zdefiniowany typ delegata, implementuje delegata.
* `Reverse rev = ReverseString;`Wiersz pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.
* `Console.WriteLine(rev("a string"));`Wiersz ilustruje sposób użycia zmiennej typu delegata do wywołania delegata.

Aby usprawnić proces opracowywania, platforma .NET zawiera zestaw typów delegatów, które programiści mogą ponownie wykorzystać i nie muszą tworzyć nowych typów. Te typy są `Func<>` , `Action<>` i `Predicate<>` i mogą być używane bez konieczności definiowania nowych typów delegatów. Istnieją pewne różnice między trzema typami, które należy wykonać w celu zamierzonego użycia:

* `Action<>`jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata. Metoda, która jest hermetyzowana, nie zwraca wartości.
* `Func<>`jest używany zwykle w przypadku, gdy istnieje transformacja, to jest konieczne przekształcenie argumentów delegata w inny wynik. Projekcje są dobrym przykładem. Metoda, która jest hermetyzowana, zwraca określoną wartość.
* `Predicate<>`jest używany, gdy należy określić, czy argument spełnia warunek delegata. Można go również napisać jako `Func<T, bool>` , co oznacza, że metoda zwraca wartość logiczną.

Teraz możemy skorzystać z naszego powyższego przykładu i napisać go ponownie przy użyciu `Func<>` delegata zamiast typu niestandardowego. Program będzie działał dokładnie tak samo.

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

W tym prostym przykładzie, jeśli metoda zdefiniowana poza tą `Main` metodą jest niezbędna. .NET Framework 2,0 wprowadził koncepcję *anonimowych delegatów*, która umożliwia tworzenie "wbudowanych" delegatów bez konieczności określania jakiegokolwiek dodatkowego typu lub metody.

W poniższym przykładzie delegat anonimowy filtruje listę tylko liczb parzystych, a następnie drukuje je w konsoli programu.

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

Jak widać, treść delegata jest tylko zestawem wyrażeń, jak każdy inny delegat. Ale zamiast tego nie jest to osobna definicja, wprowadziliśmy ją _ad hoc_ w wywołaniu <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metody.

Jednak nawet w przypadku tego podejścia nadal istnieje dużo kodu, który możemy zgłosić. Jest to miejsce, w którym *wyrażenia lambda* są odtwarzane. Wyrażenia lambda lub same "wyrażenia lambda" są stosowane w języku C# 3,0 jako jeden z podstawowych bloków konstrukcyjnych języka Integrated Query (LINQ). Jest to tylko bardziej wygodna Składnia służąca do używania delegatów. Deklarują sygnaturę i treść metody, ale nie mają formalnej tożsamości własnej, chyba że są przypisane do delegata. W przeciwieństwie do delegatów, mogą być bezpośrednio przypisane jako prawo do rejestracji zdarzeń lub w różnych klauzulach i metodach LINQ.

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

W poprzednim przykładzie użyte wyrażenie lambda ma wartość `i => i % 2 == 0` . Jest to tylko wygodna Składnia służąca do używania delegatów. Co się dzieje w obszarze okładek, podobnie jak w przypadku delegata anonimowego.

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

`+=`Operator w tym kontekście jest używany do subskrybowania [zdarzenia](../csharp/language-reference/keywords/event.md). Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Dalsze odczytywanie i zasoby

* [Delegaci](../csharp/programming-guide/delegates/index.md)
* [Funkcje anonimowe](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Wyrażenia lambda](../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
