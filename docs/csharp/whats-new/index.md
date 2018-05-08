---
title: Nowości w języku C# — przewodnik C#
description: Jak ewoluuje w języku C#
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 3fc42809943b10d09d59780576dd9768d9e16ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c"></a>Nowości w języku C# #

Ta strona zawiera plan nowych funkcji każdego wydania programu w języku C#. Poniższe linki udostępniają szczegółowe informacje o głównych funkcje dodane w poszczególnych wersjach.

> [!IMPORTANT]
> W języku C# zależy od typów i metod w *biblioteki standardowej* dla niektórych funkcji. Przykładem jest wyjątek podczas przetwarzania. Każdy `throw` instrukcja lub wyrażenie zaznaczono zapewnienie obiekt został zgłoszony jest pochodną <xref:System.Exception>. Podobnie co `catch` jest sprawdzane pod kątem upewnij się, że typ jest przechwycono pochodzi od <xref:System.Exception>. Każda wersja może dodać nowe wymagania. Aby korzystać z najnowszych funkcji języka w środowiskach starsze, może być konieczne zainstalować określone biblioteki. Te zależności są opisane na stronie dla każdej określonej wersji. Użytkownik może dowiedzieć się więcej o [relacje między języka i biblioteki](relationships-between-language-and-library.md) w tle na tę zależność. 


* [C# 7.2](csharp-7-2.md):
    - Ta strona zawiera opis najnowszych funkcji w języku C#. Jest obecnie dostępna w C# 7.2 [programu Visual Studio 2017 wersji 15,5 cala](https://www.visualstudio.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).

* [C# 7.1](csharp-7-1.md):
    - Ta strona zawiera opis funkcji w języku C# 7.1. Te funkcje zostały dodane w [programu Visual Studio 2017 wersji 15 ustęp 3](https://www.visualstudio.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).

* [C# 7.0](csharp-7.md):
    - Ta strona opisano funkcje dodane w języku C# w wersji 7.0. Te funkcje zostały dodane w [programu Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) i [.NET Core 1.0](../../core/whats-new/index.md) i nowsze
     
* [C# 6](csharp-6.md):
    - Ta strona zawiera opis funkcji, które zostały dodane w języku C# 6. Te funkcje są dostępne w programie Visual Studio 2015 dla deweloperów systemu Windows, a następnie na .NET Core 1.0 dla deweloperów eksploracji C# w macOS i Linux.

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* [Obsługa wielu Platform](../../core/index.md):
    - C# za pomocą obsługi .NET Core działa na wielu platformach. Jeśli interesuje Cię w trakcie C# macOS lub jedną z wielu obsługiwane dystrybucje systemu Linux, Dowiedz się więcej na temat platformy .NET Core.

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a>Poprzednie wersje
Poniższe listy kluczy funkcje, które zostały wprowadzone w poprzednich wersjach programu w języku C# i Visual Studio .NET.  
  
 * Visual Studio .NET 2013: 
     - Ta wersja programu Visual Studio zawiera poprawki błędów, wydajności i wersji zapoznawczych platformy technologię platformy kompilatora .NET ("Roslyn"), które stały się zestawu SDK platformy kompilatora .NET<!--Link to ../roslyn/index.md-->.

 * C# 5, programu Visual Studio .NET 2012: 
     - `Async` / `await`, a [informacje o wywołującym](../programming-guide/concepts/caller-information.md) atrybutów.

 * C# 4, programu Visual Studio .NET 2010: 
     - `Dynamic`, [argumentami nazwanymi](../programming-guide/classes-and-structs/named-and-optional-arguments.md), następujące parametry opcjonalne i rodzajowy [Kowariancja i ma przeciwwskazań wariancji](../programming-guide/concepts/covariance-contravariance/index.md).

 * C# 3, programu Visual Studio .NET 2008: 
     - Inicjatory obiektów i kolekcji, wyrażenia lambda, metody rozszerzenia, typy anonimowe, automatyczne właściwości, lokalnego `var` wnioskowanie, i [języka zapytań zintegrowanym (LINQ)](../programming-guide/concepts/linq/index.md).

 * C# 2, Visual Studio .NET 2005: 
     - Metody anonimowe, ogólne, typy dopuszczające wartości zerowe, Iteratory/yield `static` klasy i Kowariancja i ma przeciwwskazań wariancji dla delegatów.

 * C# 1.1, Visual Studio .NET 2003: 
     - `#line` komentarze w dokumencie pragma i xml.

 * C# 1, Visual Studio .NET 2002: 
     - Pierwszą wersję [C#](../csharp.md).   
