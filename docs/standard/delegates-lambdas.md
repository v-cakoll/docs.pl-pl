---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak delegaci, które definiują typ, który określa podpis określonej metody, mogą być wywoływane bezpośrednio lub przekazywane do innej metody i wywoływane.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: a9ca935814d1a7f77ded5f371ccd496c3859c523
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635930"
---
# <a name="delegates-and-lambdas"></a>Delegaci i wyrażenia lambda

Delegaci definiują typ, który określa podpis określonej metody. Metodę (statyczną lub wystąpienie), która spełnia ten podpis można przypisać do zmiennej tego typu, a następnie wywoływane bezpośrednio (z odpowiednimi argumentami) lub przekazywane jako argument się do innej metody, a następnie wywołane. W poniższym przykładzie pokazano delegowania wykorzystania.

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

* Wiersz `public delegate string Reverse(string s);` tworzy typ delegata określonego podpisu, w tym przypadku metodę, która przyjmuje parametr ciągu, a następnie zwraca parametr ciągu.
* Metoda, `static string ReverseString(string s)` która ma dokładnie taki sam podpis jak zdefiniowany typ delegata, implementuje pełnomocnika.
* Wiersz `Reverse rev = ReverseString;` pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.
* Wiersz `Console.WriteLine(rev("a string"));` pokazuje, jak używać zmiennej typu delegata do wywoływania pełnomocnika.

Aby usprawnić proces programowania, .NET zawiera zestaw typów delegatów, które programiści mogą ponownie używać i nie trzeba tworzyć nowe typy. Te typy `Action<>` `Predicate<>`są `Func<>`i , i mogą być używane bez konieczności definiowania nowych typów delegatów. Istnieją pewne różnice między trzema typami, które mają do czynienia ze sposobem, w jaki były przeznaczone do użycia:

* `Action<>`jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata. Metoda, która hermetyzuje nie zwraca wartości.
* `Func<>`jest używany zwykle, gdy masz transformację pod ręką, to znaczy, że należy przekształcić argumenty delegata w inny wynik. Projekcje są dobrym przykładem. Metoda, która hermetyzuje zwraca określoną wartość.
* `Predicate<>`jest używany, gdy trzeba ustalić, czy argument spełnia warunek delegata. Może być również zapisywany `Func<T, bool>`jako , co oznacza, że metoda zwraca wartość logiczną.

Możemy teraz wziąć nasz przykład powyżej i `Func<>` przepisać go przy użyciu pełnomocnika zamiast typu niestandardowego. Program będzie nadal działać dokładnie tak samo.

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

W tym prostym przykładzie o metody `Main` zdefiniowane poza metodą wydaje się nieco zbędne. .NET Framework 2.0 wprowadził pojęcie *anonimowych delegatów,* które umożliwiają tworzenie delegatów "wbudowanych" bez konieczności określania dodatkowego typu lub metody.

W poniższym przykładzie anonimowy delegat filtruje listę tylko do parzystych liczb, a następnie drukuje je na konsoli.

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

Jak widać, treść delegata jest tylko zestaw wyrażeń, jak każdy inny delegata. Ale zamiast oddzielnej definicji, wprowadziliśmy ją _ad hoc_ w <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> naszym wezwaniu do metody.

Jednak nawet przy takim podejściu nadal istnieje wiele kodu, który możemy wyrzucić. To jest, gdy *wyrażenia lambda* wchodzą w grę. Wyrażenia Lambda, lub po prostu "lambdas" w skrócie, zostały wprowadzone w języku C# 3.0 jako jeden z podstawowych bloków konstrukcyjnych języka zintegrowane zapytanie (LINQ). Są one po prostu bardziej wygodną składnią przy użyciu delegatów. Deklarują podpis i treść metody, ale nie mają formalnej tożsamości, chyba że są przypisane do delegata. W przeciwieństwie do delegatów, mogą być bezpośrednio przypisane jako po lewej stronie rejestracji zdarzeń lub w różnych klauzul linq i metod.

Ponieważ wyrażenie lambda jest tylko inny sposób określania delegata, powinniśmy być w stanie przepisać powyższe próbki do użycia wyrażenia lambda zamiast anonimowego delegata.

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

W poprzednim przykładzie użytym wyrażeniem `i => i % 2 == 0`lambda jest . Ponownie jest to tylko wygodna składnia do korzystania z delegatów. To, co dzieje się w ramach okładek, jest podobne do tego, co dzieje się z anonimowym pełnomocnikiem.

Ponownie lambdas są tylko delegatów, co oznacza, że mogą być używane jako program obsługi zdarzeń bez żadnych problemów, jak pokazuje poniższy fragment kodu.

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

Operator `+=` w tym kontekście służy do subskrybowania [zdarzenia](../../docs/csharp/language-reference/keywords/event.md). Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i anulować subskrypcję .](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

## <a name="further-reading-and-resources"></a>Dalsze czytanie i zasoby

* [Delegaty](../../docs/csharp/programming-guide/delegates/index.md)
* [Funkcje anonimowe](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Wyrażenia lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
