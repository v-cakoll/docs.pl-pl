---
title: Co nowego C# 7.1
description: Omówienie nowych funkcji w C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480966"
---
# <a name="whats-new-in-c-71"></a>Co nowego C# 7.1

C#7.1 to pierwsze wydanie punkt do C# języka. Oznacza cykl zwiększone wersji języka. Umożliwia nowe funkcje wcześniej, najlepiej w przypadku każdej nowej funkcji jest gotowy. C#7.1 dodaje możliwość konfigurowania kompilatora odpowiadający określonej wersji języka. Która pozwala oddzielić decyzja do uaktualnienia narzędzi od decyzji o uaktualnienie wersji językowych.

C#7.1 dodaje [wybór wersji języka](../language-reference/configure-language-version.md) element konfiguracji, trzy nowe funkcje języka i nowe zachowanie kompilatora.

Dostępne są następujące nowe funkcje języka w tej wersji:

* [`async` `Main` — Metoda](#async-main)
  - Punkt wejścia dla aplikacji może mieć `async` modyfikator.
* [`default` wyrażenia literału](#default-literal-expressions)
  - Można używać wyrażeń literał domyślny w wyrażeniach wartości domyślne, gdy można wywnioskować typu docelowego.
* [Wywnioskowane nazwy elementów krotki](#inferred-tuple-element-names)
  - Od inicjowania krotki w wielu przypadkach można wywnioskować nazwami elementów krotki.
* [Dopasowania do wzorca w parametrach typu ogólnego](#pattern-matching-on-generic-type-parameters)
  - Wyrażenia dopasowania wzorca można użyć zmiennych, którego typem jest parametr typu ogólnego.

Na koniec, kompilator zawiera dwie pozycje `/refout` i `/refonly` tej kontrolki [odwoływać się do generowania zestawu](#reference-assembly-generation).

Korzystanie z najnowszych funkcji w wersji punktu należy [skonfigurować wersję językową kompilatora](../language-reference/configure-language-version.md) i wybierz wersję.

## <a name="async-main"></a>Asynchroniczna funkcja main

*Asynchroniczna funkcja main* metoda umożliwia użycie `await` w swojej `Main` metody.
Wcześniej należy napisać:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Teraz można napisać:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Jeśli program nie zwraca kod zakończenia, możesz zadeklarować `Main` metodę, która zwraca <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Możesz dowiedzieć się więcej o szczegółach w [asynchroniczna funkcja main](../programming-guide/main-and-command-args/index.md) artykułu w Podręczniku programowania.

## <a name="default-literal-expressions"></a>Wyrażenia literału domyślnego

Wyrażenia literału domyślnego stanowią rozszerzenie wyrażenia wartości domyślnych.
Te wyrażenia Zainicjuj zmienną do wartości domyślnej. Gdzie należy wcześniej napisać:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Można teraz pominąć typ po prawej stronie inicjowania:

```csharp
Func<string, bool> whereClause = default;
```

Dowiedz się więcej na temat to rozszerzenie w C# przewodnik programowania w artykule dotyczącym [domyślna wartość wyrażenia](../programming-guide/statements-expressions-operators/default-value-expressions.md).

To ulepszenie zmienia się również niektóre reguły analizy składni dla [default — słowo kluczowe](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Wywnioskowane nazwy elementów krotki

Ta funkcja jest mały ulepszenie funkcji krotek, wprowadzona w C# 7.0. Wiele razy podczas inicjowania spójną kolekcję zmiennych po prawej stronie przypisania są takie same jak nazwy, które Twoim zdaniem elementów krotki:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Nazwy elementów krotki można wywnioskować na podstawie zmiennych, używane do zainicjowania spójna kolekcja znajdująca się w C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Dowiedz się więcej na temat tej funkcji w [krotek](../tuples.md) artykułu.

## <a name="pattern-matching-on-generic-type-parameters"></a>Dopasowania do wzorca w parametrach typu ogólnego

Począwszy od C# 7.1, wyrażenie nie zawiera wzorca `is` i `switch` typu wzorzec może być typem parametru typu ogólnego. Może to być najbardziej przydatne, gdy sprawdzanie typów, które mogą być albo `struct` lub `class` typów i chcesz uniknąć pakowania.

## <a name="reference-assembly-generation"></a>Generowanie zestawu odwołania

Istnieją dwie nowe opcje kompilatora, które generują *tylko do odwołania zestawów*: [jest opcja](../language-reference/compiler-options/refout-compiler-option.md) i [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Połączonych artykułów opisano te opcje i zestawy odwołań bardziej szczegółowo.
