---
title: Co nowego w języku C# 7.1
description: Przegląd nowych funkcji w języku C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399708"
---
# <a name="whats-new-in-c-71"></a>Co nowego w języku C# 7.1

C# 7.1 jest pierwszym wydaniem punktowym do języka C#. Oznacza to zwiększoną kadencję uwalniania dla języka. Możesz korzystać z nowych funkcji wcześniej, najlepiej, gdy każda nowa funkcja jest gotowa. C# 7.1 dodaje możliwość skonfigurowania kompilatora do określonej wersji języka. Dzięki temu można oddzielić decyzję o uaktualnieniu narzędzi od decyzji o uaktualnieniu wersji językowych.

C# 7.1 dodaje element konfiguracji [wyboru wersji językowej,](../language-reference/configure-language-version.md) trzy nowe funkcje języka i nowe zachowanie kompilatora.

Nowe funkcje języka w tej wersji to:

- [`async``Main` metoda](#async-main)
  - Punkt wejścia dla aplikacji może `async` mieć modyfikator.
- [`default`wyrażenia dosłowne](#default-literal-expressions)
  - Można użyć domyślnych wyrażeń literału w domyślnych wyrażeniach wartości, gdy można wywnioskować typ docelowy.
- [Nazwy wywnioskowanych elementów krotki](#inferred-tuple-element-names)
  - Nazwy elementów krotki można wywnioskować z inicjowania krotki w wielu przypadkach.
- [Dopasowywanie wzorców dla parametrów typu ogólnego](#pattern-matching-on-generic-type-parameters)
  - Wyrażenia dopasowania wzorca można używać w zmiennych, których typ jest parametrem typu ogólnego.

Na koniec kompilator `-refout` `-refonly` ma dwie opcje i że kontrola [referencyjnego generowania zestawu](#reference-assembly-generation).

Aby korzystać z najnowszych funkcji w wersji punktowej, należy [skonfigurować wersję języka kompilatora](../language-reference/configure-language-version.md) i wybrać wersję.

W dalszej części tego artykułu przedstawiono omówienie każdej funkcji. Dla każdej funkcji dowiesz się, co za nią kryje. Dowiesz się składni. Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *próbek.*
1. Uruchom polecenie `dotnet try`.

## <a name="async-main"></a>Asynchroniczne główne

*Asynchroniczą główną* `await` metodą `Main` umożliwia użycie w metodzie.
Wcześniej trzeba było napisać:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Możesz teraz napisać:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Jeśli program nie zwraca kodu zakończenia, można `Main` zadeklarować metodę <xref:System.Threading.Tasks.Task>zwracającą:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Więcej informacji na temat szczegółów w głównym artykule [asynchronicznego](../programming-guide/main-and-command-args/index.md) można znaleźć w przewodniku po programowaniu.

## <a name="default-literal-expressions"></a>Domyślne wyrażenia literału

Domyślne wyrażenia literału są rozszerzeniem domyślnych wyrażeń wartości.
Wyrażenia te inicjują zmienną do wartości domyślnej. Gdzie wcześniej pisałeś:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Teraz można pominąć typ po prawej stronie inicjowania:

```csharp
Func<string, bool> whereClause = default;
```

Aby uzyskać więcej informacji, zobacz domyślną sekcję [literału](../language-reference/operators/default.md#default-literal) [w artykule operatora domyślnego.](../language-reference/operators/default.md)

## <a name="inferred-tuple-element-names"></a>Nazwy wywnioskowanych elementów krotki

Ta funkcja jest małym ulepszeniem funkcji krotek wprowadzonych w języku C# 7.0. Wiele razy podczas inicjowania krotki zmienne używane po prawej stronie przypisania są takie same jak nazwy, które chcesz dla elementów krotki:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Nazwy elementów krotki można wywnioskować ze zmiennych używanych do inicjowania krotki w języku C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Więcej informacji na temat tej funkcji można znaleźć w artykule [Krotek.](../tuples.md)

## <a name="pattern-matching-on-generic-type-parameters"></a>Dopasowywanie wzorców dla parametrów typu ogólnego

Począwszy od Języka C# 7.1 wyrażenie wzorca dla `is` i wzorzec `switch` typu może mieć typ parametru typu ogólnego. Może to być najbardziej przydatne podczas `struct` sprawdzania `class` typów, które mogą być lub typy i chcesz uniknąć boksu.

## <a name="reference-assembly-generation"></a>Generowanie zespołu referencyjnego

Istnieją dwie nowe opcje kompilatora, które generują *zestawy tylko do odwołania:* [-refout](../language-reference/compiler-options/refout-compiler-option.md) i [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Połączone artykuły wyjaśniają te opcje i zestawy odwołań bardziej szczegółowo.
