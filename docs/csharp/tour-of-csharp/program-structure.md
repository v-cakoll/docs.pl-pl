---
title: Struktura programu C# — zwiedzanie języka Języka C#
description: Poznaj podstawowe elementy konstrukcyjne programu C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156834"
---
# <a name="program-structure"></a><span data-ttu-id="f5a62-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="f5a62-103">Program Structure</span></span>

<span data-ttu-id="f5a62-104">Kluczowe pojęcia organizacyjne w języku C# to ***programy,*** ***przestrzenie nazw,*** ***typy,*** ***elementy członkowskie***i ***zestawy.***</span><span class="sxs-lookup"><span data-stu-id="f5a62-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="f5a62-105">Programy C# składają się z jednego lub więcej plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="f5a62-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="f5a62-106">Programy deklarują typy, które zawierają elementy członkowskie i mogą być zorganizowane w przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="f5a62-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="f5a62-107">Klasy i interfejsy są przykładami typów.</span><span class="sxs-lookup"><span data-stu-id="f5a62-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="f5a62-108">Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f5a62-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="f5a62-109">Gdy programy C# są kompilowane, są fizycznie pakowane do zestawów.</span><span class="sxs-lookup"><span data-stu-id="f5a62-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="f5a62-110">Zestawy zazwyczaj mają rozszerzenie `.exe` `.dll`pliku lub , w zależności od tego, czy implementują ***aplikacje*** lub ***biblioteki***, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f5a62-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="f5a62-111">Za pomocą `dotnet new` polecenia można utworzyć projekt biblioteki o nazwie *acme:*</span><span class="sxs-lookup"><span data-stu-id="f5a62-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="f5a62-112">W tym projekcie deklaruj klasę o nazwie `Stack` w obszarze nazw o nazwie: `Acme.Collections`</span><span class="sxs-lookup"><span data-stu-id="f5a62-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="f5a62-113">W pełni kwalifikowaną nazwą `Acme.Collections.Stack`tej klasy jest .</span><span class="sxs-lookup"><span data-stu-id="f5a62-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="f5a62-114">Klasa zawiera kilka elementów członkowskich: pole `top`o `Push` `Pop`nazwie , dwie metody `Entry`o nazwie i , i zagnieżdżonych klasy o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f5a62-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="f5a62-115">Klasa `Entry` zawiera dalej trzy elementy `next`członkowskie: pole `data`o nazwie , pole o nazwie i konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f5a62-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="f5a62-116">Polecenie:</span><span class="sxs-lookup"><span data-stu-id="f5a62-116">The command:</span></span>

```console
dotnet build
```

<span data-ttu-id="f5a62-117">kompiluje przykład jako bibliotekę `Main` (kod bez punktu wejścia) `acme.dll`i tworzy zestaw o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f5a62-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="f5a62-118">Zestawy zawierają kod wykonywalny w postaci instrukcji il (Intermediate Language) i symboliczne informacje w postaci metadanych.</span><span class="sxs-lookup"><span data-stu-id="f5a62-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="f5a62-119">Przed jego wykonaniem kompilator Just-In-Time (JIT) programu .NET Common Language Runtime konwertuje kod IL w zestawie na kod specyficzny dla procesora.</span><span class="sxs-lookup"><span data-stu-id="f5a62-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="f5a62-120">Ponieważ zestaw jest samoopisującą się jednostką funkcji zawierającą zarówno kod, jak `#include` i metadane, nie ma potrzeby stosowania dyrektyw i plików nagłówkowych w języku C#.</span><span class="sxs-lookup"><span data-stu-id="f5a62-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="f5a62-121">Typy publiczne i elementy członkowskie zawarte w określonym zestawie są udostępniane w programie C# po prostu odwołując się do tego zestawu podczas kompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="f5a62-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="f5a62-122">Na przykład ten program `Acme.Collections.Stack` używa `acme.dll` klasy z zestawu:</span><span class="sxs-lookup"><span data-stu-id="f5a62-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="f5a62-123">Plik *csproj* dla projektu poprzedniego programu musi zawierać węzeł odniesienia dla kompilatora C#, `acme.dll` aby rozpoznać odwołania do klas w zestawie:</span><span class="sxs-lookup"><span data-stu-id="f5a62-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="f5a62-124">Po tym `dotnet build` dodaniu tworzy zestaw `example.exe`wykonywalny o nazwie , który po uruchomieniu generuje dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f5a62-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="f5a62-125">C# umożliwia tekst źródłowy programu mają być przechowywane w kilku plikach źródłowych.</span><span class="sxs-lookup"><span data-stu-id="f5a62-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="f5a62-126">Gdy program C# z wieloma plikami jest skompilowany, wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie — koncepcyjnie, to tak, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem.</span><span class="sxs-lookup"><span data-stu-id="f5a62-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="f5a62-127">Deklaracje do przodu nigdy nie są potrzebne w języku C#, ponieważ z nielicznymi wyjątkami kolejność deklaracji jest nieistotna.</span><span class="sxs-lookup"><span data-stu-id="f5a62-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="f5a62-128">C# nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga nazwy pliku źródłowego, aby dopasować typ zadeklarowany w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f5a62-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f5a62-129">[Poprzedni](index.md)
>[następny](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="f5a62-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
