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
# <a name="whats-new-in-c-71"></a><span data-ttu-id="72591-103">Co nowego w języku C# 7.1</span><span class="sxs-lookup"><span data-stu-id="72591-103">What's new in C# 7.1</span></span>

<span data-ttu-id="72591-104">C# 7.1 jest pierwszym wydaniem punktowym do języka C#.</span><span class="sxs-lookup"><span data-stu-id="72591-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="72591-105">Oznacza to zwiększoną kadencję uwalniania dla języka.</span><span class="sxs-lookup"><span data-stu-id="72591-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="72591-106">Możesz korzystać z nowych funkcji wcześniej, najlepiej, gdy każda nowa funkcja jest gotowa.</span><span class="sxs-lookup"><span data-stu-id="72591-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="72591-107">C# 7.1 dodaje możliwość skonfigurowania kompilatora do określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="72591-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="72591-108">Dzięki temu można oddzielić decyzję o uaktualnieniu narzędzi od decyzji o uaktualnieniu wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="72591-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="72591-109">C# 7.1 dodaje element konfiguracji [wyboru wersji językowej,](../language-reference/configure-language-version.md) trzy nowe funkcje języka i nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="72591-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="72591-110">Nowe funkcje języka w tej wersji to:</span><span class="sxs-lookup"><span data-stu-id="72591-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="72591-111">`async``Main` metoda</span><span class="sxs-lookup"><span data-stu-id="72591-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="72591-112">Punkt wejścia dla aplikacji może `async` mieć modyfikator.</span><span class="sxs-lookup"><span data-stu-id="72591-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="72591-113">`default`wyrażenia dosłowne</span><span class="sxs-lookup"><span data-stu-id="72591-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="72591-114">Można użyć domyślnych wyrażeń literału w domyślnych wyrażeniach wartości, gdy można wywnioskować typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="72591-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="72591-115">Nazwy wywnioskowanych elementów krotki</span><span class="sxs-lookup"><span data-stu-id="72591-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="72591-116">Nazwy elementów krotki można wywnioskować z inicjowania krotki w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="72591-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="72591-117">Dopasowywanie wzorców dla parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="72591-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="72591-118">Wyrażenia dopasowania wzorca można używać w zmiennych, których typ jest parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="72591-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="72591-119">Na koniec kompilator `-refout` `-refonly` ma dwie opcje i że kontrola [referencyjnego generowania zestawu](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="72591-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="72591-120">Aby korzystać z najnowszych funkcji w wersji punktowej, należy [skonfigurować wersję języka kompilatora](../language-reference/configure-language-version.md) i wybrać wersję.</span><span class="sxs-lookup"><span data-stu-id="72591-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="72591-121">W dalszej części tego artykułu przedstawiono omówienie każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="72591-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="72591-122">Dla każdej funkcji dowiesz się, co za nią kryje.</span><span class="sxs-lookup"><span data-stu-id="72591-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="72591-123">Dowiesz się składni.</span><span class="sxs-lookup"><span data-stu-id="72591-123">You'll learn the syntax.</span></span> <span data-ttu-id="72591-124">Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`</span><span class="sxs-lookup"><span data-stu-id="72591-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="72591-125">Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="72591-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="72591-126">Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="72591-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="72591-127">Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *próbek.*</span><span class="sxs-lookup"><span data-stu-id="72591-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="72591-128">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="72591-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="72591-129">Asynchroniczne główne</span><span class="sxs-lookup"><span data-stu-id="72591-129">Async main</span></span>

<span data-ttu-id="72591-130">*Asynchroniczą główną* `await` metodą `Main` umożliwia użycie w metodzie.</span><span class="sxs-lookup"><span data-stu-id="72591-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="72591-131">Wcześniej trzeba było napisać:</span><span class="sxs-lookup"><span data-stu-id="72591-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="72591-132">Możesz teraz napisać:</span><span class="sxs-lookup"><span data-stu-id="72591-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="72591-133">Jeśli program nie zwraca kodu zakończenia, można `Main` zadeklarować metodę <xref:System.Threading.Tasks.Task>zwracającą:</span><span class="sxs-lookup"><span data-stu-id="72591-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="72591-134">Więcej informacji na temat szczegółów w głównym artykule [asynchronicznego](../programming-guide/main-and-command-args/index.md) można znaleźć w przewodniku po programowaniu.</span><span class="sxs-lookup"><span data-stu-id="72591-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="72591-135">Domyślne wyrażenia literału</span><span class="sxs-lookup"><span data-stu-id="72591-135">Default literal expressions</span></span>

<span data-ttu-id="72591-136">Domyślne wyrażenia literału są rozszerzeniem domyślnych wyrażeń wartości.</span><span class="sxs-lookup"><span data-stu-id="72591-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="72591-137">Wyrażenia te inicjują zmienną do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="72591-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="72591-138">Gdzie wcześniej pisałeś:</span><span class="sxs-lookup"><span data-stu-id="72591-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="72591-139">Teraz można pominąć typ po prawej stronie inicjowania:</span><span class="sxs-lookup"><span data-stu-id="72591-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="72591-140">Aby uzyskać więcej informacji, zobacz domyślną sekcję [literału](../language-reference/operators/default.md#default-literal) [w artykule operatora domyślnego.](../language-reference/operators/default.md)</span><span class="sxs-lookup"><span data-stu-id="72591-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="72591-141">Nazwy wywnioskowanych elementów krotki</span><span class="sxs-lookup"><span data-stu-id="72591-141">Inferred tuple element names</span></span>

<span data-ttu-id="72591-142">Ta funkcja jest małym ulepszeniem funkcji krotek wprowadzonych w języku C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="72591-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="72591-143">Wiele razy podczas inicjowania krotki zmienne używane po prawej stronie przypisania są takie same jak nazwy, które chcesz dla elementów krotki:</span><span class="sxs-lookup"><span data-stu-id="72591-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="72591-144">Nazwy elementów krotki można wywnioskować ze zmiennych używanych do inicjowania krotki w języku C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="72591-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="72591-145">Więcej informacji na temat tej funkcji można znaleźć w artykule [Krotek.](../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="72591-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="72591-146">Dopasowywanie wzorców dla parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="72591-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="72591-147">Począwszy od Języka C# 7.1 wyrażenie wzorca dla `is` i wzorzec `switch` typu może mieć typ parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="72591-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="72591-148">Może to być najbardziej przydatne podczas `struct` sprawdzania `class` typów, które mogą być lub typy i chcesz uniknąć boksu.</span><span class="sxs-lookup"><span data-stu-id="72591-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="72591-149">Generowanie zespołu referencyjnego</span><span class="sxs-lookup"><span data-stu-id="72591-149">Reference assembly generation</span></span>

<span data-ttu-id="72591-150">Istnieją dwie nowe opcje kompilatora, które generują *zestawy tylko do odwołania:* [-refout](../language-reference/compiler-options/refout-compiler-option.md) i [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="72591-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="72591-151">Połączone artykuły wyjaśniają te opcje i zestawy odwołań bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="72591-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
