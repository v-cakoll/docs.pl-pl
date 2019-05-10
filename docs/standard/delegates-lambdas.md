---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak delegatów Definiowanie typu, które określą podpis konkretnej metody, które mogą być wywoływane bezpośrednio lub przekazana do innej metody o nazwie.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: e392f6b2e57bebf1ab916bc6142aebbc8f341db2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615324"
---
# <a name="delegates-and-lambdas"></a>Delegaci i wyrażenia lambda

Delegaty zdefiniować typ, które określą podpisu konkretnej metody. Metody (statyczny lub wystąpienia) odpowiadającej ten podpis mogą zostać przypisane do zmiennej tego typu, a następnie wywoływana bezpośrednio (z odpowiednimi argumentami) lub przekazywany jako argument sam do innej metody i następnie wywoływana. W poniższym przykładzie pokazano użycie delegata.

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

* `public delegate string Reverse(string s);` Wiersz tworzy typ delegata podpisu w tym przypadku metoda, która przyjmuje parametr ciąg, a następnie zwraca parametr ciągu.
* `static string ReverseString(string s)` Metody, która ma dokładnie tę samą sygnaturę jak typ delegata zdefiniowane, implementuje delegata.
* `Reverse rev = ReverseString;` Wiersz wskazuje, czy metody można przypisać do zmiennej odpowiedni typ delegata.
* `Console.WriteLine(rev("a string"));` Linii pokazuje, jak używana zmienna typu delegata do wywołania delegata.

W celu uproszczenia procesu tworzenia, .NET zawiera zbiór typami delegatów, które programiści mogą ponownie użyć i nie trzeba tworzyć nowe typy. Są to `Func<>`, `Action<>` i `Predicate<>`, i można ich używać w różnych miejscach interfejsów API platformy .NET bez konieczności do definiowania nowych typów obiektów delegowanych. Jak widać w ich sygnaturach, które przede wszystkim ze sposobem, w których zostały one przeznaczone do użycia istnieją oczywiście niektóre różnice między trzy:

* `Action<>` jest używany, gdy trzeba wykonać akcję przy użyciu argumentów delegata.
* `Func<>` jest używana zazwyczaj w przypadku transformacji w kasie, oznacza to, należy przekształcić argumenty delegata w różne wyniki. Prognozy są głównym przykładem.
* `Predicate<>` jest używany, gdy zachodzi potrzeba określenia, jeśli argument spełnia warunek delegata. Można również będą zapisywane jako `Func<T, bool>`.

Możemy teraz pobrać naszym powyższym przykładzie i ponownie napisać przy użyciu `Func<>` delegować zamiast typu niestandardowego. Program będzie nadal uruchomione, dokładnie tak samo.

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

W przypadku ten prosty przykład o metoda zdefiniowana poza `Main` metoda wydaje się nieco zbędny. Jest ze względu na to, że .NET Framework 2.0 wprowadzono koncepcję **anonimowe delegatów**. Za pomocą ich obsługa jest możliwe do tworzenia obiektów delegowanych "inline" bez konieczności określania żadnych dodatkowych typu lub metody. Możesz po prostu wbudowanej definicji delegata, gdy jej potrzebujesz.

Aby uzyskać przykład użyjemy zmienić się i użyj naszych delegata anonimowego, aby odfiltrować listę tylko liczby parzyste z zakresu, a następnie wydrukuj je w konsoli.

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

Jak widać, treść delegata jest po prostu zestaw wyrażeń, jak inne obiekt delegowany. Ale zamiast jej definicję oddzielne, wprowadziliśmy go _ad hoc_ w wywołaniu elementu naszych <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metody.

Jednak nawet w przypadku tej metody, ma nadal większej ilości kodu, który możemy wyrzucać. Jest to miejsce **wyrażeń lambda** dochodzą do głosu.

Wyrażenia lambda lub po prostu "wyrażenia lambda" w skrócie, zostały najpierw wprowadzone w systemie C# 3.0 jako jeden z podstawowych bloków konstrukcyjnych z Language Integrated Query (LINQ). Są one po prostu bardziej wygodne składnia przy użyciu delegatów. One deklarować podpisu i treści metody, ale nie ma formalnych tożsamości własnych, o ile nie są przypisane do delegata. W przeciwieństwie do delegatów bezpośrednio przypisać jako po lewej stronie rejestracji zdarzeń lub różne klauzule zapytań LINQ i metody.

Ponieważ wyrażenie lambda jest po prostu inny sposób określania delegata, firma Microsoft powinno być możliwe do przepisania w powyższym przykładzie, można użyć wyrażenia lambda zamiast delegata anonimowego.

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

W powyższym przykładzie jest używane wyrażenie lambda `i => i % 2 == 0`. Ponownie, jest po prostu **bardzo** wygodnej składni dla przy użyciu delegatów, więc co się stanie w sposób niewidoczny przypomina co się dzieje z delegata anonimowego.

Ponownie wyrażenia lambda są po prostu delegatów, co oznacza, że mogą być używane jako procedura obsługi zdarzeń bez problemów, tak jak pokazano w poniższym fragmencie kodu.

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

`+=` Operator w tym kontekście jest używany do subskrybowania [zdarzeń](../../docs/csharp/language-reference/keywords/event.md). Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="further-reading-and-resources"></a>Dalsze informacje i zasoby

* [Delegaty](../../docs/csharp/programming-guide/delegates/index.md)
* [Funkcje anonimowe](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Wyrażenia lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
