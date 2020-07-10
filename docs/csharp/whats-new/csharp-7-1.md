---
title: Co nowego w języku C# 7.1
description: Omówienie nowych funkcji w języku C# 7,1.
ms.date: 04/09/2019
ms.openlocfilehash: fe6e49eb01e24a27bc7970900c05150378ab194a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174773"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="996e5-103">Co nowego w języku C# 7.1</span><span class="sxs-lookup"><span data-stu-id="996e5-103">What's new in C# 7.1</span></span>

<span data-ttu-id="996e5-104">C# 7,1 to wersja pierwszego punktu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="996e5-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="996e5-105">Oznacza to zwiększoną erze wydania dla danego języka.</span><span class="sxs-lookup"><span data-stu-id="996e5-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="996e5-106">Możesz użyć nowych funkcji szybciej, najlepiej, gdy każda nowa funkcja jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="996e5-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="996e5-107">W języku C# 7,1 Dodano możliwość skonfigurowania kompilatora w celu dopasowania do określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="996e5-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="996e5-108">Dzięki temu można rozdzielić decyzje dotyczące uaktualniania narzędzi z decyzji o uaktualnieniu wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="996e5-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="996e5-109">W języku C# 7,1 dodano element konfiguracji [wyboru wersji języka](../language-reference/configure-language-version.md) , trzy nowe funkcje językowe oraz nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="996e5-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="996e5-110">Nowe funkcje języka w tej wersji są następujące:</span><span class="sxs-lookup"><span data-stu-id="996e5-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="996e5-111">`async``Main`Metoda</span><span class="sxs-lookup"><span data-stu-id="996e5-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="996e5-112">Punkt wejścia dla aplikacji może mieć `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="996e5-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="996e5-113">`default`wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="996e5-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="996e5-114">Można użyć domyślnych wyrażeń literałów w wyrażeniach wartości domyślnych, gdy można wywnioskować typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="996e5-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="996e5-115">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="996e5-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="996e5-116">Nazwy elementów krotki można wywnioskować na podstawie inicjalizacji krotki w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="996e5-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="996e5-117">Dopasowanie wzorca dla parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="996e5-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="996e5-118">Wyrażeń dopasowania wzorców można używać w zmiennych, których typem jest parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="996e5-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="996e5-119">Na koniec kompilator ma dwie opcje `-refout` i `-refonly` umożliwia [wygenerowanie zestawu odwołań](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="996e5-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="996e5-120">Aby użyć najnowszych funkcji w wersji próbnej, należy [skonfigurować wersję języka kompilatora](../language-reference/configure-language-version.md) i wybrać wersję.</span><span class="sxs-lookup"><span data-stu-id="996e5-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="996e5-121">Pozostała część tego artykułu zawiera omówienie każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="996e5-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="996e5-122">Dla każdej funkcji znajdziesz jej uzasadnienie.</span><span class="sxs-lookup"><span data-stu-id="996e5-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="996e5-123">Poznasz składnię.</span><span class="sxs-lookup"><span data-stu-id="996e5-123">You'll learn the syntax.</span></span> <span data-ttu-id="996e5-124">Te funkcje można eksplorować w środowisku za pomocą `dotnet try` Narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="996e5-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="996e5-125">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="996e5-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="996e5-126">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="996e5-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="996e5-127">Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="996e5-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="996e5-128">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="996e5-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="996e5-129">Asynchroniczny, główny</span><span class="sxs-lookup"><span data-stu-id="996e5-129">Async main</span></span>

<span data-ttu-id="996e5-130">Metoda *Async Main* umożliwia korzystanie `await` z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="996e5-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="996e5-131">Wcześniej należy napisać:</span><span class="sxs-lookup"><span data-stu-id="996e5-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="996e5-132">Teraz możesz napisać:</span><span class="sxs-lookup"><span data-stu-id="996e5-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="996e5-133">Jeśli program nie zwraca kodu zakończenia, można zadeklarować `Main` metodę, która zwraca <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="996e5-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="996e5-134">Więcej informacji na temat szczegółowych informacji można znaleźć w artykule dotyczącym [asynchronicznego](../programming-guide/main-and-command-args/index.md) artykułu w przewodniku programowania.</span><span class="sxs-lookup"><span data-stu-id="996e5-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="996e5-135">Domyślne wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="996e5-135">Default literal expressions</span></span>

<span data-ttu-id="996e5-136">Domyślne wyrażenia literałów to ulepszenie wyrażeń wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="996e5-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="996e5-137">Te wyrażenia inicjują zmienną do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="996e5-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="996e5-138">Gdzie wcześniej warto napisać:</span><span class="sxs-lookup"><span data-stu-id="996e5-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="996e5-139">Możesz teraz pominąć typ po prawej stronie inicjalizacji:</span><span class="sxs-lookup"><span data-stu-id="996e5-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="996e5-140">Aby uzyskać więcej informacji, zobacz sekcję [domyślny literał](../language-reference/operators/default.md#default-literal) w artykule [domyślny operator](../language-reference/operators/default.md) .</span><span class="sxs-lookup"><span data-stu-id="996e5-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="996e5-141">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="996e5-141">Inferred tuple element names</span></span>

<span data-ttu-id="996e5-142">Ta funkcja to małe rozszerzenie funkcji kroteks wprowadzonej w języku C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="996e5-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="996e5-143">Wiele razy po zainicjowaniu krotki zmienne używane dla prawej strony przypisania są takie same jak nazwy dla elementów krotki:</span><span class="sxs-lookup"><span data-stu-id="996e5-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="996e5-144">Nazwy elementów krotki można wywnioskować na podstawie zmiennych używanych do inicjowania krotki w języku C# 7,1:</span><span class="sxs-lookup"><span data-stu-id="996e5-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="996e5-145">Więcej informacji na temat tej funkcji można znaleźć w artykule [typy krotek](../language-reference/builtin-types/value-tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="996e5-145">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="996e5-146">Dopasowanie wzorca dla parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="996e5-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="996e5-147">Począwszy od języka C# 7,1 wyrażenie wzorca dla `is` i `switch` wzorzec typu może mieć typ parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="996e5-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="996e5-148">Może to być najbardziej przydatne podczas sprawdzania typów, które mogą być `struct` albo `class` typu, i chcesz uniknąć pakowania.</span><span class="sxs-lookup"><span data-stu-id="996e5-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="996e5-149">Generowanie zestawu odwołań</span><span class="sxs-lookup"><span data-stu-id="996e5-149">Reference assembly generation</span></span>

<span data-ttu-id="996e5-150">Istnieją dwie nowe opcje kompilatora, które generują *zestawy tylko do odwołania*: [-opcji refout](../language-reference/compiler-options/refout-compiler-option.md) i [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="996e5-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="996e5-151">Połączone artykuły wyjaśniają te opcje i zestawy referencyjne bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="996e5-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
