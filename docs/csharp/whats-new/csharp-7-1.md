---
title: Co nowego C# 7.1
description: Omówienie nowych funkcji w C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: a95111b6f217a2ca5c520c2d4d70efa0e23742f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347614"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="ba0ad-103">Co nowego C# 7.1</span><span class="sxs-lookup"><span data-stu-id="ba0ad-103">What's new in C# 7.1</span></span>

<span data-ttu-id="ba0ad-104">C#7.1 to pierwsze wydanie punkt do C# języka.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="ba0ad-105">Oznacza cykl zwiększone wersji języka.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="ba0ad-106">Umożliwia nowe funkcje wcześniej, najlepiej w przypadku każdej nowej funkcji jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="ba0ad-107">C#7.1 dodaje możliwość konfigurowania kompilatora odpowiadający określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="ba0ad-108">Która pozwala oddzielić decyzja do uaktualnienia narzędzi od decyzji o uaktualnienie wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="ba0ad-109">C#7.1 dodaje [wybór wersji języka](../language-reference/configure-language-version.md) element konfiguracji, trzy nowe funkcje języka i nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="ba0ad-110">Dostępne są następujące nowe funkcje języka w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="ba0ad-111">`async` `Main` — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba0ad-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="ba0ad-112">Punkt wejścia dla aplikacji może mieć `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="ba0ad-113">`default` wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="ba0ad-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="ba0ad-114">Można używać wyrażeń literał domyślny w wyrażeniach wartości domyślne, gdy można wywnioskować typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="ba0ad-115">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="ba0ad-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="ba0ad-116">Od inicjowania krotki w wielu przypadkach można wywnioskować nazwami elementów krotki.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="ba0ad-117">Dopasowania do wzorca w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="ba0ad-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="ba0ad-118">Wyrażenia dopasowania wzorca można użyć zmiennych, którego typem jest parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="ba0ad-119">Na koniec, kompilator zawiera dwie pozycje `-refout` i `-refonly` tej kontrolki [odwoływać się do generowania zestawu](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="ba0ad-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="ba0ad-120">Korzystanie z najnowszych funkcji w wersji punktu należy [skonfigurować wersję językową kompilatora](../language-reference/configure-language-version.md) i wybierz wersję.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="ba0ad-121">W dalszej części tego artykułu zawiera omówienie każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="ba0ad-122">Dowiesz się jej uzasadnienie, dla każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="ba0ad-123">Dowiesz się, aby składnia.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-123">You'll learn the syntax.</span></span> <span data-ttu-id="ba0ad-124">Możesz zapoznać się z tych funkcji w środowisku przy użyciu `dotnet try` narzędzie globalne:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="ba0ad-125">Zainstaluj [spróbuj dotnet](https://github.com/dotnet/try/blob/master/README.md#setup) narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="ba0ad-126">Klonuj [dotnet/try-samples](https://github.com/dotnet/try-samples) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="ba0ad-127">Ustaw bieżący katalog *csharp7* podkatalog *try-samples* repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="ba0ad-128">Uruchom `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="ba0ad-129">Asynchroniczna funkcja main</span><span class="sxs-lookup"><span data-stu-id="ba0ad-129">Async main</span></span>

<span data-ttu-id="ba0ad-130">*Asynchroniczna funkcja main* metoda umożliwia użycie `await` w swojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="ba0ad-131">Wcześniej należy napisać:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="ba0ad-132">Teraz można napisać:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="ba0ad-133">Jeśli program nie zwraca kod zakończenia, możesz zadeklarować `Main` metodę, która zwraca <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="ba0ad-134">Możesz dowiedzieć się więcej o szczegółach w [asynchroniczna funkcja main](../programming-guide/main-and-command-args/index.md) artykułu w Podręczniku programowania.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="ba0ad-135">Wyrażenia literału domyślnego</span><span class="sxs-lookup"><span data-stu-id="ba0ad-135">Default literal expressions</span></span>

<span data-ttu-id="ba0ad-136">Wyrażenia literału domyślnego stanowią rozszerzenie wyrażenia wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="ba0ad-137">Te wyrażenia Zainicjuj zmienną do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="ba0ad-138">Gdzie należy wcześniej napisać:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="ba0ad-139">Można teraz pominąć typ po prawej stronie inicjowania:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="ba0ad-140">Dowiedz się więcej na temat to rozszerzenie w C# przewodnik programowania w artykule dotyczącym [domyślna wartość wyrażenia](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ba0ad-140">You can learn more about this enhancement in the C# Programming Guide article on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="ba0ad-141">To ulepszenie zmienia się również niektóre reguły analizy składni dla [default — słowo kluczowe](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="ba0ad-141">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="ba0ad-142">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="ba0ad-142">Inferred tuple element names</span></span>

<span data-ttu-id="ba0ad-143">Ta funkcja jest mały ulepszenie funkcji krotek, wprowadzona w C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-143">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="ba0ad-144">Wiele razy podczas inicjowania spójną kolekcję zmiennych po prawej stronie przypisania są takie same jak nazwy, które Twoim zdaniem elementów krotki:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-144">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="ba0ad-145">Nazwy elementów krotki można wywnioskować na podstawie zmiennych, używane do zainicjowania spójna kolekcja znajdująca się w C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="ba0ad-145">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="ba0ad-146">Dowiedz się więcej na temat tej funkcji w [krotek](../tuples.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-146">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="ba0ad-147">Dopasowania do wzorca w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="ba0ad-147">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="ba0ad-148">Począwszy od C# 7.1, wyrażenie nie zawiera wzorca `is` i `switch` typu wzorzec może być typem parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-148">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="ba0ad-149">Może to być najbardziej przydatne, gdy sprawdzanie typów, które mogą być albo `struct` lub `class` typów i chcesz uniknąć pakowania.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-149">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="ba0ad-150">Generowanie zestawu odwołania</span><span class="sxs-lookup"><span data-stu-id="ba0ad-150">Reference assembly generation</span></span>

<span data-ttu-id="ba0ad-151">Istnieją dwie nowe opcje kompilatora, które generują *tylko do odwołania zestawów*: [- opcji refout](../language-reference/compiler-options/refout-compiler-option.md) i [jest opcja refonly -](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ba0ad-151">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="ba0ad-152">Połączonych artykułów opisano te opcje i zestawy odwołań bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="ba0ad-152">The linked articles explain these options and reference assemblies in more detail.</span></span>
