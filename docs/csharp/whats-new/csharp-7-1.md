---
title: Co nowego w C# 7,1
description: Omówienie nowych funkcji w C# 7,1.
ms.date: 04/09/2019
ms.openlocfilehash: ee68cbf129d02fc58155a603d6a3f63cfb182cd0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105552"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="6aaa6-103">Co nowego w C# 7,1</span><span class="sxs-lookup"><span data-stu-id="6aaa6-103">What's new in C# 7.1</span></span>

<span data-ttu-id="6aaa6-104">C#7,1 to wersja C# pierwszego punktu w punkcie.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="6aaa6-105">Oznacza to zwiększoną erze wydania dla danego języka.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="6aaa6-106">Możesz użyć nowych funkcji szybciej, najlepiej, gdy każda nowa funkcja jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="6aaa6-107">C#7,1 dodaje możliwość skonfigurowania kompilatora w celu dopasowania do określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="6aaa6-108">Dzięki temu można rozdzielić decyzje dotyczące uaktualniania narzędzi z decyzji o uaktualnieniu wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="6aaa6-109">C#7,1 dodaje element konfiguracji [wyboru wersji języka](../language-reference/configure-language-version.md) , trzy nowe funkcje językowe i nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="6aaa6-110">Nowe funkcje języka w tej wersji są następujące:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="6aaa6-111">`async``Main` Metoda</span><span class="sxs-lookup"><span data-stu-id="6aaa6-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="6aaa6-112">Punkt wejścia dla aplikacji może mieć `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="6aaa6-113">`default`wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="6aaa6-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="6aaa6-114">Można użyć domyślnych wyrażeń literałów w wyrażeniach wartości domyślnych, gdy można wywnioskować typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="6aaa6-115">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="6aaa6-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="6aaa6-116">Nazwy elementów krotki można wywnioskować na podstawie inicjalizacji krotki w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="6aaa6-117">Dopasowanie wzorca dla parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="6aaa6-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="6aaa6-118">Wyrażeń dopasowania wzorców można używać w zmiennych, których typem jest parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="6aaa6-119">Na koniec kompilator ma dwie opcje `-refout` i `-refonly` umożliwia wygenerowanie [zestawu odwołań](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="6aaa6-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="6aaa6-120">Aby użyć najnowszych funkcji w wersji próbnej, należy [skonfigurować wersję języka kompilatora](../language-reference/configure-language-version.md) i wybrać wersję.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="6aaa6-121">Pozostała część tego artykułu zawiera omówienie każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="6aaa6-122">Dla każdej funkcji znajdziesz jej uzasadnienie.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="6aaa6-123">Poznasz składnię.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-123">You'll learn the syntax.</span></span> <span data-ttu-id="6aaa6-124">Te funkcje można eksplorować w środowisku za pomocą `dotnet try` narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="6aaa6-125">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="6aaa6-126">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="6aaa6-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="6aaa6-127">Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="6aaa6-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="6aaa6-128">Uruchom `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="6aaa6-129">Asynchroniczny, główny</span><span class="sxs-lookup"><span data-stu-id="6aaa6-129">Async main</span></span>

<span data-ttu-id="6aaa6-130">Metoda *Async Main* umożliwia korzystanie `await` z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="6aaa6-131">Wcześniej należy napisać:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="6aaa6-132">Teraz możesz napisać:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="6aaa6-133">Jeśli program nie zwraca kodu zakończenia, można zadeklarować `Main` metodę, która <xref:System.Threading.Tasks.Task>zwraca:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="6aaa6-134">Więcej informacji na temat szczegółowych informacji można znaleźć w artykule dotyczącym [asynchronicznego](../programming-guide/main-and-command-args/index.md) artykułu w przewodniku programowania.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="6aaa6-135">Domyślne wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="6aaa6-135">Default literal expressions</span></span>

<span data-ttu-id="6aaa6-136">Domyślne wyrażenia literałów to ulepszenie wyrażeń wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="6aaa6-137">Te wyrażenia inicjują zmienną do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="6aaa6-138">Gdzie wcześniej warto napisać:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="6aaa6-139">Możesz teraz pominąć typ po prawej stronie inicjalizacji:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="6aaa6-140">Aby uzyskać więcej informacji, zobacz sekcję [domyślny literał](../language-reference/operators/default.md#default-literal) w artykule [domyślny operator](../language-reference/operators/default.md) .</span><span class="sxs-lookup"><span data-stu-id="6aaa6-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="6aaa6-141">Wywnioskowane nazwy elementów krotki</span><span class="sxs-lookup"><span data-stu-id="6aaa6-141">Inferred tuple element names</span></span>

<span data-ttu-id="6aaa6-142">Ta funkcja to małe rozszerzenie funkcji kroteks wprowadzonej w C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="6aaa6-143">Wiele razy po zainicjowaniu krotki zmienne używane dla prawej strony przypisania są takie same jak nazwy dla elementów krotki:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="6aaa6-144">Nazwy elementów krotki można wywnioskować na podstawie zmiennych użytych do zainicjowania krotki w C# 7,1:</span><span class="sxs-lookup"><span data-stu-id="6aaa6-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="6aaa6-145">Więcej informacji na temat tej funkcji można znaleźć w [](../tuples.md) artykule krotkis.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="6aaa6-146">Dopasowanie wzorca dla parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="6aaa6-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="6aaa6-147">Począwszy od C# 7,1, wyrażenie wzorca dla `is` i `switch` wzorzec typu mogą mieć typ parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="6aaa6-148">Może to być najbardziej przydatne podczas sprawdzania typów, które mogą być `struct` albo `class` typu, i chcesz uniknąć pakowania.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="6aaa6-149">Generowanie zestawu odwołań</span><span class="sxs-lookup"><span data-stu-id="6aaa6-149">Reference assembly generation</span></span>

<span data-ttu-id="6aaa6-150">Istnieją dwie nowe opcje kompilatora, które generują *zestawy tylko do odwołania*: [-opcji refout](../language-reference/compiler-options/refout-compiler-option.md) i [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="6aaa6-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="6aaa6-151">Połączone artykuły wyjaśniają te opcje i zestawy referencyjne bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="6aaa6-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
