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
# <a name="whats-new-in-c-71"></a><span data-ttu-id="f67fe-103">Nowości w języku C# 7.1</span><span class="sxs-lookup"><span data-stu-id="f67fe-103">What's new in C# 7.1</span></span>

<span data-ttu-id="f67fe-104">C# 7.1 to pierwszy punkt wersji języka C#.</span><span class="sxs-lookup"><span data-stu-id="f67fe-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="f67fe-105">Umożliwia oznaczanie okresach wydania zwiększona dla języka.</span><span class="sxs-lookup"><span data-stu-id="f67fe-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="f67fe-106">Służy nowe funkcje wcześniej, najlepszym rozwiązaniem, gdy każda nowa funkcja jest gotowe.</span><span class="sxs-lookup"><span data-stu-id="f67fe-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="f67fe-107">C# 7.1 dodaje możliwość konfigurowania kompilatora do dopasowania określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="f67fe-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="f67fe-108">Który umożliwia decyzja o uaktualnienie narzędzia decyzja o uaktualnienie wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="f67fe-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="f67fe-109">C# 7.1 dodaje [wybór wersji języka](../language-reference/configure-language-version.md) element konfiguracji, trzy nowe funkcje językowe i nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f67fe-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="f67fe-110">Dostępne są następujące nowe funkcje językowe w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="f67fe-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="f67fe-111">`async` `Main` — Metoda</span><span class="sxs-lookup"><span data-stu-id="f67fe-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f67fe-112">Punkt wejścia dla aplikacji może mieć `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="f67fe-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="f67fe-113">`default` Wyrażenia dosłowne</span><span class="sxs-lookup"><span data-stu-id="f67fe-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f67fe-114">Gdy typ docelowy można wywnioskować, można użyć wyrażenia dosłowne domyślne w wyrażeniach wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="f67fe-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="f67fe-115">Nazwy elementów wywnioskowanych spójnej kolekcji</span><span class="sxs-lookup"><span data-stu-id="f67fe-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="f67fe-116">Od zainicjowania spójnej kolekcji w wielu przypadkach można wywnioskować nazwy elementów spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f67fe-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="f67fe-117">Na koniec kompilator ma dwie opcje `/refout` i `/refonly` tego formantu [odwołania generowanie zestawów](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="f67fe-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="f67fe-118">Aby korzystać z najnowszych funkcji w wersji punktu, należy [skonfigurować kompilatora wersji języka](../language-reference/configure-language-version.md) i wybierz wersję.</span><span class="sxs-lookup"><span data-stu-id="f67fe-118">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="f67fe-119">Asynchroniczne głównego</span><span class="sxs-lookup"><span data-stu-id="f67fe-119">Async main</span></span>

<span data-ttu-id="f67fe-120">*Async głównego* metoda pozwala na użycie `await` w Twojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="f67fe-120">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="f67fe-121">Wcześniej będzie potrzebny do zapisania:</span><span class="sxs-lookup"><span data-stu-id="f67fe-121">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f67fe-122">Możesz teraz zapisać:</span><span class="sxs-lookup"><span data-stu-id="f67fe-122">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f67fe-123">Jeśli program nie zwraca kod zakończenia, mogą zadeklarować `Main` metodę zwracającą <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="f67fe-123">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f67fe-124">Możesz przeczytać dodatkowe informacje szczegółowe informacje w [async głównego](../programming-guide/main-and-command-args/index.md) w Podręczniku programowania.</span><span class="sxs-lookup"><span data-stu-id="f67fe-124">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f67fe-125">Wyrażenia dosłowne domyślne</span><span class="sxs-lookup"><span data-stu-id="f67fe-125">Default literal expressions</span></span>

<span data-ttu-id="f67fe-126">Wyrażenia dosłowne domyślne są ulepszeniem wyrażenia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f67fe-126">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="f67fe-127">Wyrażenia te zainicjować zmiennej przy użyciu wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f67fe-127">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f67fe-128">Gdzie należy wcześniej zapisać:</span><span class="sxs-lookup"><span data-stu-id="f67fe-128">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f67fe-129">Teraz można pominąć inicjowanie typ po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="f67fe-129">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f67fe-130">Użytkownik może dowiedzieć się więcej o to rozszerzenie w temacie C# przewodnik programowania w języku na [domyślna wartość wyrażenia](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f67fe-130">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="f67fe-131">To rozszerzenie zmieniają się także niektóre reguły analizy [słowo kluczowe default](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="f67fe-131">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="f67fe-132">Nazwy elementów wywnioskowanych spójnej kolekcji</span><span class="sxs-lookup"><span data-stu-id="f67fe-132">Inferred tuple element names</span></span>

<span data-ttu-id="f67fe-133">Ta funkcja jest mała rozszerzenie funkcji krotek wprowadzono w języku C# w wersji 7.0.</span><span class="sxs-lookup"><span data-stu-id="f67fe-133">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="f67fe-134">Wiele razy podczas inicjowania krotka zmiennych po prawej stronie przypisania są takie same jak nazwy, którą chcesz spójnej kolekcji elementów:</span><span class="sxs-lookup"><span data-stu-id="f67fe-134">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="f67fe-135">Nazwy elementów spójnej kolekcji można wywnioskować na podstawie zmiennych używaną do inicjalizacji spójna kolekcja znajdująca się w języku C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="f67fe-135">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f67fe-136">Dowiedz się więcej o tej funkcji w [krotek](../tuples.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f67fe-136">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="f67fe-137">Generowanie odwołania do zestawu</span><span class="sxs-lookup"><span data-stu-id="f67fe-137">Reference assembly generation</span></span>

<span data-ttu-id="f67fe-138">Dostępne są dwie opcje kompilatora nowe, które generują *tylko do odwołania zestawów*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) i [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f67fe-138">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f67fe-139">W połączonych tematach opisano te opcje i zestawy referencyjne bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="f67fe-139">The linked topics explain these options and reference assemblies in more detail.</span></span>
