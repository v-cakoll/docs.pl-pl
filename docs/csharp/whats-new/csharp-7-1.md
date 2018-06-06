---
title: Nowości w języku C# 7.1
description: Przegląd nowych funkcji w języku C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728657"
---
# <a name="whats-new-in-c-71"></a>Nowości w języku C# 7.1

C# 7.1 to pierwszy punkt wersji języka C#. Umożliwia oznaczanie okresach wydania zwiększona dla języka. Służy nowe funkcje wcześniej, najlepszym rozwiązaniem, gdy każda nowa funkcja jest gotowe. C# 7.1 dodaje możliwość konfigurowania kompilatora do dopasowania określonej wersji języka. Który umożliwia decyzja o uaktualnienie narzędzia decyzja o uaktualnienie wersji językowych.

C# 7.1 dodaje [wybór wersji języka](../language-reference/configure-language-version.md) element konfiguracji, trzy nowe funkcje językowe i nowe zachowanie kompilatora.

Dostępne są następujące nowe funkcje językowe w tej wersji:

* [`async` `Main` — Metoda](#async-main)
  - Punkt wejścia dla aplikacji może mieć `async` modyfikator.
* [`default` Wyrażenia dosłowne](#default-literal-expressions)
  - Gdy typ docelowy można wywnioskować, można użyć wyrażenia dosłowne domyślne w wyrażeniach wartości domyślne.
* [Nazwy elementów wywnioskowanych spójnej kolekcji](#inferred-tuple-element-names)
  - Od zainicjowania spójnej kolekcji w wielu przypadkach można wywnioskować nazwy elementów spójnej kolekcji.

Na koniec kompilator ma dwie opcje `/refout` i `/refonly` tego formantu [odwołania generowanie zestawów](#reference-assembly-generation).

Aby korzystać z najnowszych funkcji w wersji punktu, należy [skonfigurować kompilatora wersji języka](../language-reference/configure-language-version.md) i wybierz wersję.

## <a name="async-main"></a>Asynchroniczne głównego

*Async głównego* metoda pozwala na użycie `await` w Twojej `Main` metody.
Wcześniej będzie potrzebny do zapisania:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Możesz teraz zapisać:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Jeśli program nie zwraca kod zakończenia, mogą zadeklarować `Main` metodę zwracającą <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Możesz przeczytać dodatkowe informacje szczegółowe informacje w [async głównego](../programming-guide/main-and-command-args/index.md) w Podręczniku programowania.

## <a name="default-literal-expressions"></a>Wyrażenia dosłowne domyślne

Wyrażenia dosłowne domyślne są ulepszeniem wyrażenia wartości domyślnej.
Wyrażenia te zainicjować zmiennej przy użyciu wartości domyślnej. Gdzie należy wcześniej zapisać:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Teraz można pominąć inicjowanie typ po prawej stronie:

```csharp
Func<string, bool> whereClause = default;
```

Użytkownik może dowiedzieć się więcej o to rozszerzenie w temacie C# przewodnik programowania w języku na [domyślna wartość wyrażenia](../programming-guide/statements-expressions-operators/default-value-expressions.md).

To rozszerzenie zmieniają się także niektóre reguły analizy [słowo kluczowe default](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Nazwy elementów wywnioskowanych spójnej kolekcji

Ta funkcja jest mała rozszerzenie funkcji krotek wprowadzono w języku C# w wersji 7.0. Wiele razy podczas inicjowania krotka zmiennych po prawej stronie przypisania są takie same jak nazwy, którą chcesz spójnej kolekcji elementów:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Nazwy elementów spójnej kolekcji można wywnioskować na podstawie zmiennych używaną do inicjalizacji spójna kolekcja znajdująca się w języku C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Dowiedz się więcej o tej funkcji w [krotek](../tuples.md) tematu.

## <a name="reference-assembly-generation"></a>Generowanie odwołania do zestawu

Dostępne są dwie opcje kompilatora nowe, które generują *tylko do odwołania zestawów*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) i [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
W połączonych tematach opisano te opcje i zestawy referencyjne bardziej szczegółowo.
