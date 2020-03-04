---
title: C#Struktura programu — Przewodnik po C# języku
description: Zapoznaj się z podstawowymi blokami konstrukcyjnymi C# programu
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159120"
---
# <a name="program-structure"></a><span data-ttu-id="88941-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="88941-103">Program Structure</span></span>

<span data-ttu-id="88941-104">Kluczowe koncepcje organizacyjne C# w programie to ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***.</span><span class="sxs-lookup"><span data-stu-id="88941-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="88941-105">C#programy składają się z co najmniej jednego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="88941-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="88941-106">Programy deklarują typy, które zawierają składowe i mogą być zorganizowane w przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="88941-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="88941-107">Klasy i interfejsy są przykładami typów.</span><span class="sxs-lookup"><span data-stu-id="88941-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="88941-108">Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="88941-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="88941-109">Gdy C# programy są kompilowane, są fizycznie spakowane w zestawy.</span><span class="sxs-lookup"><span data-stu-id="88941-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="88941-110">Zestawy zazwyczaj mają rozszerzenie pliku `.exe` lub `.dll`, w zależności od tego, czy implementują odpowiednio ***aplikacje*** lub ***biblioteki***.</span><span class="sxs-lookup"><span data-stu-id="88941-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="88941-111">Można utworzyć projekt biblioteki o nazwie *Acme* przy użyciu polecenia `dotnet new`:</span><span class="sxs-lookup"><span data-stu-id="88941-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="88941-112">W tym projekcie Zadeklaruj klasę o nazwie `Stack` w przestrzeni nazw o nazwie `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="88941-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="88941-113">W pełni kwalifikowana nazwa tej klasy jest `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="88941-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="88941-114">Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o nazwie `Push` i `Pop`oraz zagnieżdżoną klasę o nazwie `Entry`.</span><span class="sxs-lookup"><span data-stu-id="88941-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="88941-115">Klasa `Entry` dodatkowo zawiera trzy elementy członkowskie: pole o nazwie `next`, pole o nazwie `data`i Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="88941-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="88941-116">Polecenie:</span><span class="sxs-lookup"><span data-stu-id="88941-116">The command:</span></span>

```console
dotnet build 
```

<span data-ttu-id="88941-117">kompiluje przykład jako bibliotekę (kod bez punktu wejścia `Main`) i tworzy zestaw o nazwie `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="88941-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="88941-118">Zestawy zawierają kod wykonywalny w postaci instrukcji języka pośredniego (IL) i informacji symbolicznych w formie metadanych.</span><span class="sxs-lookup"><span data-stu-id="88941-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="88941-119">Przed wykonaniem, kompilator just-in-Time (JIT) środowiska uruchomieniowego języka wspólnego .NET konwertuje kod IL w zestawie na kod specyficzny dla procesora.</span><span class="sxs-lookup"><span data-stu-id="88941-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="88941-120">Ponieważ zestaw jest samoopisującą się jednostką funkcji obejmujących zarówno kod, jak i metadane, nie ma potrzeby stosowania dyrektyw `#include` i plików nagłówkowych w programie C#.</span><span class="sxs-lookup"><span data-stu-id="88941-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="88941-121">Typy publiczne i składowe zawarte w określonym zestawie są udostępniane w C# programie po prostu przez odwołanie się do tego zestawu podczas kompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="88941-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="88941-122">Na przykład ten program używa klasy `Acme.Collections.Stack` z zestawu `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="88941-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="88941-123">Plik *csproj* dla projektu poprzedniego programu musi zawierać węzeł odniesienia dla kompilatora, C# aby rozpoznać odwołania do klas w zestawie `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="88941-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="88941-124">Po tym dodaniu `dotnet build` tworzy zestaw wykonywalny o nazwie `example.exe`, który w przypadku uruchamiania generuje dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="88941-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="88941-125">C#zezwala na przechowywanie tekstu źródłowego programu w kilku plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="88941-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="88941-126">W przypadku kompilowania programu C# z obsługą wielu plików wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — jest to tak samo, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem.</span><span class="sxs-lookup"><span data-stu-id="88941-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="88941-127">Deklaracje przesyłania dalej nie są C# nigdy niewymagane w programie, dlatego z kilkoma wyjątkami porządek deklaracji jest nieważny.</span><span class="sxs-lookup"><span data-stu-id="88941-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="88941-128">C#nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga, aby nazwa pliku źródłowego była zgodna z typem zadeklarowanym w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="88941-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="88941-129">[Poprzednie](index.md)
>[dalej](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="88941-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
