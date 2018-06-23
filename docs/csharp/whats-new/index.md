---
title: Nowości w języku C# — przewodnik C#
description: Jak ewoluuje w języku C#
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 399550178a12ff520dff033f0f1dc4a7cdfb9591
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314675"
---
# <a name="whats-new-in-c"></a>Nowości w języku C# #

Ta strona zawiera plan nowych funkcji każdego wydania programu w języku C#. Poniższe linki udostępniają szczegółowe informacje o głównych funkcje dodane w poszczególnych wersjach.

> [!IMPORTANT]
> W języku C# zależy od typów i metod w *biblioteki standardowej* dla niektórych funkcji. Przykładem jest wyjątek podczas przetwarzania. Każdy `throw` instrukcja lub wyrażenie zaznaczono zapewnienie obiekt został zgłoszony jest pochodną <xref:System.Exception>. Podobnie co `catch` jest sprawdzane pod kątem upewnij się, że typ jest przechwycono pochodzi od <xref:System.Exception>. Każda wersja może dodać nowe wymagania. Aby korzystać z najnowszych funkcji języka w środowiskach starsze, może być konieczne zainstalować określone biblioteki. Te zależności są opisane na stronie dla każdej określonej wersji. Użytkownik może dowiedzieć się więcej o [relacje między języka i biblioteki](relationships-between-language-and-library.md) w tle na tę zależność. 

Aby korzystać z najnowszych funkcji w wersji punktu, należy [skonfigurować kompilatora wersji języka](../language-reference/configure-language-version.md) i wybierz wersję.

* [C# 7.3](csharp-7-3.md):
  - Ta strona zawiera opis najnowszych funkcji w języku C#. Jest obecnie dostępna w C# 7.3 [programu Visual Studio 2017 wersji 15.7](https://visualstudio.microsoft.com/vs/whatsnew/), a następnie w [.NET Core-SDK 2.1 2.1.300 RC1](../../core/whats-new/index.md).
* [C# 7.2](csharp-7-2.md):
  - Ta strona opisano funkcje dodane w języku C#. Jest obecnie dostępna w C# 7.2 [programu Visual Studio 2017 wersji 15,5 cala](https://visualstudio.microsoft.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.1](csharp-7-1.md):
  - Ta strona opisano funkcje dodane w języku C# 7.1. Te funkcje zostały dodane w [programu Visual Studio 2017 wersji 15 ustęp 3](https://visualstudio.microsoft.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.0](csharp-7.md):
  - Ta strona opisano funkcje dodane w języku C# w wersji 7.0. Te funkcje zostały dodane w [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) i [.NET Core 1.0](../../core/whats-new/index.md) i nowsze
* [C# 6](csharp-6.md):
  - Ta strona zawiera opis funkcji, które zostały dodane w języku C# 6. Te funkcje są dostępne w programie Visual Studio 2015 dla deweloperów systemu Windows, a następnie na .NET Core 1.0 dla deweloperów eksploracji C# w macOS i Linux.
* [Obsługa wielu Platform](../../core/index.md):
  - C# za pomocą obsługi .NET Core działa na wielu platformach. Jeśli interesuje Cię w trakcie C# macOS lub jedną z wielu obsługiwane dystrybucje systemu Linux, Dowiedz się więcej na temat platformy .NET Core.
* [Zestaw SDK platformy kompilatora .NET](../roslyn-sdk/index.md):
  - Zestawu SDK platformy kompilatora .NET umożliwia pisanie kodu, który przeprowadza analizę statyczną w kodzie języka C#. Te interfejsy API umożliwia odnaleźć potencjalne błędy lub nieprawidłowe wskazówki, sugerować poprawki i nawet zaimplementować te poprawki.

## <a name="previous-versions"></a>Poprzednie wersje

Poniższe listy kluczy funkcje, które zostały wprowadzone w poprzednich wersjach programu w języku C# i Visual Studio .NET.

* Visual Studio .NET 2013:
  - Ta wersja programu Visual Studio zawiera poprawki błędów, wydajności i wersji zapoznawczych platformy technologię platformy kompilatora .NET ("Roslyn"), które stały się [zestawu SDK platformy kompilatora .NET](../roslyn-sdk/index.md).
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
