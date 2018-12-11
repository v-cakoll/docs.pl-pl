---
title: C#Program, struktura — Przewodnik po przykładzie C# języka
description: Dowiedz się, podstawowe bloki konstrukcyjne C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: de10cd000b4028a66ce6dd6f21e39c013e38ecd2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131030"
---
# <a name="program-structure"></a><span data-ttu-id="49060-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="49060-103">Program Structure</span></span>

<span data-ttu-id="49060-104">Kluczowe założenia organizacji w języku C# są ***programy***, ***przestrzenie nazw***, ***typy***, ***członków***, i ***zestawy***.</span><span class="sxs-lookup"><span data-stu-id="49060-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="49060-105">C# programy składają się z jednego lub więcej plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="49060-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="49060-106">Programy deklarują typy, które zawierają elementy członkowskie i mogą być organizowane w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="49060-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="49060-107">Klasy i interfejsy są przykłady typów.</span><span class="sxs-lookup"><span data-stu-id="49060-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="49060-108">Pola, metody, właściwości i zdarzenia są przykłady elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="49060-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="49060-109">Po skompilowaniu C# programy są fizycznie spakowane do zestawów.</span><span class="sxs-lookup"><span data-stu-id="49060-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="49060-110">Zestawy zwykle z rozszerzeniem pliku `.exe` lub `.dll`, w zależności od tego, czy zaimplementować ***aplikacje*** lub ***biblioteki***, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="49060-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="49060-111">Przykład deklaruje klasę o nazwie `Stack` w przestrzeni nazw o nazwie `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="49060-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="49060-112">W pełni kwalifikowana nazwa tej klasy to `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="49060-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="49060-113">Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o nazwie `Push` i `Pop`i klasę zagnieżdżoną o nazwie `Entry`.</span><span class="sxs-lookup"><span data-stu-id="49060-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="49060-114">`Entry` Dodatkowo klasa zawiera trzy elementy członkowskie: pole o nazwie `next`, pole o nazwie `data`i konstruktora.</span><span class="sxs-lookup"><span data-stu-id="49060-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="49060-115">Przy założeniu, że kod źródłowy przykładu znajduje się w pliku `acme.cs`, wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="49060-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="49060-116">kompiluje przykład jako biblioteki (kod bez `Main` punktu wejścia) i tworzy zestaw o nazwie `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="49060-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49060-117">Przykłady powyżej użyj `csc` wiersz polecenia C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="49060-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="49060-118">Tym kompilatorze jest plikiem wykonywalnym Windows.</span><span class="sxs-lookup"><span data-stu-id="49060-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="49060-119">Aby użyć C# na innych platformach, należy używać narzędzi dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49060-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="49060-120">Ekosystem platformy .NET Core używa `dotnet` interfejsu wiersza polecenia do zarządzania kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="49060-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="49060-121">Obejmuje to zarządzanie zależnościami i wywoływanie C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="49060-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="49060-122">Zobacz [w tym samouczku](../../core/tutorials/using-with-xplat-cli.md) pełny opis tych narzędzi na platformach obsługiwanych przez platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49060-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="49060-123">Zestawy zawierają kodu wykonywalnego w formie instrukcje języka pośredniego (IL) i informacji o symbolach w postaci metadanych.</span><span class="sxs-lookup"><span data-stu-id="49060-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="49060-124">Przed wykonaniem jego kodu IL w zestawie jest automatycznie konwertowany na kod specyficzny dla procesora przez kompilator just in Time (JIT) środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="49060-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="49060-125">Ponieważ zestaw jest samoopisujący jednostka zawierająca kod i metadanych funkcji, nie ma potrzeby dla `#include` dyrektyw i pliki nagłówkowe w języku C#.</span><span class="sxs-lookup"><span data-stu-id="49060-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="49060-126">Typy publiczne i elementów członkowskich znajdujących się w określonym zestawie są udostępniane w programie C# poprzez odwołanie do tego zestawu podczas kompilowania kodu programu.</span><span class="sxs-lookup"><span data-stu-id="49060-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="49060-127">Na przykład ten program używa `Acme.Collections.Stack` klasy z `acme.dll` zestawu:</span><span class="sxs-lookup"><span data-stu-id="49060-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="49060-128">Jeśli program jest przechowywany w pliku `example.cs`, gdy `example.cs` jest kompilowany, zestawu acme.dll można odwoływać się za pomocą /r — opcja kompilatora:</span><span class="sxs-lookup"><span data-stu-id="49060-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="49060-129">Spowoduje to utworzenie pliku wykonywalnego zestaw o nazwie `example.exe`, który, po uruchomieniu tworzy dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="49060-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="49060-130">C# umożliwia tekst źródłowy program ma być przechowywany w kilku plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="49060-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="49060-131">Wielu plików języka C# program jest skompilowany, wszystkie pliki źródłowe są przetwarzane razem, gdy pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — model jest tak, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem.</span><span class="sxs-lookup"><span data-stu-id="49060-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="49060-132">Deklaracje przechodzenia do przodu nigdy nie są wymagane w języku C#, ponieważ z nielicznymi wyjątkami, kolejności deklaracji jest niewielka.</span><span class="sxs-lookup"><span data-stu-id="49060-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="49060-133">C# nie istnieje limit pliku źródłowego do deklarowania tylko jeden typ publiczny ani nie wymaga nazwy pliku źródłowego, aby dopasować typ zadeklarowany w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="49060-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49060-134">[Poprzednie](index.md)
>[dalej](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="49060-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>