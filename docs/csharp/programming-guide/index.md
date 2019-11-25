---
title: Przewodnik programowania w języku C#
ms.date: 05/02/2017
f1_keywords:
- cs.langref
helpviewer_keywords:
- reference tables [C#]
- C# language, programming guide
- Visual C#, programming concepts
- C# language, concepts
ms.assetid: ac0f23a2-6bf3-4077-be99-538ae5fd3bc5
ms.openlocfilehash: ad4e953941e189e6ed9baefb6cb07e7955000c7f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283119"
---
# <a name="c-programming-guide"></a><span data-ttu-id="51b19-102">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="51b19-102">C# programming guide</span></span>

<span data-ttu-id="51b19-103">Ta sekcja zawiera szczegółowe informacje o kluczowych funkcjach języka C# oraz o funkcjach tego języka dostępnych przez platformę .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51b19-103">This section provides detailed information on key C# language features and features accessible to C# through the .NET Framework.</span></span>  
  
 <span data-ttu-id="51b19-104">W większej części tej sekcji przyjęto założenie, że masz już pewną wiedzę na temat języka C# i ogólnie na temat programowania.</span><span class="sxs-lookup"><span data-stu-id="51b19-104">Most of this section assumes that you already know something about C# and general programming concepts.</span></span> <span data-ttu-id="51b19-105">Jeśli jesteś kompletnym początkującym z programowaniem lub C#programem, możesz chcieć odwiedzić [wprowadzenie do C# samouczków](../tutorials/intro-to-csharp/index.md) lub [samouczka platformy .NET w przeglądarce](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1), gdzie nie jest wymagana wcześniejsza wiedza o programowaniu.</span><span class="sxs-lookup"><span data-stu-id="51b19-105">If you are a complete beginner with programming or with C#, you might want to visit the [Introduction to C# Tutorials](../tutorials/intro-to-csharp/index.md) or [.NET In-Browser Tutorial](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1), where no prior programming knowledge is required.</span></span>  
  
 <span data-ttu-id="51b19-106">Aby uzyskać informacje dotyczące określonych słów kluczowych, operatorów i dyrektyw preprocesora, zobacz sekcję [Dokumentacja języka C#](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="51b19-106">For information about specific keywords, operators and preprocessor directives, see [C# Reference](../language-reference/index.md).</span></span> <span data-ttu-id="51b19-107">Informacje o specyfikacji języka C# można znaleźć w temacie [Specyfikacja języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="51b19-107">For information about the C# Language Specification, see [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>  
  
## <a name="program-sections"></a><span data-ttu-id="51b19-108">Sekcje programu</span><span class="sxs-lookup"><span data-stu-id="51b19-108">Program sections</span></span>

[<span data-ttu-id="51b19-109">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="51b19-109">Inside a C# Program</span></span>](./inside-a-program/index.md)  
  
[<span data-ttu-id="51b19-110">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="51b19-110">Main() and Command-Line Arguments</span></span>](./main-and-command-args/index.md)  

## <a name="language-sections"></a><span data-ttu-id="51b19-111">Sekcje języka</span><span class="sxs-lookup"><span data-stu-id="51b19-111">Language Sections</span></span>

[<span data-ttu-id="51b19-112">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="51b19-112">Statements, Expressions, and Operators</span></span>](./statements-expressions-operators/index.md)  

 [<span data-ttu-id="51b19-113">Typy</span><span class="sxs-lookup"><span data-stu-id="51b19-113">Types</span></span>](./types/index.md)  

 [<span data-ttu-id="51b19-114">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="51b19-114">Classes and Structs</span></span>](./classes-and-structs/index.md)  
  
 [<span data-ttu-id="51b19-115">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="51b19-115">Interfaces</span></span>](./interfaces/index.md)  

 [<span data-ttu-id="51b19-116">Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="51b19-116">Enumeration Types</span></span>](./enumeration-types.md)  
  
 [<span data-ttu-id="51b19-117">Delegaty</span><span class="sxs-lookup"><span data-stu-id="51b19-117">Delegates</span></span>](./delegates/index.md)  

 [<span data-ttu-id="51b19-118">Tablice</span><span class="sxs-lookup"><span data-stu-id="51b19-118">Arrays</span></span>](./arrays/index.md)  
  
 [<span data-ttu-id="51b19-119">Ciągi</span><span class="sxs-lookup"><span data-stu-id="51b19-119">Strings</span></span>](./strings/index.md)  
  
 [<span data-ttu-id="51b19-120">Właściwości</span><span class="sxs-lookup"><span data-stu-id="51b19-120">Properties</span></span>](./classes-and-structs/properties.md)  
  
 [<span data-ttu-id="51b19-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="51b19-121">Indexers</span></span>](./indexers/index.md)  
  
 [<span data-ttu-id="51b19-122">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="51b19-122">Events</span></span>](./events/index.md)  
  
 [<span data-ttu-id="51b19-123">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="51b19-123">Generics</span></span>](./generics/index.md)  
  
 [<span data-ttu-id="51b19-124">Iteratory</span><span class="sxs-lookup"><span data-stu-id="51b19-124">Iterators</span></span>](./concepts/iterators.md)
  
 [<span data-ttu-id="51b19-125">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="51b19-125">LINQ Query Expressions</span></span>](../linq/index.md)  
  
 [<span data-ttu-id="51b19-126">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="51b19-126">Lambda Expressions</span></span>](./statements-expressions-operators/lambda-expressions.md)  
  
 [<span data-ttu-id="51b19-127">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="51b19-127">Namespaces</span></span>](./namespaces/index.md)  
  
 [<span data-ttu-id="51b19-128">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="51b19-128">Unsafe Code and Pointers</span></span>](./unsafe-code-pointers/index.md)  
  
 [<span data-ttu-id="51b19-129">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="51b19-129">XML Documentation Comments</span></span>](./xmldoc/index.md)  
  
## <a name="platform-sections"></a><span data-ttu-id="51b19-130">Sekcje platformy</span><span class="sxs-lookup"><span data-stu-id="51b19-130">Platform Sections</span></span>

 [<span data-ttu-id="51b19-131">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="51b19-131">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
  
 [<span data-ttu-id="51b19-132">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="51b19-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
  
 [<span data-ttu-id="51b19-133">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="51b19-133">Attributes</span></span>](./concepts/attributes/index.md)  
  
 [<span data-ttu-id="51b19-134">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="51b19-134">Collections</span></span>](./concepts/collections.md)  
  
 [<span data-ttu-id="51b19-135">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="51b19-135">Exceptions and Exception Handling</span></span>](./exceptions/index.md)  
  
 [<span data-ttu-id="51b19-136">System plików i Rejestr (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="51b19-136">File System and the Registry (C# Programming Guide)</span></span>](./file-system/index.md)  
  
 [<span data-ttu-id="51b19-137">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="51b19-137">Interoperability</span></span>](./interop/index.md)  
  
 [<span data-ttu-id="51b19-138">Odbicie</span><span class="sxs-lookup"><span data-stu-id="51b19-138">Reflection</span></span>](./concepts/reflection.md)  
  
## <a name="see-also"></a><span data-ttu-id="51b19-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51b19-139">See also</span></span>

- [<span data-ttu-id="51b19-140">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="51b19-140">C# Reference</span></span>](../language-reference/index.md)
