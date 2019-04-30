---
title: Co nowego C# 7.1
description: Omówienie nowych funkcji w C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675562"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="e0574-103">Co nowego C# 7.1</span><span class="sxs-lookup"><span data-stu-id="e0574-103">What's new in C# 7.1</span></span>

<span data-ttu-id="e0574-104">C#7.1 to pierwsze wydanie punkt do C# języka.</span><span class="sxs-lookup"><span data-stu-id="e0574-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="e0574-105">Oznacza cykl zwiększone wersji języka.</span><span class="sxs-lookup"><span data-stu-id="e0574-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="e0574-106">Umożliwia nowe funkcje wcześniej, najlepiej w przypadku każdej nowej funkcji jest gotowy.</span><span class="sxs-lookup"><span data-stu-id="e0574-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="e0574-107">C#7.1 dodaje możliwość konfigurowania kompilatora odpowiadający określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="e0574-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="e0574-108">Która pozwala oddzielić decyzja do uaktualnienia narzędzi od decyzji o uaktualnienie wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="e0574-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="e0574-109">C#7.1 dodaje [wybór wersji języka](../language-reference/configure-language-version.md) element konfiguracji, trzy nowe funkcje języka i nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e0574-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="e0574-110">Dostępne są następujące nowe funkcje języka w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="e0574-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="e0574-111">`async` `Main` — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0574-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="e0574-112">Punkt wejścia dla aplikacji może mieć `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="e0574-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="e0574-113">`default` wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="e0574-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="e0574-114">Można używać wyrażeń literał domyślny w wyrażeniach wartości domyślne, gdy można wywnioskować typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e0574-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="e0574-115">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="e0574-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="e0574-116">Od inicjowania krotki w wielu przypadkach można wywnioskować nazwami elementów krotki.</span><span class="sxs-lookup"><span data-stu-id="e0574-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="e0574-117">Dopasowania do wzorca w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="e0574-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="e0574-118">Wyrażenia dopasowania wzorca można użyć zmiennych, którego typem jest parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="e0574-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="e0574-119">Na koniec, kompilator zawiera dwie pozycje `/refout` i `/refonly` tej kontrolki [odwoływać się do generowania zestawu](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="e0574-119">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="e0574-120">Korzystanie z najnowszych funkcji w wersji punktu należy [skonfigurować wersję językową kompilatora](../language-reference/configure-language-version.md) i wybierz wersję.</span><span class="sxs-lookup"><span data-stu-id="e0574-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="e0574-121">Asynchroniczna funkcja main</span><span class="sxs-lookup"><span data-stu-id="e0574-121">Async main</span></span>

<span data-ttu-id="e0574-122">*Asynchroniczna funkcja main* metoda umożliwia użycie `await` w swojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="e0574-122">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="e0574-123">Wcześniej należy napisać:</span><span class="sxs-lookup"><span data-stu-id="e0574-123">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="e0574-124">Teraz można napisać:</span><span class="sxs-lookup"><span data-stu-id="e0574-124">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="e0574-125">Jeśli program nie zwraca kod zakończenia, możesz zadeklarować `Main` metodę, która zwraca <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="e0574-125">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="e0574-126">Możesz dowiedzieć się więcej o szczegółach w [asynchroniczna funkcja main](../programming-guide/main-and-command-args/index.md) artykułu w Podręczniku programowania.</span><span class="sxs-lookup"><span data-stu-id="e0574-126">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="e0574-127">Wyrażenia literału domyślnego</span><span class="sxs-lookup"><span data-stu-id="e0574-127">Default literal expressions</span></span>

<span data-ttu-id="e0574-128">Wyrażenia literału domyślnego stanowią rozszerzenie wyrażenia wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="e0574-128">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="e0574-129">Te wyrażenia Zainicjuj zmienną do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="e0574-129">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="e0574-130">Gdzie należy wcześniej napisać:</span><span class="sxs-lookup"><span data-stu-id="e0574-130">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="e0574-131">Można teraz pominąć typ po prawej stronie inicjowania:</span><span class="sxs-lookup"><span data-stu-id="e0574-131">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="e0574-132">Dowiedz się więcej na temat to rozszerzenie w C# przewodnik programowania w artykule dotyczącym [domyślna wartość wyrażenia](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e0574-132">You can learn more about this enhancement in the C# Programming Guide article on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="e0574-133">To ulepszenie zmienia się również niektóre reguły analizy składni dla [default — słowo kluczowe](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="e0574-133">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="e0574-134">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="e0574-134">Inferred tuple element names</span></span>

<span data-ttu-id="e0574-135">Ta funkcja jest mały ulepszenie funkcji krotek, wprowadzona w C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="e0574-135">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="e0574-136">Wiele razy podczas inicjowania spójną kolekcję zmiennych po prawej stronie przypisania są takie same jak nazwy, które Twoim zdaniem elementów krotki:</span><span class="sxs-lookup"><span data-stu-id="e0574-136">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="e0574-137">Nazwy elementów krotki można wywnioskować na podstawie zmiennych, używane do zainicjowania spójna kolekcja znajdująca się w C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="e0574-137">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="e0574-138">Dowiedz się więcej na temat tej funkcji w [krotek](../tuples.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="e0574-138">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="e0574-139">Dopasowania do wzorca w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="e0574-139">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="e0574-140">Począwszy od C# 7.1, wyrażenie nie zawiera wzorca `is` i `switch` typu wzorzec może być typem parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="e0574-140">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="e0574-141">Może to być najbardziej przydatne, gdy sprawdzanie typów, które mogą być albo `struct` lub `class` typów i chcesz uniknąć pakowania.</span><span class="sxs-lookup"><span data-stu-id="e0574-141">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="e0574-142">Generowanie zestawu odwołania</span><span class="sxs-lookup"><span data-stu-id="e0574-142">Reference assembly generation</span></span>

<span data-ttu-id="e0574-143">Istnieją dwie nowe opcje kompilatora, które generują *tylko do odwołania zestawów*: [jest opcja](../language-reference/compiler-options/refout-compiler-option.md) i [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e0574-143">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="e0574-144">Połączonych artykułów opisano te opcje i zestawy odwołań bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="e0574-144">The linked articles explain these options and reference assemblies in more detail.</span></span>
