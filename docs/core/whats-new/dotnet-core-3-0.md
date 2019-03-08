---
title: What's new in .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 89264098ed17b398c83bc2dcddd98d9d8fc958f7
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679739"
---
# <a name="whats-new-in-net-core-30-preview-2"></a><span data-ttu-id="54fce-103">What's new in .NET Core 3.0 (wersja zapoznawcza 2)</span><span class="sxs-lookup"><span data-stu-id="54fce-103">What's new in .NET Core 3.0 (Preview 2)</span></span>

<span data-ttu-id="54fce-104">W tym artykule opisano nowości w programie .NET Core 3.0 (wersja zapoznawcza 2).</span><span class="sxs-lookup"><span data-stu-id="54fce-104">This article describes what is new in .NET Core 3.0 (preview 2).</span></span> <span data-ttu-id="54fce-105">Jedną z największych ulepszenia to obsługa aplikacji klasycznych Windows (tylko Windows).</span><span class="sxs-lookup"><span data-stu-id="54fce-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="54fce-106">Przy użyciu zestawu SDK programu .NET Core 3.0 składnika o nazwie Windows Desktop, można portu usługi Windows Forms i aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="54fce-106">By utilizing a .NET Core 3.0 SDK component called Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="54fce-107">Było jasne, składnik Windows Desktop jest tylko obsługiwana i uwzględniane na Windows.</span><span class="sxs-lookup"><span data-stu-id="54fce-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="54fce-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu Windows](#windows-desktop) poniżej.</span><span class="sxs-lookup"><span data-stu-id="54fce-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="54fce-109">.NET core 3.0 dodaje obsługę C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="54fce-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="54fce-110">[Pobierz i rozpoczynanie pracy z usługą .NET Core 3.0 w wersji zapoznawczej 2](https://aka.ms/netcore3download) teraz na Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="54fce-110">[Download and get started with .NET Core 3.0 Preview 2](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="54fce-111">Można wyświetlić szczegółowe informacje o wersji w [informacje o wersji platformy .NET Core 3.0 w wersji zapoznawczej 2](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="54fce-111">You can see complete details of the release in the [.NET Core 3.0 Preview 2 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="54fce-112">Aby uzyskać więcej informacji na temat co wydanej z każdą wersją zobacz następujące komunikaty:</span><span class="sxs-lookup"><span data-stu-id="54fce-112">For more information about what was released with each version, see the following announcements:</span></span>

- [<span data-ttu-id="54fce-113">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 1</span><span class="sxs-lookup"><span data-stu-id="54fce-113">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [<span data-ttu-id="54fce-114">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 2</span><span class="sxs-lookup"><span data-stu-id="54fce-114">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)

## <a name="c-8"></a><span data-ttu-id="54fce-115">C# 8</span><span class="sxs-lookup"><span data-stu-id="54fce-115">C# 8</span></span>

<span data-ttu-id="54fce-116">Obsługuje platformy .NET core 3.0 C# 8, a począwszy od platformy .NET Core 3.0 w wersji zapoznawczej 2 obsługuje te nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="54fce-116">.NET Core 3.0 supports C# 8, and as of .NET Core 3.0 Preview 2, supports these new features.</span></span> <span data-ttu-id="54fce-117">Aby uzyskać więcej informacji na temat C# funkcje 8.0, zobacz następujące wpisy na blogu:</span><span class="sxs-lookup"><span data-stu-id="54fce-117">For more information about C# 8.0 features, see the following blog posts:</span></span>

- [<span data-ttu-id="54fce-118">Osiągnij więcej ze wzorców w C# 8.0</span><span class="sxs-lookup"><span data-stu-id="54fce-118">Do more with patterns in C# 8.0</span></span>](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)
- [<span data-ttu-id="54fce-119">Wykonaj C# 8.0 dla pokrętła</span><span class="sxs-lookup"><span data-stu-id="54fce-119">Take C# 8.0 for a spin</span></span>](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/)
- [<span data-ttu-id="54fce-120">Building C# 8.0</span><span class="sxs-lookup"><span data-stu-id="54fce-120">Building C# 8.0</span></span>](https://devblogs.microsoft.com/dotnet/building-c-8-0/)


### <a name="ranges-and-indices"></a><span data-ttu-id="54fce-121">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="54fce-121">Ranges and indices</span></span>

<span data-ttu-id="54fce-122">Nowy `Index` typ może być używany do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="54fce-122">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="54fce-123">Można utworzyć jeden z `int` , jest liczona od początku lub z prefiksem `^` — operator (C#), jest liczona od końca:</span><span class="sxs-lookup"><span data-stu-id="54fce-123">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="54fce-124">Istnieje również `Range` typ, który składa się z dwóch `Index` wartości, jeden dla początkowego i jeden dla elementu end i mogą być zapisywane z `x..y` zakres wyrażenia (C#).</span><span class="sxs-lookup"><span data-stu-id="54fce-124">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="54fce-125">Następnie można zaindeksować z `Range` w celu tworzenia wycinka:</span><span class="sxs-lookup"><span data-stu-id="54fce-125">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a><span data-ttu-id="54fce-126">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="54fce-126">Async streams</span></span>

<span data-ttu-id="54fce-127">`IAsyncEnumerable<T>` Typu jest nowa wersja asynchroniczne `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="54fce-127">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="54fce-128">Język umożliwia `await foreach` za pośrednictwem `IAsyncEnumerable<T>` używanie ich elementy i używać `yield return` do ich do produkcji elementów.</span><span class="sxs-lookup"><span data-stu-id="54fce-128">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="54fce-129">Poniższy przykład ilustruje środowiska produkcyjnego i zużycia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="54fce-129">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="54fce-130">`foreach` Instrukcja jest asynchroniczne, a sam używa `yield return` do produkcji strumienia asynchronicznego dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="54fce-130">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="54fce-131">Ten wzorzec (przy użyciu `yield return`) to zalecany model do produkcji strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="54fce-131">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="54fce-132">Oprócz możliwości `await foreach`, można również utworzyć async Iteratory, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator` można zarówno `await` i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="54fce-132">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="54fce-133">W przypadku obiektów, które muszą zostać zlikwidowany, można użyć `IAsyncDisposable`, który implementuje różnych typów BCL, takich jak `Stream` i `Timer`.</span><span class="sxs-lookup"><span data-stu-id="54fce-133">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

>[!NOTE]
><span data-ttu-id="54fce-134">Potrzebujesz .NET Core 3.0 w wersji zapoznawczej 2, aby użyć strumieni asynchronicznych, jeśli chcesz tworzyć aplikacje za pomocą programu Visual Studio 2019 r w wersji zapoznawczej 2 lub jego najnowszej wersji zapoznawczej [ C# rozszerzenia programu Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span><span class="sxs-lookup"><span data-stu-id="54fce-134">You need .NET Core 3.0 Preview 2 to use async streams if you want to develop with either Visual Studio 2019 Preview 2 or the latest preview of the [C# extension for Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span></span> <span data-ttu-id="54fce-135">Jeśli używasz platformy .NET Core 3.0 w wersji zapoznawczej 2 w wierszu polecenia, następnie wszystko, co będzie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="54fce-135">If you are using .NET Core 3.0 Preview 2 at the command line, then everything will work as expected.</span></span>

### <a name="using-declarations"></a><span data-ttu-id="54fce-136">Za pomocą deklaracji</span><span class="sxs-lookup"><span data-stu-id="54fce-136">Using Declarations</span></span>

<span data-ttu-id="54fce-137">*Za pomocą deklaracji* to nowy sposób, aby upewnić się, obiekt jest prawidłowo usunięte.</span><span class="sxs-lookup"><span data-stu-id="54fce-137">*Using declarations* are a new way to ensure your object is properly disposed.</span></span> <span data-ttu-id="54fce-138">A *użycie — deklaracja* utrzymuje aktywność obiekt jest nadal w zakresie.</span><span class="sxs-lookup"><span data-stu-id="54fce-138">A *using declaration* keeps the object alive while it is still in scope.</span></span> <span data-ttu-id="54fce-139">Gdy obiekt staje się poza zakresem, jest automatycznie usuwany.</span><span class="sxs-lookup"><span data-stu-id="54fce-139">Once the object becomes out of scope, it is automatically disposed.</span></span> <span data-ttu-id="54fce-140">Spowoduje to zmniejszenie zagnieżdżonych *za pomocą instrukcji* i sprawić, że kod jest bardziej przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="54fce-140">This will reduce nested *using statements* and make your code cleaner.</span></span>

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a><span data-ttu-id="54fce-141">Wyrażenia Switch</span><span class="sxs-lookup"><span data-stu-id="54fce-141">Switch Expressions</span></span>

<span data-ttu-id="54fce-142">*Przełącz wyrażenia* są bardziej przejrzysty sposób zapobiegania zrobić *switch, instrukcja* , ale ponieważ jest to wyrażenie zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="54fce-142">*Switch expressions* are a cleaner way of doing a *switch statement* but, since it's an expression, returns a value.</span></span> <span data-ttu-id="54fce-143">*Przełącz wyrażenia* także w pełni zintegrowane z dopasowywania do wzorca, a następnie użyj wzorca odrzucania `_`, do reprezentowania `default` wartość.</span><span class="sxs-lookup"><span data-stu-id="54fce-143">*Switch expressions* are also fully integrated with pattern matching, and use the discard pattern, `_`, to represent the `default` value.</span></span>

<span data-ttu-id="54fce-144">Można wyświetlić składnię *Przełącz wyrażenia* w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="54fce-144">You can see the syntax for *switch expressions* in the following example:</span></span>

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

<span data-ttu-id="54fce-145">Istnieją dwa wzorce podstawą w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="54fce-145">There are two patterns at play in this example.</span></span> <span data-ttu-id="54fce-146">`o` najpierw jest zgodna z `Point` *wpisz wzór* i następnie *wzorzec właściwość* wewnątrz *{nawiasów klamrowych}*.</span><span class="sxs-lookup"><span data-stu-id="54fce-146">`o` first matches with the `Point` *type pattern* and then with the *property pattern* inside the *{curly braces}*.</span></span> <span data-ttu-id="54fce-147">`_` Opisuje `discard pattern`, która jest taka sama jak `default` dla *instrukcje switch*.</span><span class="sxs-lookup"><span data-stu-id="54fce-147">The `_` describes the `discard pattern`, which is the same as `default` for *switch statements*.</span></span>

<span data-ttu-id="54fce-148">Wzorce umożliwiają pisanie kod deklaratywny, która przechwytuje zgodne z zamiarami użytkownika zamiast procedurach kod, który implementuje testy dla niego.</span><span class="sxs-lookup"><span data-stu-id="54fce-148">Patterns enable you to write declarative code that captures your intent instead of procedural code that implements tests for it.</span></span> <span data-ttu-id="54fce-149">Kompilator staje się odpowiedzialnych za wykonanie zadań żmudnych kod proceduralny i gwarantuje zawsze wykonuj poprawnie.</span><span class="sxs-lookup"><span data-stu-id="54fce-149">The compiler becomes responsible for implementing that boring procedural code and is guaranteed to always do it correctly.</span></span>

<span data-ttu-id="54fce-150">Nadal będą przypadki gdzie *instrukcje switch* będzie lepszym rozwiązaniem niż *Przełącz wyrażenia* i wzorce mogą być używane z obu stylów składni.</span><span class="sxs-lookup"><span data-stu-id="54fce-150">There will still be cases where *switch statements* will be a better choice than *switch expressions* and patterns can be used with both syntax styles.</span></span>

<span data-ttu-id="54fce-151">Aby uzyskać więcej informacji, zobacz [więcej możliwości dzięki wzorce w C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/).</span><span class="sxs-lookup"><span data-stu-id="54fce-151">For more information, see [Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="54fce-152">Ulepszenia zmiennoprzecinkowej IEEE</span><span class="sxs-lookup"><span data-stu-id="54fce-152">IEEE Floating-point improvements</span></span>

<span data-ttu-id="54fce-153">Liczb zmiennoprzecinkowych punktu interfejsy API są w trakcie aktualizacji do wykonania [poprawki 754-2008 IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="54fce-153">Floating point APIs are in the process of being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="54fce-154">Celem tych zmian jest obsługa wszystkich operacji "required" i upewnij się, że ich behaviorally zgodne ze specyfikacji IEEE.</span><span class="sxs-lookup"><span data-stu-id="54fce-154">The goal of these changes is to expose all "required" operations and ensure that they are behaviorally compliant with the IEEE spec.</span></span>

<span data-ttu-id="54fce-155">Formatowanie poprawki i analizowanie:</span><span class="sxs-lookup"><span data-stu-id="54fce-155">Parsing and formatting fixes:</span></span>

* <span data-ttu-id="54fce-156">Poprawnie przeanalizować i zaokrąglanie danych wejściowych o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="54fce-156">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="54fce-157">Poprawnie przeanalizować i sformatować ujemna zero.</span><span class="sxs-lookup"><span data-stu-id="54fce-157">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="54fce-158">Poprawnie przeanalizować nieskończoności i NaN poprzez sprawdzanie bez uwzględniania wielkości liter, dzięki czemu, opcjonalny poprzedzających `+` jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="54fce-158">Correctly parse Infinity and NaN by performing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="54fce-159">Matematyczne nowe interfejsy API są:</span><span class="sxs-lookup"><span data-stu-id="54fce-159">New Math APIs have:</span></span>

* `BitIncrement/BitDecrement`\
<span data-ttu-id="54fce-160">Odnosi się do `nextUp` i `nextDown` IEEE operacji.</span><span class="sxs-lookup"><span data-stu-id="54fce-160">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="54fce-161">Zwracają najmniejsza liczba zmiennoprzecinkowa porównuje w mniejszym lub większym niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="54fce-161">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="54fce-162">Na przykład `Math.BitIncrement(0.0)` zwróci `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="54fce-162">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* `MaxMagnitude/MinMagnitude`\
<span data-ttu-id="54fce-163">Odnosi się do `maxNumMag` i `minNumMag` operacje IEEE zwracają wartość, która jest większy lub mniejszy w wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="54fce-163">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="54fce-164">Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwróci `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="54fce-164">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* `ILogB`\
<span data-ttu-id="54fce-165">Odnosi się do `logB` IEEE operacji, która zwraca wartość całkowitą, zwraca całkowitą dziennik base 2 parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="54fce-165">Corresponds to the `logB` IEEE operation which returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="54fce-166">Efektywnie jest taka sama jak `floor(log2(x))`, ale pracy z minimalnym błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="54fce-166">This is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* `ScaleB`\
<span data-ttu-id="54fce-167">Odnosi się do `scaleB` IEEE operacji, która przyjmuje wartość całkowitą, funkcja zwraca skutecznie `x * pow(2, n)`, ale odbywa się przy użyciu minimalnego błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="54fce-167">Corresponds to the `scaleB` IEEE operation which takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* `Log2`\
<span data-ttu-id="54fce-168">Odnosi się do `log2` operacji IEEE Zwraca logarytm o podstawie 2 dla podanego.</span><span class="sxs-lookup"><span data-stu-id="54fce-168">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="54fce-169">Minimalizuje błędów zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="54fce-169">It minimizes rounding error.</span></span>

* `FusedMultiplyAdd`\
<span data-ttu-id="54fce-170">Odnosi się do `fma` wykonuje operację IEEE kolei wielokrotnie dodać.</span><span class="sxs-lookup"><span data-stu-id="54fce-170">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="54fce-171">Oznacza to robi `(x * y) + z` jako pojedyncza operacja,-, minimalizując błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="54fce-171">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="54fce-172">Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` co powoduje zwrócenie `1e308`.</span><span class="sxs-lookup"><span data-stu-id="54fce-172">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="54fce-173">Regularne `(1e308 * 2.0) - 1e308` zwraca `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="54fce-173">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* `CopySign`\
<span data-ttu-id="54fce-174">Odnosi się do `copySign` IEEE operację, zwraca wartość `x`, ale przy użyciu konta z `y`.</span><span class="sxs-lookup"><span data-stu-id="54fce-174">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="54fce-175">Wewnętrzne zależne platformy .NET</span><span class="sxs-lookup"><span data-stu-id="54fce-175">.NET Platform Dependent Intrinsics</span></span>

<span data-ttu-id="54fce-176">Dodano interfejsy API, takich jak zezwalające na dostęp do niektórych instrukcji zorientowane na wydajności procesora CPU **SIMD** lub **instrukcji manipulowania Bit** ustawia.</span><span class="sxs-lookup"><span data-stu-id="54fce-176">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="54fce-177">Te instrukcje może pomóc w osiągnięciu ulepszenia wydajności big Data w niektórych scenariuszach, takich jak przetwarzanie danych, efektywnie równolegle.</span><span class="sxs-lookup"><span data-stu-id="54fce-177">These instructions can help achieve big performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> <span data-ttu-id="54fce-178">Oprócz udostępnianie interfejsów API do programów do użycia, do bibliotek .NET rozpoczęły się przy użyciu tych instrukcji, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="54fce-178">In addition to exposing the APIs for your programs to use, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="54fce-179">Następujące żądania ściągnięcia CoreCLR pokazują niektóre funkcje wewnętrzne, za pośrednictwem implementacji lub użyj:</span><span class="sxs-lookup"><span data-stu-id="54fce-179">The following CoreCLR PRs demonstrate a few of the intrinsics, either via implementation or use:</span></span>

* [<span data-ttu-id="54fce-180">Implementowanie prostego funkcje wewnętrzne sprzętu SSE2</span><span class="sxs-lookup"><span data-stu-id="54fce-180">Implement simple SSE2 hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15585)
* [<span data-ttu-id="54fce-181">Implementuje funkcje wewnętrzne sprzętu SSE</span><span class="sxs-lookup"><span data-stu-id="54fce-181">Implement the SSE hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15538)
* [<span data-ttu-id="54fce-182">Funkcje wewnętrzne Arm64 podstawowego sprzętu</span><span class="sxs-lookup"><span data-stu-id="54fce-182">Arm64 Base HW Intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/16822)
* [<span data-ttu-id="54fce-183">Użyj TZCNT i LZCNT dla lokalizacji {pierwszy | Znaleziono ostatnie} {bajt | Char}</span><span class="sxs-lookup"><span data-stu-id="54fce-183">Use TZCNT and LZCNT for Locate{First|Last}Found{Byte|Char}</span></span>](https://github.com/dotnet/coreclr/pull/21073)

<span data-ttu-id="54fce-184">Aby uzyskać więcej informacji, zobacz [wewnętrzne zależne platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), który definiuje podejście do definiowania tej infrastruktury sprzętowej, dzięki czemu Microsoft, dostawców mikroukładu lub wszelkie inne firmy lub osoby do definiowania scalonym / W przypadku interfejsów API, które powinny być udostępniana dla kodu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="54fce-184">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), which defines an approach for defining this hardware infrastructure, allowing Microsoft, chip vendors, or any other company or individual to define hardware/chip APIs that should be exposed to .NET code.</span></span>

## <a name="default-executables"></a><span data-ttu-id="54fce-185">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="54fce-185">Default executables</span></span>

<span data-ttu-id="54fce-186">.NET core będzie teraz tworzyć [zależny od struktury plików wykonywalnych](../deploying/index.md#framework-dependent-executables-fde) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="54fce-186">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="54fce-187">Jest to nowość w aplikacji, które używają globalnie zainstalowaną wersję platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54fce-187">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="54fce-188">Do tej pory tylko [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) dałby w efekcie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="54fce-188">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="54fce-189">Podczas `dotnet build` lub `dotnet publish`, plik wykonywalny jest tworzony, pod warunkiem, które odpowiadają środowisko i platforma używasz zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="54fce-189">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="54fce-190">Mogą spodziewać się tego samego rzeczy, korzystając z tych plików wykonywalnych, tak jak w innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="54fce-190">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="54fce-191">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="54fce-191">You can double-click on the executable.</span></span>
* <span data-ttu-id="54fce-192">Można uruchomić aplikacji z poziomu wiersza polecenia, takie jak `myapp.exe` na Windows, i `./myapp` w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="54fce-192">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="54fce-193">Kopiuje zależności kompilacji</span><span class="sxs-lookup"><span data-stu-id="54fce-193">Build copies dependencies</span></span>

<span data-ttu-id="54fce-194">`dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięcią podręczną programu NuGet do folderu wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="54fce-194">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="54fce-195">Wcześniej zależności zostały skopiowane tylko jako część `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="54fce-195">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="54fce-196">Istnieją pewne operacje takie jak łączenie i razor strony publikowania, który nadal będzie wymagać publikowania.</span><span class="sxs-lookup"><span data-stu-id="54fce-196">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="54fce-197">Narzędzia do lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="54fce-197">Local dotnet tools</span></span>

>[!WARNING]
><span data-ttu-id="54fce-198">Nastąpiła zmiana w lokalnym narzędzia .NET Core między .NET Core 3.0 w wersji zapoznawczej 1 i .NET Core 3.0 w wersji zapoznawczej 2.</span><span class="sxs-lookup"><span data-stu-id="54fce-198">There was a change in .NET Core Local Tools between .NET Core 3.0 Preview 1 and .NET Core 3.0 Preview 2.</span></span>  <span data-ttu-id="54fce-199">Jeśli wypróbowane lokalne narzędzia w wersji zapoznawczej 1, uruchamiając polecenie, takie jak `dotnet tool restore` lub `dotnet tool install`, należy usunąć folder pamięci podręcznej narzędzia lokalnym przed narzędzia lokalnych będą działać poprawnie w wersji zapoznawczej 2.</span><span class="sxs-lookup"><span data-stu-id="54fce-199">If you tried out local tools in Preview 1 by running a command like `dotnet tool restore` or `dotnet tool install`, you need to delete your local tools cache folder before local tools will work correctly in Preview 2.</span></span> <span data-ttu-id="54fce-200">Ten folder znajduje się w:</span><span class="sxs-lookup"><span data-stu-id="54fce-200">This folder is located at:</span></span>
>
><span data-ttu-id="54fce-201">Na komputerze mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="54fce-201">On mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
><span data-ttu-id="54fce-202">Na Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="54fce-202">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>
>
><span data-ttu-id="54fce-203">Jeśli ten folder nie zostaną usunięte, zostanie wyświetlony błąd.</span><span class="sxs-lookup"><span data-stu-id="54fce-203">If you do not delete this folder, you will receive an error.</span></span>

<span data-ttu-id="54fce-204">.NET Core 2.1 obsługiwana globalnego narzędzia, .NET Core 3.0 to ma teraz lokalne narzędzia.</span><span class="sxs-lookup"><span data-stu-id="54fce-204">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="54fce-205">Lokalne narzędzia są podobne do narzędzia globalnych, ale są skojarzone z określonej lokalizacji na dysku.</span><span class="sxs-lookup"><span data-stu-id="54fce-205">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="54fce-206">Dzięki temu projektów i narzędzi na repozytorium.</span><span class="sxs-lookup"><span data-stu-id="54fce-206">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="54fce-207">Wszystkie zainstalowane lokalnie narzędzie nie jest globalnie dostępna.</span><span class="sxs-lookup"><span data-stu-id="54fce-207">Any tool installed locally isn't available globally.</span></span> <span data-ttu-id="54fce-208">Narzędzia są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="54fce-208">Tools are distributed as NuGet packages.</span></span>

<span data-ttu-id="54fce-209">Lokalne narzędzia opierają się na nazwę pliku manifestu `dotnet-tools.json` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="54fce-209">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="54fce-210">Ten plik manifestu definiuje narzędzia była dostępna, w tym folderze, jak i poniżej.</span><span class="sxs-lookup"><span data-stu-id="54fce-210">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="54fce-211">Ten plik manifestu są tworzone w katalogu głównym repozytorium, możesz upewnij się, każdy klonowania kodu można przywrócić i korzystania z narzędzi, które są niezbędne do pomyślnie pracę z kodem.</span><span class="sxs-lookup"><span data-stu-id="54fce-211">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="54fce-212">Aby utworzyć `dotnet-tools.json` plik manifestu, użyj:</span><span class="sxs-lookup"><span data-stu-id="54fce-212">To create a `dotnet-tools.json` manifest file, use:</span></span>

```console
dotnet new tool-manifest
```

<span data-ttu-id="54fce-213">Dodaj nowe narzędzie do lokalnego manifestu za pomocą:</span><span class="sxs-lookup"><span data-stu-id="54fce-213">Add a new tool to the local manifest with:</span></span>

```console
dotnet tool install <packageId>
```

<span data-ttu-id="54fce-214">Może również wyświetlać listę narzędzi dostępnych w lokalnym manifest za pomocą:</span><span class="sxs-lookup"><span data-stu-id="54fce-214">You can also list the tools in the local manifest with:</span></span>

```console
dotnet tool list
```

<span data-ttu-id="54fce-215">Aby zobaczyć, jakie narzędzia są zainstalowane globalnie, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="54fce-215">To see what tools are installed globally, use:</span></span>

```console
dotnet tool list -g
```

<span data-ttu-id="54fce-216">Narzędzia do lokalnego manifestu plik jest dostępny, ale narzędzia zdefiniowany w manifeście nie został zainstalowany, użyj następującego polecenia, aby automatyczne pobranie i zainstalowanie tych narzędzi:</span><span class="sxs-lookup"><span data-stu-id="54fce-216">When the local tools manifest file is available, but the tools defined in the manifest have not been installed, use the following command to automatically download and install those tools:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="54fce-217">Uruchom narzędzie lokalnych za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="54fce-217">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="54fce-218">Po uruchomieniu lokalne narzędzie dotnet wyszukuje manifest zapasową bieżącej struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="54fce-218">When a local tool is run, dotnet searches for a manifest up the current directory structure.</span></span> <span data-ttu-id="54fce-219">W przypadku odnalezienia pliku manifestu narzędzie przeszukiwany jest dla żądanego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="54fce-219">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="54fce-220">Jeśli narzędzie zostanie znaleziony w manifeście, ale nie pamięci podręcznej, użytkownik otrzyma błąd i musi zostać uruchomiony `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="54fce-220">If the tool is found in the manifest, but not the cache, the user receives an error and needs to run `dotnet tool restore`.</span></span>

<span data-ttu-id="54fce-221">Aby usunąć narzędzie z pliku manifestu lokalne narzędzie, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="54fce-221">To remove a tool from the local tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <packageId>
```

<span data-ttu-id="54fce-222">Plik manifestu narzędzia zaprojektowano w celu Zezwól na edytowanie strony — co może zrobić, aby zaktualizować wersję wymagane do pracy z repozytorium.</span><span class="sxs-lookup"><span data-stu-id="54fce-222">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span> <span data-ttu-id="54fce-223">Oto przykład `dotnet-tools.json` pliku:</span><span class="sxs-lookup"><span data-stu-id="54fce-223">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="54fce-224">Globalne i lokalne narzędzi zgodna wersja środowiska uruchomieniowego jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="54fce-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="54fce-225">Wiele narzędzi, obecnie w witrynie NuGet.org docelowej platformy .NET Core środowiska uruchomieniowego 2.1.</span><span class="sxs-lookup"><span data-stu-id="54fce-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="54fce-226">Aby zainstalować te globalnie lub lokalnie, czy nadal należy zainstalować [środowisko uruchomieniowe programu NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="54fce-226">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="54fce-227">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="54fce-227">Windows desktop</span></span>

<span data-ttu-id="54fce-228">Począwszy od programu .NET Core 3.0 w wersji zapoznawczej 1, możesz tworzyć aplikacje pulpitu Windows przy użyciu WPF i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="54fce-228">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="54fce-229">Następujące struktury obsługi, za pomocą nowoczesnych kontrolek i Fluent stylów z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [Wyspy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="54fce-229">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="54fce-230">Składnik Windows Desktop jest częścią Windows zestaw SDK programu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="54fce-230">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="54fce-231">Można utworzyć nowej aplikacji WPF i Windows Forms z następującymi `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="54fce-231">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="54fce-232">Visual Studio 2019 Preview 2 dodaje **nowy projekt** szablonów dla platformy .NET Core 3.0 Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="54fce-232">Visual Studio 2019 Preview 2 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span> <span data-ttu-id="54fce-233">Projektanci nadal jeszcze nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="54fce-233">Designers are still not yet supported.</span></span> <span data-ttu-id="54fce-234">I można otwierać, uruchamianie i debugowanie tych projektów w programie Visual Studio 2019 r.</span><span class="sxs-lookup"><span data-stu-id="54fce-234">And you can open, launch, and debug these projects in Visual Studio 2019.</span></span>

<span data-ttu-id="54fce-235">Visual Studio 2017 15.9 dodaje możliwość [Włącz podglądy platformy .NET Core](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), ale konieczne jest włączenie tej funkcji i nie jest obsługiwanym scenariuszem.</span><span class="sxs-lookup"><span data-stu-id="54fce-235">Visual Studio 2017 15.9 adds the ability to [enable .NET Core previews](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), but you need to turn that feature on, and it's not a supported scenario.</span></span>

<span data-ttu-id="54fce-236">Nowe projekty są takie same jak istniejących projektów .NET Core z dodatkami kilka.</span><span class="sxs-lookup"><span data-stu-id="54fce-236">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="54fce-237">Oto porównanie podstawowy projekt konsoli .NET Core i podstawowy projekt Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="54fce-237">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="54fce-238">W projekcie konsoli .NET Core, projekt korzysta z `Microsoft.NET.Sdk` zestawu SDK ale deklaruje zależności na .NET Core 3.0 to za pośrednictwem `netcoreapp3.0` platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="54fce-238">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="54fce-239">Aby utworzyć aplikację pulpitu Windows, należy użyć `Microsoft.NET.Sdk.WindowsDesktop` zestawu SDK i wybierz polecenie struktury interfejsu użytkownika, których można użyć:</span><span class="sxs-lookup"><span data-stu-id="54fce-239">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="54fce-240">Aby wybrać Windows Forms w WPF, należy ustawić `UseWindowsForms` zamiast `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="54fce-240">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="54fce-241">Zarówno `UseWPF` i `UseWindowsForms` można ustawić `true` Jeśli aplikacja korzysta z obu platform, na przykład gdy okno dialogowe Windows Forms jest hosting kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="54fce-241">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="54fce-242">Podziel się swoją opinię na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) i [dotnet/core](https://github.com/dotnet/core/issues) repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="54fce-242">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="msix-deployment-for-windows-desktop"></a><span data-ttu-id="54fce-243">Wdrożenie MSIX for Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="54fce-243">MSIX Deployment for Windows Desktop</span></span>

<span data-ttu-id="54fce-244">[MSIX](https://docs.microsoft.com/windows/msix/) jest nowy format pakietu aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="54fce-244">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows app package format.</span></span> <span data-ttu-id="54fce-245">Może służyć do wdrażania aplikacji klasycznych .NET Core 3.0 dla systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="54fce-245">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="54fce-246">[Projekt pakietu aplikacji Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępne w wersji 2 (wersja zapoznawcza) 2019 r w usłudze Visual Studio, umożliwia tworzenie pakietów MSIX [niezależna](../deploying/index.md#self-contained-deployments-scd) aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54fce-246">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019 Preview 2, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

><span data-ttu-id="54fce-247">Uwaga: Plik projektu .NET Core, musisz określić obsługiwane środowiska uruchomieniowe w `<RuntimeIdentifiers>` właściwości:</span><span class="sxs-lookup"><span data-stu-id="54fce-247">Note: The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a><span data-ttu-id="54fce-248">Szybkie wbudowanej obsługi formatu JSON</span><span class="sxs-lookup"><span data-stu-id="54fce-248">Fast built-in JSON support</span></span>

<span data-ttu-id="54fce-249">Ekosystemu .NET opierało się na [ **Json.NET** ](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal dobrych wyborów.</span><span class="sxs-lookup"><span data-stu-id="54fce-249">The .NET ecosystem has relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="54fce-250">**Program Json.NET** używa ciągów .NET jako jego podstawowy datatype kulisy używanej na UTF-16.</span><span class="sxs-lookup"><span data-stu-id="54fce-250">**Json.NET** uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span>

<span data-ttu-id="54fce-251">Nowa funkcja wbudowanej obsługi JSON to alokacji o wysokiej wydajności, niski i oparte na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="54fce-251">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="54fce-252">Trzy nowe główne powiązane JSON typy zostały dodane do platformy .NET Core 3.0 `System.Text.Json` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="54fce-252">Three new main JSON-related types have been added to .NET Core 3.0 the `System.Text.Json` namespace.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="54fce-253">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="54fce-253">Utf8JsonReader</span></span>

<span data-ttu-id="54fce-254">`System.Text.Json.Utf8JsonReader` jest o wysokiej wydajności, niski alokacji, tylko do przodu czytnik UTF-8 kodowany w formacie JSON tekst odczytywane `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="54fce-254">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="54fce-255">`Utf8JsonReader` Jest typem podstawowe, niskiego poziomu, który można wykorzystać do tworzenia niestandardowych analizatory i deserializers.</span><span class="sxs-lookup"><span data-stu-id="54fce-255">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="54fce-256">Odczytywanie za pośrednictwem ładunek w formacie JSON za pomocą nowego `Utf8JsonReader` wynosi 2 x szybciej niż przy użyciu czytnika, z **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="54fce-256">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="54fce-257">Nie przydziela do czasu konieczne actualize tokenów JSON jako ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="54fce-257">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="54fce-258">Ten nowy interfejs API obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="54fce-258">This new API will include the following components:</span></span>

* <span data-ttu-id="54fce-259">W wersji zapoznawczej 1: Czytnik JSON (dostępu sekwencyjnego)</span><span class="sxs-lookup"><span data-stu-id="54fce-259">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="54fce-260">Dodana w następnej kolejności: Moduł zapisujący JSON, modelu DOM (dostępu swobodnego) obiektów poco elementu serializującego obiektów poco Deserializator</span><span class="sxs-lookup"><span data-stu-id="54fce-260">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="54fce-261">Oto pętli czytnika podstawowego `Utf8JsonReader` mogą służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="54fce-261">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a><span data-ttu-id="54fce-262">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="54fce-262">Utf8JsonWriter</span></span>

<span data-ttu-id="54fce-263">`System.Text.Json.Utf8JsonWriter` zapewnia wysoce wydajnych niebuforowanym, tylko do zapisu kodowany w formacie UTF-8 do przodu tekstu JSON z popularnych typów .NET, takich jak `String`, `Int32`, i `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="54fce-263">`System.Text.Json.Utf8JsonWriter` provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="54fce-264">Podobnie jak czytelnik moduł zapisujący jest typu podstawowe, niskiego poziomu, który można wykorzystać do tworzenia niestandardowych serializatory.</span><span class="sxs-lookup"><span data-stu-id="54fce-264">Like the reader, the writer is a foundational, low-level type, that can be leveraged to build custom serializers.</span></span> <span data-ttu-id="54fce-265">Zapis ładunku JSON za pomocą nowego `Utf8JsonWriter` wynosi 30-80% szybciej niż przy użyciu składnika zapisywania z **Json.NET** i nie przydziela.</span><span class="sxs-lookup"><span data-stu-id="54fce-265">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and does not allocate.</span></span>

<span data-ttu-id="54fce-266">Poniżej przedstawiono przykładowe zastosowanie `Utf8JsonWriter` mogą służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="54fce-266">Here is a sample usage of the `Utf8JsonWriter` that can be used as a starting point:</span></span>

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

<span data-ttu-id="54fce-267">`Utf8JsonWriter` Akceptuje `IBufferWriter<byte>` jako lokalizacja danych wyjściowych synchronicznie zapisać dane json, a jako obiekt wywołujący należy podać konkretną implementację.</span><span class="sxs-lookup"><span data-stu-id="54fce-267">The `Utf8JsonWriter` accepts `IBufferWriter<byte>` as the output location to synchronously write the json data into, and you as the caller need to provide a concrete implementation.</span></span> <span data-ttu-id="54fce-268">Platforma nie zawiera implementację tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="54fce-268">The platform does not currently include an implementation of this interface.</span></span> <span data-ttu-id="54fce-269">Na przykład `IBufferWriter<byte>`, zobacz [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span><span class="sxs-lookup"><span data-stu-id="54fce-269">For an example of `IBufferWriter<byte>`, see [https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35)</span></span>

### <a name="jsondocument"></a><span data-ttu-id="54fce-270">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="54fce-270">JsonDocument</span></span>

<span data-ttu-id="54fce-271">`System.Text.Json.JsonDocument` jest wbudowana w górnej części `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="54fce-271">`System.Text.Json.JsonDocument` is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="54fce-272">`JsonDocument` Zapewnia możliwość analizowania danych JSON i dokonać jego kompilacji tylko do odczytu modelu DOM (Document Object) można wykonywać zapytania do obsługi dostępu losowego i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="54fce-272">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="54fce-273">Elementy JSON, które tworzą dane można uzyskać dostęp za pośrednictwem `JsonElement` typu, który jest uwidaczniany przez `JsonDocument` jako właściwość o nazwie `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="54fce-273">The JSON elements that compose the data can be accessed via the `JsonElement` type which is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="54fce-274">`JsonElement` Zawiera wyliczenia tablicy i obiektów JSON, wraz z interfejsów API do konwertowania tekstu JSON do popularnych typów .NET.</span><span class="sxs-lookup"><span data-stu-id="54fce-274">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="54fce-275">Analizowanie typowe ładunek w formacie JSON i uzyskiwania dostępu do wszystkich jej członków przy użyciu `JsonDocument` jest szybsza niż x 2 – 3 **Json.NET** z niewielkim alokacji dla danych, które są racjonalnie o rozmiarze (czyli < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="54fce-275">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with very little allocations for data that is reasonably sized (i.e. < 1 MB).</span></span>

<span data-ttu-id="54fce-276">Poniżej przedstawiono przykładowe zastosowanie `JsonDocument` i `JsonElement` mogą służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="54fce-276">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a><span data-ttu-id="54fce-277">Unloadability zestawu</span><span class="sxs-lookup"><span data-stu-id="54fce-277">Assembly Unloadability</span></span>

<span data-ttu-id="54fce-278">Unloadability zestawu jest nową funkcją `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="54fce-278">Assembly unloadability is a new capability of `AssemblyLoadContext`.</span></span> <span data-ttu-id="54fce-279">Ta nowa funkcja jest w dużej mierze przejrzyste z perspektywy API udostępnianych za pomocą zaledwie kilku nowych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="54fce-279">This new feature is largely transparent from an API perspective, exposed with just a few new APIs.</span></span> <span data-ttu-id="54fce-280">Dzięki temu można zwolnić zwalnianie pamięci wszystkich wystąpień typów, pola statyczne i samego montażu kontekst modułu ładującego.</span><span class="sxs-lookup"><span data-stu-id="54fce-280">It enables a loader context to be unloaded, releasing all memory for instantiated types, static fields and for the assembly itself.</span></span> <span data-ttu-id="54fce-281">Aplikacja powinna mieć możliwość ładowanie i zwalnianie zestawów za pomocą tego mechanizmu w nieskończoność, bez występuje przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="54fce-281">An application should be able to load and unload assemblies via this mechanism forever without experiencing a memory leak.</span></span>

<span data-ttu-id="54fce-282">Ta nowa funkcja może służyć do scenariuszy, podobnie do:</span><span class="sxs-lookup"><span data-stu-id="54fce-282">This new capability can be used for scenarios similar to:</span></span>

* <span data-ttu-id="54fce-283">Wtyczka scenariuszy, w której dodatek dynamicznej, ładowanie i zwalnianie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="54fce-283">Plugin scenarios where dynamic plugin loading and unloading is required.</span></span> 
* <span data-ttu-id="54fce-284">Dynamiczne kompilowanie, uruchamianie i następnie opróżnianie kodu.</span><span class="sxs-lookup"><span data-stu-id="54fce-284">Dynamically compiling, running and then flushing code.</span></span> <span data-ttu-id="54fce-285">Przydatne w przypadku witryn sieci web, skryptów aparatów itp.</span><span class="sxs-lookup"><span data-stu-id="54fce-285">Useful for web sites, scripting engines, etc.</span></span>
* <span data-ttu-id="54fce-286">Ładowanie zestawów do introspekcji (na przykład ReflectionOnlyLoad), mimo że [MetadataLoadContext](#type-metadataloadcontext) (wydane w wersji zapoznawczej 1) będzie lepszym rozwiązaniem w wielu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="54fce-286">Loading assemblies for introspection (like ReflectionOnlyLoad), although [MetadataLoadContext](#type-metadataloadcontext) (released in Preview 1) will be a better choice in many cases.</span></span>

<span data-ttu-id="54fce-287">Aby uzyskać więcej informacji, zobacz [przy użyciu Unloadability](https://github.com/dotnet/coreclr/pull/22221) dokumentu.</span><span class="sxs-lookup"><span data-stu-id="54fce-287">For more information, see the [Using Unloadability](https://github.com/dotnet/coreclr/pull/22221) document.</span></span>

<span data-ttu-id="54fce-288">Zwalnianie zestawów wymaga znaczących opieki, aby upewnić się, że wszystkie odwołania do obiektów zarządzanych z poza kontekstem modułu ładującego są zrozumiałe i zarządzane.</span><span class="sxs-lookup"><span data-stu-id="54fce-288">Assembly unloading requires significant care to ensure that all references to managed objects from outside a loader context are understood and managed.</span></span> <span data-ttu-id="54fce-289">Kontekst modułu ładującego zleconą można zwolnić zewnętrznego odwołania musi zostać nieużywanej tak, aby kontekst modułu ładującego jest spójny tylko do samego siebie.</span><span class="sxs-lookup"><span data-stu-id="54fce-289">When the loader context is requested to be unloaded, any outside references need to have been unreferenced so that the loader context is self-consistent only to itself.</span></span>

<span data-ttu-id="54fce-290">W .NET Framework podano unloadability zestawu domen aplikacji (domen aplikacji), które nie są obsługiwane za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54fce-290">Assembly unloadability was provided in the .NET Framework by Application Domains (AppDomains), which are not supported with .NET Core.</span></span> <span data-ttu-id="54fce-291">Domen aplikacji ma zalety i ograniczenia w porównaniu do tego nowego modelu.</span><span class="sxs-lookup"><span data-stu-id="54fce-291">AppDomains had both benefits and limitations compared to this new model.</span></span> <span data-ttu-id="54fce-292">Należy wziąć pod uwagę ten nowy model modułu ładującego do bardziej elastyczne i wyższej wydajności w porównaniu do domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54fce-292">Consider this new loader model to be more flexible and higher performant when compared to AppDomains.</span></span>

## <a name="windows-native-interop"></a><span data-ttu-id="54fce-293">Współdziałanie natywne Windows</span><span class="sxs-lookup"><span data-stu-id="54fce-293">Windows Native Interop</span></span>

<span data-ttu-id="54fce-294">Windows oferuje zaawansowane natywne interfejsy API, w postaci prostych interfejsów API języka C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="54fce-294">Windows offers a rich native API, in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="54fce-295">Od platformy .NET Core 1.0 **P/Invoke** obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="54fce-295">Since .NET Core 1.0, **P/Invoke** has been supported.</span></span> <span data-ttu-id="54fce-296">Za pomocą platformy .NET Core 3.0 to obsługują teraz możliwość **CoCreate interfejsów API modelu COM** i **aktywować interfejsów API WinRT** został dodany.</span><span class="sxs-lookup"><span data-stu-id="54fce-296">Now with .NET Core 3.0, support for the ability to **CoCreate COM APIs** and **Activate WinRT APIs** has been added.</span></span>

<span data-ttu-id="54fce-297">Możesz zobaczyć przykład korzystając z modelu COM za pomocą [kodu źródłowego w wersji demonstracyjnej programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="54fce-297">You can see an example of using COM with the [Excel Demo source code](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>


## <a name="type-sequencereader"></a><span data-ttu-id="54fce-298">Wpisz: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="54fce-298">Type: SequenceReader</span></span>

<span data-ttu-id="54fce-299">W programie .NET Core 3.0 `System.Buffers.SequenceReader` dodano, który może służyć jako czytnik `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="54fce-299">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="54fce-300">Umożliwia to łatwe w użyciu o wysokiej wydajności, niski alokacji analizowanie `System.IO.Pipelines` dane, które mogą przechodzić przez kilka buforów zapasowy.</span><span class="sxs-lookup"><span data-stu-id="54fce-300">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="54fce-301">Poniższy przykład dzieli dane wejściowe `Sequence` na prawidłowe `CR/LF` rozdzielonych wiersze:</span><span class="sxs-lookup"><span data-stu-id="54fce-301">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="54fce-302">Wpisz: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="54fce-302">Type: MetadataLoadContext</span></span>

<span data-ttu-id="54fce-303">`MetadataLoadContext` Typ został dodany, który umożliwia odczytywanie zestawu metadanych, bez wywierania wpływu na domeny aplikacji obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="54fce-303">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="54fce-304">Zestawy są odczytywane jako dane, w tym zestawy stworzona z myślą o różnych architektur oraz platformach niż bieżącego środowiska.</span><span class="sxs-lookup"><span data-stu-id="54fce-304">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="54fce-305">`MetadataLoadContext` nakłada się na <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, która jest dostępna tylko w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54fce-305">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="54fce-306">`MetdataLoadContext` jest dostępna w [pakietu System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="54fce-306">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="54fce-307">To pakiet .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="54fce-307">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="54fce-308">`MetadataLoadContext` Udostępnia interfejsy API, podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale nie zależy od tego typu.</span><span class="sxs-lookup"><span data-stu-id="54fce-308">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="54fce-309">Podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` umożliwia ładowanie zestawów w zestawie izolowane ładowania wszechświat.</span><span class="sxs-lookup"><span data-stu-id="54fce-309">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="54fce-310">`MetdataLoadContext` Interfejsy API zwracają <xref:System.Reflection.Assembly> obiektów, umożliwiające użycie odbicia dobrze znanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="54fce-310">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="54fce-311">Wykonanie zorientowane na interfejsy API, takich jak [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nie są dozwolone i będzie zgłaszać wyjątek InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="54fce-311">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="54fce-312">W poniższym przykładzie pokazano, jak znaleźć konkretne typy w zestawie, który implementuje danego interfejsu:</span><span class="sxs-lookup"><span data-stu-id="54fce-312">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="54fce-313">Scenariusze dotyczące `MetadataLoadContext` obejmują funkcje czasu projektowania, narzędzi, czas kompilacji i środowiska uruchomieniowego światła w górę funkcje wymagające sprawdzanie zbiór zestawów danych i ma blokady wszystkich plików i pamięć zwolniona po kontroli jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="54fce-313">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="54fce-314">`MetadataLoadContext` Przeszła klasy programu rozpoznawania nazw dla jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="54fce-314">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="54fce-315">Zadanie programu rozpoznawania nazw ma ładować `Assembly` biorąc pod uwagę jej `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="54fce-315">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="54fce-316">Klasa rozpoznawania pochodzi z abstrakcyjnej `MetadataAssemblyResolver` klasy.</span><span class="sxs-lookup"><span data-stu-id="54fce-316">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="54fce-317">Implementacja programu rozpoznawania nazw dla scenariuszy opartych na ścieżkach jest dostarczana z `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="54fce-317">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="54fce-318">[Testy MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) pokazują wielu przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="54fce-318">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="54fce-319">[Zestawu testów](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) są dobrym miejscem do rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="54fce-319">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="54fce-320">TLS 1.3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="54fce-320">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="54fce-321">.NET core będą teraz korzystać z [Obsługa protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy będzie ona dostępna w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="54fce-321">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="54fce-322">Istnieją różne korzyści 1.3 protokołu TLS na [zespołu OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="54fce-322">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="54fce-323">Czas połączenia ulepszona z powodu ograniczenia liczby rund między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="54fce-323">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="54fce-324">Ulepszone zabezpieczenia z powodu usunięcia rozmaite algorytmy kryptograficzne przestarzały i niezabezpieczone i szyfrowania większej uzgadniania połączenia.</span><span class="sxs-lookup"><span data-stu-id="54fce-324">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="54fce-325">.NET core 3.0 w wersji zapoznawczej 1 jest w stanie wykorzystujących **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, lub **OpenSSL 1.0.2** (niezależnie od znaleziono wersji najlepiej jest, w systemie Linux).</span><span class="sxs-lookup"><span data-stu-id="54fce-325">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="54fce-326">Podczas **OpenSSL 1.1.1** jest dostępna będzie używać typów SslStream i HttpClient **TLS 1.3** korzystając z `SslProtocols.None` (protokołów domyślne systemu), zakładając, że klient i serwer obsługi **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="54fce-326">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="54fce-327">W poniższym przykładzie pokazano .NET Core 3.0 w wersji zapoznawczej 1 na 18.10 Ubuntu nawiązywania połączenia z <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="54fce-327">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="54fce-328">Windows i macOS nie jest jeszcze obsługiwany **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="54fce-328">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="54fce-329">.NET core 3.0 to będzie obsługiwać **TLS 1.3** w tych systemach operacyjnych po udostępnieniu Pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="54fce-329">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="54fce-330">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="54fce-330">Cryptography</span></span>

<span data-ttu-id="54fce-331">Dodano obsługę dla **AES-GCM** i **AES-CCM** szyfrów, wdrożone za pośrednictwem `System.Security.Cryptography.AesGcm` i `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="54fce-331">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="54fce-332">Te algorytmy są [uwierzytelnione szyfrowanie za pomocą algorytmów skojarzenia danych (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)i pierwszy algorytmów szyfrowania uwierzytelniony (AE) dodane do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54fce-332">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="54fce-333">Poniższy kod demonstruje użycie **AesGcm** szyfrowania do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="54fce-333">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="54fce-334">Kod **AesCcm** będzie wyglądała niemal identyczne (tylko nazwy zmiennych klasy może się różnić).</span><span class="sxs-lookup"><span data-stu-id="54fce-334">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="54fce-335">Kryptograficznych kluczy importu/eksportu</span><span class="sxs-lookup"><span data-stu-id="54fce-335">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="54fce-336">.NET core 3.0 w wersji zapoznawczej 1 obsługuje importowanie i eksportowanie kluczy asymetrycznych publicznych i prywatnych z standardowych formatów, bez konieczności korzystania z certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="54fce-336">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="54fce-337">Wszystkie klucza Obsługa typów (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** format kluczy publicznych i **PKCS #8 PrivateKeyInfo** i **PKCS #8 EncryptedPrivateKeyInfo**  formatów dla kluczy prywatnych.</span><span class="sxs-lookup"><span data-stu-id="54fce-337">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="54fce-338">Dodatkowo obsługuje RSA **PKCS #1 RSAPublicKey** i **PKCS #1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="54fce-338">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="54fce-339">Wszystkie metody eksportowania generuje dane binarne zakodowane w formacie DER i metod import oczekiwać takie same.</span><span class="sxs-lookup"><span data-stu-id="54fce-339">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="54fce-340">Jeśli klucz jest przechowywany w formacie PEM przyjaznego tekstu, obiekt wywołujący, będą musieli base64 — dekodowanie zawartości przed wywołaniem metody importu.</span><span class="sxs-lookup"><span data-stu-id="54fce-340">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="54fce-341">Pliki PKCS #8 mogą być kontrolowane za pomocą `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` klasy.</span><span class="sxs-lookup"><span data-stu-id="54fce-341">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="54fce-342">Pliki PFX/PKCS #12, które mogą być kontrolowane i modyfikować za pomocą `System.Security.Cryptography.Pkcs.Pkcs12Info` i `System.Security.Cryptography.Pkcs.Pkcs12Builder`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="54fce-342">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="54fce-343">Portu SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="54fce-343">SerialPort for Linux</span></span>

<span data-ttu-id="54fce-344">.NET core 3.0 obsługuje teraz <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="54fce-344">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="54fce-345">Wcześniej, .NET Core obsługiwana tylko przy użyciu `SerialPort` typu na Windows.</span><span class="sxs-lookup"><span data-stu-id="54fce-345">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="54fce-346">Więcej udoskonaleń BCL</span><span class="sxs-lookup"><span data-stu-id="54fce-346">More BCL Improvements</span></span>

<span data-ttu-id="54fce-347">`Span<T>`, `Memory<T>`, I w środowisku .NET Core 3.0 zostały zoptymalizowane powiązanych typów, które zostały wprowadzone w programie .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="54fce-347">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="54fce-348">Typowe operacje takie jak span konstrukcji, dzielenie, analizowania i formatowanie teraz działać lepiej.</span><span class="sxs-lookup"><span data-stu-id="54fce-348">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="54fce-349">Ponadto takie jak typy `String` przejrzane czyni je bardziej efektywnymi, gdy jest używana jako klucze o ulepszenia w obszarze cover `Dictionary<TKey, TValue>` i innych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="54fce-349">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="54fce-350">Bez zmian w kodzie są wymagane do korzystania z tych ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="54fce-350">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="54fce-351">Następujące ulepszenia również są nowe w .NET Core 3 (wersja zapoznawcza) 1:</span><span class="sxs-lookup"><span data-stu-id="54fce-351">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="54fce-352">Obsługa Brotli wbudowanej w HttpClient</span><span class="sxs-lookup"><span data-stu-id="54fce-352">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="54fce-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="54fce-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="54fce-354">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="54fce-354">Unsafe.Unbox</span></span>
* <span data-ttu-id="54fce-355">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="54fce-355">CancellationToken.Unregister</span></span>
* <span data-ttu-id="54fce-356">Złożone operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="54fce-356">Complex arithmetic operators</span></span>
* <span data-ttu-id="54fce-357">Podtrzymywania API gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="54fce-357">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="54fce-358">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="54fce-358">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="54fce-359">IPEndPoint analizy</span><span class="sxs-lookup"><span data-stu-id="54fce-359">IPEndPoint parsing</span></span>
* <span data-ttu-id="54fce-360">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="54fce-360">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="54fce-361">Warstwowe kompilacji</span><span class="sxs-lookup"><span data-stu-id="54fce-361">Tiered compilation</span></span>

<span data-ttu-id="54fce-362">[Warstwowe kompilacji](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) jest domyślnie przy użyciu platformy .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="54fce-362">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="54fce-363">Jest funkcją, która umożliwia bardziej adaptacyjnie Użyj kompilator just in Time (JIT), aby uzyskać lepszą wydajność, zarówno podczas uruchamiania i w celu zmaksymalizowania wydajności.</span><span class="sxs-lookup"><span data-stu-id="54fce-363">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="54fce-364">Ta funkcja została dodana jako funkcja opcjonalna w [platformy .NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) i następnie została włączona domyślnie w [.NET Core 2.2 w wersji zapoznawczej 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="54fce-364">This feature was added as an opt-in feature in [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="54fce-365">Następnie został on przywrócony do zoptymalizowany pod kątem się przy użyciu wersji platformy .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="54fce-365">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="54fce-366">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="54fce-366">ARM64 Linux support</span></span>

<span data-ttu-id="54fce-367">Dodano obsługę dla architektury ARM64 dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="54fce-367">Support has been added for ARM64 for Linux.</span></span> <span data-ttu-id="54fce-368">Głównym zastosowaniem dla architektury ARM64 jest obecnie używany w scenariuszach IoT.</span><span class="sxs-lookup"><span data-stu-id="54fce-368">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="54fce-369">Firma Alpine, Debian i Ubuntu [obrazów platformy Docker są dostępne dla platformy .NET Core dla architektury ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="54fce-369">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="54fce-370">Sprawdź, czy [stanu programu .NET Core ARM64](https://github.com/dotnet/announcements/issues/82) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="54fce-370">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="54fce-371">**ARM64** pomocy technicznej Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="54fce-371">**ARM64** Windows support isn't yet available.</span></span>

## <a name="install-net-core-30-previews-on-linux-with-snap"></a><span data-ttu-id="54fce-372">Instalowanie wersji zapoznawczych programu .NET Core 3.0 w systemie Linux za pomocą przystawki</span><span class="sxs-lookup"><span data-stu-id="54fce-372">Install .NET Core 3.0 Previews on Linux with Snap</span></span>

<span data-ttu-id="54fce-373">Przystawki jest preferowanym sposobem zainstalować i spróbować wersji zapoznawczych platformy .NET Core [systemu Linux obsługujących przystawki](https://docs.snapcraft.io/installing-snapd/6735).</span><span class="sxs-lookup"><span data-stu-id="54fce-373">Snap is the preferred way to install and try .NET Core previews on [Linux distributions that support Snap](https://docs.snapcraft.io/installing-snapd/6735).</span></span>

<span data-ttu-id="54fce-374">Po skonfigurowaniu przyciągania w systemie, uruchom następujące polecenie, aby zainstalować [zestawu SDK platformy .NET Core SDK 3.0 w wersji zapoznawczej](https://snapcraft.io/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="54fce-374">After configuring Snap on your system, run the following command to install the [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk).</span></span>

```console
sudo snap install dotnet-sdk --beta --classic
```
 
<span data-ttu-id="54fce-375">.NET Core w zainstalowanych przy użyciu pakietu przystawki domyślnego polecenia .NET Core po `dotnet-sdk.dotnet`, a nie po prostu `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="54fce-375">When .NET Core in installed using the Snap package, the default .NET Core command is `dotnet-sdk.dotnet`, as opposed to just `dotnet`.</span></span> <span data-ttu-id="54fce-376">Polecenie namespaced ma, nie będzie ona konflikt z globalnie zainstalowanej wersji platformy .NET Core, które mogą wiązać Ciebie.</span><span class="sxs-lookup"><span data-stu-id="54fce-376">The benefit of the namespaced command is that it will not conflict with a globally installed .NET Core version you may have.</span></span> <span data-ttu-id="54fce-377">To polecenie może być aliasem do `dotnet` za pomocą:</span><span class="sxs-lookup"><span data-stu-id="54fce-377">This command can be aliased to `dotnet` with:</span></span>

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="54fce-378">Niektóre dystrybucje wymagają dodatkowych czynności, aby umożliwić dostęp do certyfikatu SSL.</span><span class="sxs-lookup"><span data-stu-id="54fce-378">Some distros require an additional step to enable access to the SSL certificate.</span></span> <span data-ttu-id="54fce-379">Zobacz nasze [Konfiguracja w systemie Linux](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) Aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="54fce-379">See our [Linux Setup](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) for details.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="54fce-380">Interfejs GPIO obsługa urządzenia Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="54fce-380">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="54fce-381">Dwa nowe pakiety zostały zwolnione do narzędzia NuGet używanego do programowania GPIO.</span><span class="sxs-lookup"><span data-stu-id="54fce-381">Two new packages have been released to NuGet that you can use for GPIO programming.</span></span>

* [<span data-ttu-id="54fce-382">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="54fce-382">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [<span data-ttu-id="54fce-383">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="54fce-383">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

<span data-ttu-id="54fce-384">Pakiety GPIO obejmuje funkcje interfejsu API dla urządzeń z GPIO, SPI, I2C i PWM.</span><span class="sxs-lookup"><span data-stu-id="54fce-384">The GPIO Packages includes APIs for GPIO, SPI, I2C and PWM devices.</span></span> <span data-ttu-id="54fce-385">Pakiet IoT powiązania obejmuje [powiązania urządzenia](https://github.com/dotnet/iot/blob/master/src/devices/README.md) różne kawałki i czujników, taki sam, te, które są dostępne pod adresem [dotnet/iot-src/urządzeń](https://github.com/dotnet/iot/tree/master/src/devices).</span><span class="sxs-lookup"><span data-stu-id="54fce-385">The IoT bindings package includes [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) for various chips and sensors, the same ones available at [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices).</span></span>

<span data-ttu-id="54fce-386">Zaktualizowano portu szeregowego nie należą do tych pakietów interfejsów API, które zostały ogłoszone w ramach platformy .NET Core 3.0 w wersji zapoznawczej 1, ale są dostępne w ramach platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="54fce-386">The updated serial port APIs that were announced as part of .NET Core 3.0 Preview 1 are not part of these packages but are available as part of the .NET Core platform.</span></span>


## <a name="platform-support"></a><span data-ttu-id="54fce-387">Obsługa platformy</span><span class="sxs-lookup"><span data-stu-id="54fce-387">Platform Support</span></span>

<span data-ttu-id="54fce-388">.NET core 3 będą obsługiwane w następujących systemach operacyjnych:</span><span class="sxs-lookup"><span data-stu-id="54fce-388">.NET Core 3 will be supported on the following operating systems:</span></span>

* <span data-ttu-id="54fce-389">Klient Windows: 7, 8.1, 10 (1607+)</span><span class="sxs-lookup"><span data-stu-id="54fce-389">Windows Client: 7, 8.1, 10 (1607+)</span></span>
* <span data-ttu-id="54fce-390">Windows Server: 2012 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="54fce-390">Windows Server: 2012 R2 SP1+</span></span>
* <span data-ttu-id="54fce-391">macOS: 10.12+</span><span class="sxs-lookup"><span data-stu-id="54fce-391">macOS: 10.12+</span></span>
* <span data-ttu-id="54fce-392">RHEL: 6+</span><span class="sxs-lookup"><span data-stu-id="54fce-392">RHEL: 6+</span></span>
* <span data-ttu-id="54fce-393">Fedora: 26+</span><span class="sxs-lookup"><span data-stu-id="54fce-393">Fedora: 26+</span></span>
* <span data-ttu-id="54fce-394">Ubuntu: 16.04+</span><span class="sxs-lookup"><span data-stu-id="54fce-394">Ubuntu: 16.04+</span></span>
* <span data-ttu-id="54fce-395">Debian: 9+</span><span class="sxs-lookup"><span data-stu-id="54fce-395">Debian: 9+</span></span>
* <span data-ttu-id="54fce-396">SLES: 12+</span><span class="sxs-lookup"><span data-stu-id="54fce-396">SLES: 12+</span></span>
* <span data-ttu-id="54fce-397">openSUSE: 42.3+</span><span class="sxs-lookup"><span data-stu-id="54fce-397">openSUSE: 42.3+</span></span>
* <span data-ttu-id="54fce-398">Firma Alpine: 3.8+</span><span class="sxs-lookup"><span data-stu-id="54fce-398">Alpine: 3.8+</span></span>

<span data-ttu-id="54fce-399">Obsługa mikroukładu następująco:</span><span class="sxs-lookup"><span data-stu-id="54fce-399">Chip support follows:</span></span>

* <span data-ttu-id="54fce-400">x64 w Windows, macOS i Linux</span><span class="sxs-lookup"><span data-stu-id="54fce-400">x64 on Windows, macOS, and Linux</span></span>
* <span data-ttu-id="54fce-401">x86 na Windows</span><span class="sxs-lookup"><span data-stu-id="54fce-401">x86 on Windows</span></span>
* <span data-ttu-id="54fce-402">ARM32 w systemach Windows i Linux</span><span class="sxs-lookup"><span data-stu-id="54fce-402">ARM32 on Windows and Linux</span></span>
* <span data-ttu-id="54fce-403">ARM64 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="54fce-403">ARM64 on Linux</span></span>

<span data-ttu-id="54fce-404">W przypadku systemu Linux ARM32 jest obsługiwana na Debian 9 + i systemem Ubuntu 16.04 +.</span><span class="sxs-lookup"><span data-stu-id="54fce-404">For Linux, ARM32 is supported on Debian 9+ and Ubuntu 16.04+.</span></span> <span data-ttu-id="54fce-405">Dla architektury ARM64 jest taka sama jak ARM32 dodając Alpine 3.8.</span><span class="sxs-lookup"><span data-stu-id="54fce-405">For ARM64, it is the same as ARM32 with the addition of Alpine 3.8.</span></span> <span data-ttu-id="54fce-406">Są to te same wersje tych dystrybucje, ponieważ jest obsługiwana X64.</span><span class="sxs-lookup"><span data-stu-id="54fce-406">These are the same versions of those distros as is supported for X64.</span></span>

<span data-ttu-id="54fce-407">Obrazy platformy docker dla platformy .NET Core 3.0 są dostępne pod adresem [microsoft/dotnet w usłudze Docker Hub](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="54fce-407">Docker images for .NET Core 3.0 are available at [microsoft/dotnet on Docker Hub](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="54fce-408">Firma Microsoft jest obecnie w trakcie przyjmowania [rejestru kontenerów firmy Microsoft (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) i oczekuje się, że końcowy obrazów platformy .NET Core 3.0 tylko zostaną opublikowane na MCR.</span><span class="sxs-lookup"><span data-stu-id="54fce-408">Microsoft is currently in the process of adopting [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) and it is expected that the final .NET Core 3.0 images will only be published to MCR.</span></span>
