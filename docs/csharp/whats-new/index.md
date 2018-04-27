---
title: Nowości w języku C# — przewodnik C#
description: Jak ewoluuje w języku C#
keywords: C#, najnowsze funkcje nowości, Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: d66f835d57f43d2016d3b20e2205e0052d064acb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="whats-new-in-c"></a><span data-ttu-id="6da82-104">Nowości w języku C#</span><span class="sxs-lookup"><span data-stu-id="6da82-104">What's new in C#</span></span> #

<span data-ttu-id="6da82-105">Ta strona zawiera plan nowych funkcji każdego wydania programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="6da82-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="6da82-106">Poniższe linki udostępniają szczegółowe informacje o głównych funkcje dodane w poszczególnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="6da82-106">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6da82-107">W języku C# zależy od typów i metod w *biblioteki standardowej* dla niektórych funkcji.</span><span class="sxs-lookup"><span data-stu-id="6da82-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="6da82-108">Przykładem jest wyjątek podczas przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6da82-108">One example is exception processing.</span></span> <span data-ttu-id="6da82-109">Każdy `throw` instrukcja lub wyrażenie zaznaczono zapewnienie obiekt został zgłoszony jest pochodną <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6da82-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="6da82-110">Podobnie co `catch` jest sprawdzane pod kątem upewnij się, że typ jest przechwycono pochodzi od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6da82-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="6da82-111">Każda wersja może dodać nowe wymagania.</span><span class="sxs-lookup"><span data-stu-id="6da82-111">Each version may add new requirements.</span></span> <span data-ttu-id="6da82-112">Aby korzystać z najnowszych funkcji języka w środowiskach starsze, może być konieczne zainstalować określone biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6da82-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="6da82-113">Te zależności są opisane na stronie dla każdej określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="6da82-113">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="6da82-114">Użytkownik może dowiedzieć się więcej o [relacje między języka i biblioteki](relationships-between-language-and-library.md) w tle na tę zależność.</span><span class="sxs-lookup"><span data-stu-id="6da82-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="6da82-115">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="6da82-115">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="6da82-116">Ta strona zawiera opis najnowszych funkcji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="6da82-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="6da82-117">Jest obecnie dostępna w C# 7.2 [programu Visual Studio 2017 wersji 15,5 cala](https://www.visualstudio.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="6da82-117">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="6da82-118">[C# 7.1](csharp-7-1.md):</span><span class="sxs-lookup"><span data-stu-id="6da82-118">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="6da82-119">Ta strona zawiera opis funkcji w języku C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="6da82-119">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="6da82-120">Te funkcje zostały dodane w [programu Visual Studio 2017 wersji 15 ustęp 3](https://www.visualstudio.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="6da82-120">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="6da82-121">[C# 7.0](csharp-7.md):</span><span class="sxs-lookup"><span data-stu-id="6da82-121">[C# 7.0](csharp-7.md):</span></span>
    - <span data-ttu-id="6da82-122">Ta strona opisano funkcje dodane w języku C# w wersji 7.0.</span><span class="sxs-lookup"><span data-stu-id="6da82-122">This page describes the features added in C# 7.0.</span></span> <span data-ttu-id="6da82-123">Te funkcje zostały dodane w [programu Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) i [.NET Core 1.0](../../core/whats-new/index.md) i nowsze</span><span class="sxs-lookup"><span data-stu-id="6da82-123">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="6da82-124">[C# 6](csharp-6.md):</span><span class="sxs-lookup"><span data-stu-id="6da82-124">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="6da82-125">Ta strona zawiera opis funkcji, które zostały dodane w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="6da82-125">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="6da82-126">Te funkcje są dostępne w programie Visual Studio 2015 dla deweloperów systemu Windows, a następnie na .NET Core 1.0 dla deweloperów eksploracji C# w macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="6da82-126">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="6da82-127">[Obsługa wielu Platform](../../core/index.md):</span><span class="sxs-lookup"><span data-stu-id="6da82-127">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="6da82-128">C# za pomocą obsługi .NET Core działa na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="6da82-128">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="6da82-129">Jeśli interesuje Cię w trakcie C# macOS lub jedną z wielu obsługiwane dystrybucje systemu Linux, Dowiedz się więcej na temat platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6da82-129">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="6da82-130">Poprzednie wersje</span><span class="sxs-lookup"><span data-stu-id="6da82-130">Previous Versions</span></span>
<span data-ttu-id="6da82-131">Poniższe listy kluczy funkcje, które zostały wprowadzone w poprzednich wersjach programu w języku C# i Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="6da82-131">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="6da82-132">Visual Studio .NET 2013:</span><span class="sxs-lookup"><span data-stu-id="6da82-132">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="6da82-133">Ta wersja programu Visual Studio zawiera poprawki błędów, wydajności i wersji zapoznawczych platformy technologię platformy kompilatora .NET ("Roslyn"), które stały się zestawu SDK platformy kompilatora .NET<!--Link to ../roslyn/index.md-->.</span><span class="sxs-lookup"><span data-stu-id="6da82-133">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="6da82-134">C# 5, programu Visual Studio .NET 2012:</span><span class="sxs-lookup"><span data-stu-id="6da82-134">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="6da82-135">`Async` / `await`, a [informacje o wywołującym](../programming-guide/concepts/caller-information.md) atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6da82-135">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="6da82-136">C# 4, programu Visual Studio .NET 2010:</span><span class="sxs-lookup"><span data-stu-id="6da82-136">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="6da82-137">`Dynamic`, [argumentami nazwanymi](../programming-guide/classes-and-structs/named-and-optional-arguments.md), następujące parametry opcjonalne i rodzajowy [Kowariancja i ma przeciwwskazań wariancji](../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="6da82-137">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="6da82-138">C# 3, programu Visual Studio .NET 2008:</span><span class="sxs-lookup"><span data-stu-id="6da82-138">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="6da82-139">Inicjatory obiektów i kolekcji, wyrażenia lambda, metody rozszerzenia, typy anonimowe, automatyczne właściwości, lokalnego `var` wnioskowanie, i [języka zapytań zintegrowanym (LINQ)](../programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="6da82-139">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="6da82-140">C# 2, Visual Studio .NET 2005:</span><span class="sxs-lookup"><span data-stu-id="6da82-140">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="6da82-141">Metody anonimowe, ogólne, typy dopuszczające wartości zerowe, Iteratory/yield `static` klasy i Kowariancja i ma przeciwwskazań wariancji dla delegatów.</span><span class="sxs-lookup"><span data-stu-id="6da82-141">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="6da82-142">C# 1.1, Visual Studio .NET 2003:</span><span class="sxs-lookup"><span data-stu-id="6da82-142">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="6da82-143">`#line` komentarze w dokumencie pragma i xml.</span><span class="sxs-lookup"><span data-stu-id="6da82-143">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="6da82-144">C# 1, Visual Studio .NET 2002:</span><span class="sxs-lookup"><span data-stu-id="6da82-144">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="6da82-145">Pierwszą wersję [C#](../csharp.md).</span><span class="sxs-lookup"><span data-stu-id="6da82-145">The first release of [C#](../csharp.md).</span></span>   
