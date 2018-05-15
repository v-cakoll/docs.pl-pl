---
title: C# Program struktury — samouczek języka C#
description: Dowiedz się, podstawowe bloki konstrukcyjne program C#
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: dee24077f9f6287780320d979c44aef5230be81e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="program-structure"></a><span data-ttu-id="bdfbe-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="bdfbe-103">Program Structure</span></span>

<span data-ttu-id="bdfbe-104">Podstawowe pojęcia organizacji w języku C# to ***programy***, ***przestrzeni nazw***, ***typy***, ***członków***, i ***zestawy***.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="bdfbe-105">C# programy składają się z co najmniej jeden plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="bdfbe-106">Programy deklaruj typy, które zawierają elementy członkowskie i można organizować w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="bdfbe-107">Klasy i interfejsy są przykłady typów.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="bdfbe-108">Pola, metody, właściwości i zdarzenia są przykłady elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="bdfbe-109">Gdy są kompilowane programów C#, są one fizycznie umieszczone w zestawy.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="bdfbe-110">Zestawy zwykle mają rozszerzenia pliku `.exe` lub `.dll`w zależności od tego, czy wdrożenie ***aplikacji*** lub ***biblioteki***odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="bdfbe-111">Przykład deklaruje klasę o nazwie `Stack` w obszarze nazw o nazwie `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="bdfbe-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="bdfbe-112">W pełni kwalifikowana nazwa ta klasa jest `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="bdfbe-113">Klasa zawiera kilka elementów członkowskich: pola o nazwie `top`, dwie metody o nazwie `Push` i `Pop`i zagnieżdżone klasy o nazwie `Entry`.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="bdfbe-114">`Entry` Dalsze klasa zawiera trzy elementy członkowskie: pola o nazwie `next`, pole o nazwie `data`ani konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="bdfbe-115">Przy założeniu, że kod źródłowy przykładu znajduje się w pliku `acme.cs`, wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="bdfbe-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="bdfbe-116">kompiluje przykład jako biblioteki (code bez `Main` punktu wejścia) i tworzy zestaw o nazwie `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdfbe-117">Przykłady powyżej użyj `csc` jako kompilatora wiersza polecenia języka C#.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="bdfbe-118">Ten kompilator jest wykonywalne systemu windows.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-118">This compiler is a windows executable.</span></span> <span data-ttu-id="bdfbe-119">Aby użyć C# na innych platformach, należy używać narzędzi dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="bdfbe-120">Używa ekosystemu platformy .NET Core `dotnet` interfejsu wiersza polecenia do zarządzania kompilacji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="bdfbe-121">W tym zarządzanie zależności i wywoływanie kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="bdfbe-122">Zobacz [w tym samouczku](../../core/tutorials/using-with-xplat-cli.md) pełen opis tych narzędzi na platformach obsługiwanych przez oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="bdfbe-123">Zestaw nie zawiera kodu wykonywalnego w postaci instrukcji w języku pośrednim (IL) i symboliczne informacje w postaci metadanych.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="bdfbe-124">Przed wykonaniem jego kod IL w zestawie jest automatycznie konwertowany do specyficznych dla procesora kodu za pomocą kompilatora just in Time (JIT) aparatu plików wykonywalnych języka wspólnego .NET.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="bdfbe-125">Ponieważ zestaw jest samoopisujące jednostka zawierająca kod i metadanych funkcji, nie jest wymagane dla `#include` dyrektywy i pliki nagłówkowe w języku C#.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="bdfbe-126">Typy publiczne i elementów członkowskich zawartych w określonym zestawie stają się dostępne w programie C# za pomocą odwołania do tego zestawu, w przypadku kompilowania kodu programu.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="bdfbe-127">Na przykład ten program używa `Acme.Collections.Stack` klasę z `acme.dll` zestawu:</span><span class="sxs-lookup"><span data-stu-id="bdfbe-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="bdfbe-128">Jeśli program jest przechowywany w pliku `example.cs`, gdy `example.cs` jest skompilowany, zestawu acme.dll można odwoływać się przy użyciu /r — opcja kompilatora:</span><span class="sxs-lookup"><span data-stu-id="bdfbe-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="bdfbe-129">Spowoduje to utworzenie pliku wykonywalnego zestawu o nazwie `example.exe`, która po uruchomieniu tworzy dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bdfbe-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="bdfbe-130">C# zezwala na tekst źródłowy program ma być przechowywana w kilka plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="bdfbe-131">Podczas kompilowania wielu plików programu C#, są ze sobą przetwarzanie wszystkich plików źródłowych i plików źródłowych za darmo można odwoływać się siebie nawzajem — koncepcyjnie, są tak, jakby wszystkie pliki źródłowe zostały połączone w jeden plik dużych przed przetworzeniem.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="bdfbe-132">Deklaracje do przodu nigdy nie są potrzebne w języku C#, ponieważ z nielicznymi wyjątkami kolejności deklaracji jest niewielka.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="bdfbe-133">C# nie istnieje limit pliku źródłowego do deklarowania tylko jeden typ publiczny, ani nie wymaga nazwy pliku źródłowego, aby dopasować typ zadeklarowany w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="bdfbe-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="bdfbe-134">[Poprzednie](index.md)
[dalej](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="bdfbe-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
