---
title: "Delegaci i wyrażeń lambda"
description: "Dowiedz się, jak delegatów Definiowanie typu, które określą podpisu konkretnej metody, które można wywołać bezpośrednio lub przekazana do innej metody i wywołać."
keywords: .NET, .NET core
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d418733ada67a1cb751bbfa74afee2eeeee04976
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="delegates-and-lambdas"></a>Delegaci i wyrażeń lambda

Obiekty delegowane Definiowanie typu, które określą sygnatury określonej metody. Metody (statyczny lub wystąpienia) odpowiadającej tego podpisu może być przypisany do zmiennej tego typu, a następnie wywołać bezpośrednio (za pomocą odpowiednie argumenty) lub przekazanego jako argument się do innej metody i następnie wywołuje. W poniższym przykładzie pokazano Użyj delegata.

```csharp
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

*   W wierszu 4 utworzymy typem obiektu delegowanego niektórych podpisu w tym przypadku metoda który przyjmuje parametr typu string i zwraca parametr typu string.
*   W wierszu 6 definiujemy implementacji delegata dzięki udostępnieniu metod, który ma dokładnie takiego samego podpisu.
*   W wierszu 13 metody jest przypisany do typu, który odpowiada `Reverse` delegowanie.
*   Na koniec wiersza 15 możemy wywołać delegata przekazywanie ciągu do wycofania.

W celu uproszczenia procesu tworzenia, .NET zawiera zestaw typów delegatów, które programiści mogą ponownie wykorzystać i nie trzeba tworzyć nowych typów. Są to `Func<>`, `Action<>` i `Predicate<>`, i mogą być używane w różnych miejscach interfejsów API architektury .NET bez konieczności do definiowania nowych typów delegata. Oczywiście są pewne różnice między trzy jak widać w ich sygnaturach, które przede wszystkim ze sposobem, które zostały one przeznaczone do użycia:

*   `Action<>`jest używany, gdy istnieje potrzeba wykonania akcji na podstawie argumentów delegata.
*   `Func<>`jest używana zazwyczaj, gdy masz transformację dostępnych produktów, oznacza to, należy przekształcić argumenty delegata w innych wyników. Projekcje są podstawowym przykładem.
*   `Predicate<>`jest używany podczas należy ustalić, jeśli argument spełnia warunek delegata. Można również będą zapisywane jako `Func<T, bool>`.

Możemy teraz pobrać naszym przykładzie powyżej i przepisywania za pomocą `Func<>` delegować zamiast typu niestandardowego. Program nadal będzie działać, dokładnie tak samo.

```csharp
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

W tym przykładzie prosty o metoda poza metodą Main() wydaje się nieco zbędny. Jest w związku z tym, że .NET Framework 2.0 wprowadzono koncepcję **anonimowych delegatów**. Z pomocy technicznej jest możliwość tworzenia delegatów "wbudowany" bez konieczności określania wszelkie dodatkowe typu lub metody. Możesz po prostu wbudowanej definicji delegata, w których należy.

Na przykład zamierzamy przełączyć go się i użyć naszych anonimowe delegata do odfiltrowywania listę tylko liczby parzyste i wydrukuj je w konsoli.

```csharp
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
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

Zwróć uwagę, wyróżnione wiersze. Jak widać, treść delegata jest tylko zestaw wyrażeń, co inne delegata. Ale gdy jest osobnym definicji, a nie dodaliśmy go _ad hoc_ w naszym wywołaniu `FindAll()` metody `List<T>` typu.

Jednak nawet w przypadku tej metody jest nadal większej ilości kodu, który mamy wyrzucać. Jest to, gdy **wyrażenia lambda** wchodzić w grę.

Wyrażenia lambda lub po prostu "wyrażeń lambda" skrócie, wprowadzono najpierw w języku C# 3.0 jako jeden z podstawowych bloków konstrukcyjnych z języka zintegrowane zapytania (LINQ). Są one tylko wygodniejsze składnia przy użyciu delegatów. One zadeklarować podpisu i treści metody, ale nie ma formalnych tożsamości we własnym, o ile nie są przypisane do delegata. W przeciwieństwie do delegatów bezpośrednio przypisać jako po lewej stronie rejestracji zdarzeń lub w wielu klauzul Linq i metod.

Wyrażenie lambda jest po prostu innym sposobem określania delegata, możemy powinno być możliwe do edycji w powyższym przykładzie, aby użyć wyrażenia lambda zamiast anonimowego obiektu delegowanego.

```csharp
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

Jeśli Spójrz na wyróżnione wiersze widać, jak wygląda wyrażenia lambda. Ponownie, to po prostu **bardzo** wygodny składnia przy użyciu delegatów, co się stanie, w obszarze obejmuje przypomina co się dzieje z anonimowego obiektem delegowanym.

Ponownie wyrażenia lambda są tylko delegatów, co oznacza może być używany jako program obsługi zdarzeń bez problemów, jak pokazano w poniższy fragment kodu.

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

## <a name="further-reading-and-resources"></a>Dalsze informacje i zasoby

*   [Delegaci](../../docs/csharp/programming-guide/delegates/index.md)
*   [Funkcje anonimowe](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [Wyrażenia lambda](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
