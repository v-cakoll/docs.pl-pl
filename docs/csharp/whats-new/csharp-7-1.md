---
title: "Nowości w języku C# 7.1"
description: "Przegląd nowych funkcji w języku C# 7.1."
keywords: "C# język projektu, 7.1, Visual Studio 2017 r."
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a>Nowości w języku C# 7.1

C# 7.1 to pierwszy punkt wersji języka C#. Umożliwia oznaczanie okresach wydania zwiększona dla języka. Służy nowe funkcje wcześniej, najlepszym rozwiązaniem, gdy każda nowa funkcja jest gotowe. C# 7.1 dodaje możliwość konfigurowania kompilatora do dopasowania określonej wersji języka. Który umożliwia decyzja o uaktualnienie narzędzia decyzja o uaktualnienie wersji językowych.

C# 7.1 dodaje [wybór wersji języka](#language-version-selection) element konfiguracji, trzy nowe funkcje językowe i nowe zachowanie kompilatora.

Dostępne są następujące nowe funkcje językowe w tej wersji:

* [`async``Main` — metoda](#async-main)
  - Punkt wejścia dla aplikacji może mieć `async` modyfikator.
* [`default`Wyrażenia dosłowne](#default-literal-expressions)
  - Gdy typ docelowy można wywnioskować, można użyć wyrażenia dosłowne domyślne w wyrażeniach wartości domyślne.
* [Nazwy elementów wywnioskowanych spójnej kolekcji](#inferred-tuple-element-names)
  - Od zainicjowania spójnej kolekcji w wielu przypadkach można wywnioskować nazwy elementów spójnej kolekcji.

Na koniec kompilator ma dwie opcje `/refout` i `/refonly` tego formantu [odwołania generowanie zestawów](#reference-assembly-generation).

## <a name="language-version-selection"></a>Wybór wersji języka

Kompilator języka C# obsługuje 7.1 C# w programie Visual Studio 2017 wersji 15 ustęp 3 lub .NET Core SDK 2.0. Jednak 7.1 funkcje są domyślnie wyłączone. Aby włączyć funkcje 7.1, musisz zmienić ustawienie wersji języka dla projektu.

W programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz **właściwości**. Wybierz **kompilacji** i wybierz **zaawansowane** przycisku. Na liście rozwijanej wybierz **C# najnowsza wersja pomocnicza (Najnowsza wersja)**, lub wersji **C# 7.1** jak pokazano w następującym obrazu. `latest` Wartość oznacza, że chcesz używać najnowszej wersji pomocniczej na bieżącym komputerze. `C# 7.1` Oznacza, że chcesz używać C# 7.1, nawet po udostępnieniu nowsze wersje pomocnicze.

![Ustawienie wersji językowej](./media/csharp-7-1/advanced-build-settings.png)

Alternatywnie można edytować plik "csproj" i dodawania lub modyfikowania następujące wiersze:

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Jeśli używasz programu Visual Studio IDE do aktualizacji plików csproj IDE tworzy osobne węzły dla każdej konfiguracji kompilacji. Będzie zazwyczaj wartość taka sama we wszystkich konfiguracjach kompilacji, ale należy jawnie ustaw dla każdej konfiguracji kompilacji, lub wybierz opcję "Wszystkie konfiguracje" po zmodyfikowaniu tego ustawienia. W pliku csproj, pojawi się następujące:

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Prawidłowe ustawienia dla `LangVersion` elementu są:

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

Ciągi specjalne `default` i `latest` rozwiązania do najnowszej wersji językowych główne i pomocnicze odpowiednio zainstalowana na maszynie kompilacji.

To ustawienie zapewnia oddzielenie instalowanie nowej wersji zestawu SDK i narzędzia w środowisku projektowania wybór uwzględnienie nowe funkcje językowe w projekcie. Najnowsze narzędzia i zestawu SDK można zainstalować na komputerze kompilacji. Każdy projekt można skonfigurować do korzystania z określonej wersji języka dla jego kompilacji.

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
