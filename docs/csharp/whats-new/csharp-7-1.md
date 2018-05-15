---
title: Nowości w języku C# 7.1
description: Przegląd nowych funkcji w języku C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 00baec45d7582d3ac12c7b0865241f5cd8159246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="fe155-103">Nowości w języku C# 7.1</span><span class="sxs-lookup"><span data-stu-id="fe155-103">What's new in C# 7.1</span></span>

<span data-ttu-id="fe155-104">C# 7.1 to pierwszy punkt wersji języka C#.</span><span class="sxs-lookup"><span data-stu-id="fe155-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="fe155-105">Umożliwia oznaczanie okresach wydania zwiększona dla języka.</span><span class="sxs-lookup"><span data-stu-id="fe155-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="fe155-106">Służy nowe funkcje wcześniej, najlepszym rozwiązaniem, gdy każda nowa funkcja jest gotowe.</span><span class="sxs-lookup"><span data-stu-id="fe155-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="fe155-107">C# 7.1 dodaje możliwość konfigurowania kompilatora do dopasowania określonej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="fe155-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="fe155-108">Który umożliwia decyzja o uaktualnienie narzędzia decyzja o uaktualnienie wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="fe155-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="fe155-109">C# 7.1 dodaje [wybór wersji języka](#language-version-selection) element konfiguracji, trzy nowe funkcje językowe i nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fe155-109">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="fe155-110">Dostępne są następujące nowe funkcje językowe w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="fe155-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="fe155-111">`async` `Main` — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe155-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="fe155-112">Punkt wejścia dla aplikacji może mieć `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="fe155-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="fe155-113">`default` Wyrażenia dosłowne</span><span class="sxs-lookup"><span data-stu-id="fe155-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="fe155-114">Gdy typ docelowy można wywnioskować, można użyć wyrażenia dosłowne domyślne w wyrażeniach wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="fe155-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="fe155-115">Nazwy elementów wywnioskowanych spójnej kolekcji</span><span class="sxs-lookup"><span data-stu-id="fe155-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="fe155-116">Od zainicjowania spójnej kolekcji w wielu przypadkach można wywnioskować nazwy elementów spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fe155-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="fe155-117">Na koniec kompilator ma dwie opcje `/refout` i `/refonly` tego formantu [odwołania generowanie zestawów](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="fe155-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="fe155-118">Wybór wersji języka</span><span class="sxs-lookup"><span data-stu-id="fe155-118">Language version selection</span></span>

<span data-ttu-id="fe155-119">Kompilator języka C# obsługuje 7.1 C# w programie Visual Studio 2017 wersji 15 ustęp 3 lub .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="fe155-119">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="fe155-120">Jednak 7.1 funkcje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="fe155-120">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="fe155-121">Aby włączyć funkcje 7.1, musisz zmienić ustawienie wersji języka dla projektu.</span><span class="sxs-lookup"><span data-stu-id="fe155-121">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="fe155-122">W programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fe155-122">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="fe155-123">Wybierz **kompilacji** i wybierz **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="fe155-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="fe155-124">Na liście rozwijanej wybierz **C# najnowsza wersja pomocnicza (Najnowsza wersja)**, lub wersji **C# 7.1** jak pokazano w następującym obrazu.</span><span class="sxs-lookup"><span data-stu-id="fe155-124">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="fe155-125">`latest` Wartość oznacza, że chcesz używać najnowszej wersji pomocniczej na bieżącym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fe155-125">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="fe155-126">`C# 7.1` Oznacza, że chcesz używać C# 7.1, nawet po udostępnieniu nowsze wersje pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="fe155-126">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![Ustawienie wersji językowej](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="fe155-128">Alternatywnie można edytować plik "csproj" i dodawania lub modyfikowania następujące wiersze:</span><span class="sxs-lookup"><span data-stu-id="fe155-128">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="fe155-129">Jeśli używasz programu Visual Studio IDE do aktualizacji plików csproj IDE tworzy osobne węzły dla każdej konfiguracji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe155-129">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="fe155-130">Będzie zazwyczaj wartość taka sama we wszystkich konfiguracjach kompilacji, ale należy jawnie ustaw dla każdej konfiguracji kompilacji, lub wybierz opcję "Wszystkie konfiguracje" po zmodyfikowaniu tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="fe155-130">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="fe155-131">W pliku csproj, pojawi się następujące:</span><span class="sxs-lookup"><span data-stu-id="fe155-131">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="fe155-132">Prawidłowe ustawienia dla `LangVersion` elementu są:</span><span class="sxs-lookup"><span data-stu-id="fe155-132">Valid settings for the `LangVersion` element are:</span></span>

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

<span data-ttu-id="fe155-133">Ciągi specjalne `default` i `latest` rozwiązania do najnowszej wersji językowych główne i pomocnicze odpowiednio zainstalowana na maszynie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe155-133">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="fe155-134">To ustawienie zapewnia oddzielenie instalowanie nowej wersji zestawu SDK i narzędzia w środowisku projektowania wybór uwzględnienie nowe funkcje językowe w projekcie.</span><span class="sxs-lookup"><span data-stu-id="fe155-134">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="fe155-135">Najnowsze narzędzia i zestawu SDK można zainstalować na komputerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe155-135">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="fe155-136">Każdy projekt można skonfigurować do korzystania z określonej wersji języka dla jego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe155-136">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="fe155-137">Asynchroniczne głównego</span><span class="sxs-lookup"><span data-stu-id="fe155-137">Async main</span></span>

<span data-ttu-id="fe155-138">*Async głównego* metoda pozwala na użycie `await` w Twojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="fe155-138">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="fe155-139">Wcześniej będzie potrzebny do zapisania:</span><span class="sxs-lookup"><span data-stu-id="fe155-139">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="fe155-140">Możesz teraz zapisać:</span><span class="sxs-lookup"><span data-stu-id="fe155-140">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="fe155-141">Jeśli program nie zwraca kod zakończenia, mogą zadeklarować `Main` metodę zwracającą <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="fe155-141">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="fe155-142">Możesz przeczytać dodatkowe informacje szczegółowe informacje w [async głównego](../programming-guide/main-and-command-args/index.md) w Podręczniku programowania.</span><span class="sxs-lookup"><span data-stu-id="fe155-142">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="fe155-143">Wyrażenia dosłowne domyślne</span><span class="sxs-lookup"><span data-stu-id="fe155-143">Default literal expressions</span></span>

<span data-ttu-id="fe155-144">Wyrażenia dosłowne domyślne są ulepszeniem wyrażenia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="fe155-144">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="fe155-145">Wyrażenia te zainicjować zmiennej przy użyciu wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="fe155-145">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="fe155-146">Gdzie należy wcześniej zapisać:</span><span class="sxs-lookup"><span data-stu-id="fe155-146">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="fe155-147">Teraz można pominąć inicjowanie typ po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="fe155-147">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="fe155-148">Użytkownik może dowiedzieć się więcej o to rozszerzenie w temacie C# przewodnik programowania w języku na [domyślna wartość wyrażenia](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fe155-148">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="fe155-149">To rozszerzenie zmieniają się także niektóre reguły analizy [słowo kluczowe default](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="fe155-149">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="fe155-150">Nazwy elementów wywnioskowanych spójnej kolekcji</span><span class="sxs-lookup"><span data-stu-id="fe155-150">Inferred tuple element names</span></span>

<span data-ttu-id="fe155-151">Ta funkcja jest mała rozszerzenie funkcji krotek wprowadzono w języku C# w wersji 7.0.</span><span class="sxs-lookup"><span data-stu-id="fe155-151">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="fe155-152">Wiele razy podczas inicjowania krotka zmiennych po prawej stronie przypisania są takie same jak nazwy, którą chcesz spójnej kolekcji elementów:</span><span class="sxs-lookup"><span data-stu-id="fe155-152">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="fe155-153">Nazwy elementów spójnej kolekcji można wywnioskować na podstawie zmiennych używaną do inicjalizacji spójna kolekcja znajdująca się w języku C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="fe155-153">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="fe155-154">Dowiedz się więcej o tej funkcji w [krotek](../tuples.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="fe155-154">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="fe155-155">Generowanie odwołania do zestawu</span><span class="sxs-lookup"><span data-stu-id="fe155-155">Reference assembly generation</span></span>

<span data-ttu-id="fe155-156">Dostępne są dwie opcje kompilatora nowe, które generują *tylko do odwołania zestawów*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) i [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="fe155-156">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="fe155-157">W połączonych tematach opisano te opcje i zestawy referencyjne bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="fe155-157">The linked topics explain these options and reference assemblies in more detail.</span></span>
