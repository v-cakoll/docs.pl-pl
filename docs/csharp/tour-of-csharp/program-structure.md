---
title: C#Struktura programu — Przewodnik po C# języku
description: Zapoznaj się z podstawowymi blokami konstrukcyjnymi C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5102c72d68108f698a0456b9c14e6713778f4325
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834156"
---
# <a name="program-structure"></a><span data-ttu-id="f9dfc-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="f9dfc-103">Program Structure</span></span>

<span data-ttu-id="f9dfc-104">Kluczowe koncepcje organizacyjne C# w programie to ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="f9dfc-105">C#programy składają się z co najmniej jednego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="f9dfc-106">Programy deklarują typy, które zawierają składowe i mogą być zorganizowane w przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="f9dfc-107">Klasy i interfejsy są przykładami typów.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="f9dfc-108">Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="f9dfc-109">Gdy C# programy są kompilowane, są fizycznie spakowane do zestawów.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="f9dfc-110">Zestawy zazwyczaj mają rozszerzenie pliku `.exe` lub `.dll`, w zależności od tego, czy implementują odpowiednio ***aplikacje*** lub ***biblioteki***.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="f9dfc-111">Przykład deklaruje klasę o nazwie `Stack` w przestrzeni nazw o nazwie `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="f9dfc-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="f9dfc-112">W pełni kwalifikowana nazwa tej klasy jest `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="f9dfc-113">Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o nazwie `Push` i `Pop`oraz zagnieżdżoną klasę o nazwie `Entry`.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="f9dfc-114">Klasa `Entry` dodatkowo zawiera trzy elementy członkowskie: pole o nazwie `next`, pole o nazwie `data`i Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="f9dfc-115">Przy założeniu, że kod źródłowy przykładu jest przechowywany w pliku `acme.cs`, wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="f9dfc-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```console
csc /t:library acme.cs
```

<span data-ttu-id="f9dfc-116">kompiluje przykład jako bibliotekę (kod bez punktu wejścia `Main`) i tworzy zestaw o nazwie `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9dfc-117">Powyższe przykłady używają `csc` jako kompilator wiersza C# polecenia.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="f9dfc-118">Ten kompilator jest plikiem wykonywalnym systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="f9dfc-119">Aby korzystać C# z różnych platform, należy użyć narzędzi dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="f9dfc-120">Ekosystem platformy .NET Core używa interfejsu wiersza polecenia `dotnet` do zarządzania kompilacjami w wierszu poleceń.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="f9dfc-121">Obejmuje to zarządzanie zależnościami i wywoływanie C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="f9dfc-122">Zapoznaj się z [tym samouczkiem](../../core/tutorials/using-with-xplat-cli.md) , aby zapoznać się z pełnymi opisami tych narzędzi na platformach obsługiwanych przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="f9dfc-123">Zestawy zawierają kod wykonywalny w postaci instrukcji języka pośredniego (IL) i informacji symbolicznych w formie metadanych.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="f9dfc-124">Przed wykonaniem kod IL w zestawie jest automatycznie konwertowany na kod specyficzny dla procesora przez kompilator just-in-Time (JIT) środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="f9dfc-125">Ponieważ zestaw jest samoopisującą się jednostką funkcji obejmujących zarówno kod, jak i metadane, nie ma potrzeby stosowania dyrektyw `#include` i plików nagłówkowych w programie C#.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="f9dfc-126">Typy publiczne i składowe zawarte w określonym zestawie są udostępniane w C# programie po prostu przez odwołanie się do tego zestawu podczas kompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="f9dfc-127">Na przykład ten program używa klasy `Acme.Collections.Stack` z zestawu `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="f9dfc-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="f9dfc-128">Jeśli program jest przechowywany w pliku `example.cs`, podczas kompilowania `example.cs`, można odwoływać się do zestawu Acme. dll przy użyciu/r opcji kompilatora:</span><span class="sxs-lookup"><span data-stu-id="f9dfc-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```console
csc /r:acme.dll example.cs
```

<span data-ttu-id="f9dfc-129">Spowoduje to utworzenie zestawu wykonywalnego o nazwie `example.exe`, który w przypadku uruchamiania generuje dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f9dfc-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="f9dfc-130">C#zezwala na przechowywanie tekstu źródłowego programu w kilku plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="f9dfc-131">W przypadku kompilowania programu C# z obsługą wielu plików wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — jest to tak samo, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="f9dfc-132">Deklaracje przesyłania dalej nie są C# nigdy niewymagane w programie, w związku z czym z kilkoma wyjątkami, zamówienie deklaracji jest nieważne.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="f9dfc-133">C#nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga, aby nazwa pliku źródłowego była zgodna z typem zadeklarowanym w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f9dfc-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f9dfc-134">[Poprzedni](index.md)
>[Następny](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="f9dfc-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
