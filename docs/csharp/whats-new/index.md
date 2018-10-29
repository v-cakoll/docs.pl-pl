---
title: Co nowego C# - C# przewodnik
description: Jak jest C# ewoluują języka
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: b079c21ee90a797b038b96ae68123a538464c382
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201442"
---
# <a name="whats-new-in-c"></a>Co nowego w języku C# #

Ta strona zawiera plan działania o nowe funkcje w każdej wersji głównej programu C# języka. Połączone artykuły zawierają szczegółowe informacji na temat główne funkcje dodane w każdej wersji. Zawiera informacje na temat nowych funkcji, które zostały zwolnione, w głównym wydaniu lub w publicznej wersji zapoznawczej. Szczegóły stanów funkcji języka, w tym funkcje uznane za dla przyszłych wydaniach można znaleźć [w repozytorium dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) w witrynie GitHub.

> [!IMPORTANT]
> C# Języka zależy od typów i metod w *biblioteki standardowej* dla niektórych funkcji. Przykładem jest wyjątek podczas przetwarzania. Każdy `throw` instrukcję lub wyrażenie jest zaznaczone, aby upewnić się, obiekt jest zgłaszana jest tworzony na podstawie <xref:System.Exception>. Podobnie co `catch` jest sprawdzany w celu zapewnienia, że typ wciągnięcia jest tworzony na podstawie <xref:System.Exception>. Każda wersja może dodawać nowych wymagań. Aby korzystać z najnowszych funkcji języków, w środowiskach starsze, może być konieczne zainstalowanie określonych bibliotek. Te zależności są udokumentowane na stronie informacjach dotyczących określonej wersji. Możesz dowiedzieć się więcej [relacje między językiem a biblioteki](relationships-between-language-and-library.md) tła na tę zależność. 

Korzystanie z najnowszych funkcji w wersji punktu należy [skonfigurować wersję językową kompilatora](../language-reference/configure-language-version.md) i wybierz wersję.

* [C#7.3](csharp-7-3.md):
  - Ta strona zawiera opis najnowszych funkcji C# języka. C#7.3 jest obecnie dostępna w [Visual Studio 2017 w wersji 15.7](https://visualstudio.microsoft.com/vs/whatsnew/), a następnie w [zestawu SDK platformy .NET Core 2.1 2.1.300 RC1](../../core/whats-new/index.md).
* [C#7.2](csharp-7-2.md):
  - Ta strona w tym artykule opisano funkcje dodane w C# języka. C#7.2 jest obecnie dostępna w [programu Visual Studio 2017 w wersji 15.5](https://visualstudio.microsoft.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C#7.1](csharp-7-1.md):
  - Ta strona w tym artykule opisano funkcje dodane w C# 7.1. Te funkcje zostały dodane w [programu Visual Studio 2017 w wersji 15.3](https://visualstudio.microsoft.com/vs/whatsnew/), a następnie w [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C#7.0](csharp-7.md):
  - Ta strona w tym artykule opisano funkcje dodane w C# 7.0. Te funkcje zostały dodane w [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) i [platformy .NET Core 1.0](../../core/whats-new/index.md) lub nowszy
* [C#6](csharp-6.md):
  - Ta strona zawiera opis funkcji, które zostały dodane w C# 6. Te funkcje są dostępne w programie Visual Studio 2015 dla deweloperów Windows i platformy .NET Core 1.0 dla deweloperów, eksplorowanie C# w systemach macOS i Linux.
* [Obsługa wielu Platform](../../core/index.md):
  - C#, dzięki obsłudze platformy .NET Core działa na wielu platformach. Jeśli chcesz wypróbować C# w systemie macOS lub na jednym z wielu obsługiwane dystrybucje systemu Linux, więcej informacji na temat platformy .NET Core.
* [Zestaw SDK platformy kompilatora .NET](../roslyn-sdk/index.md):
  - Zestaw SDK platformy kompilatora .NET pozwala napisać kod, który wykonuje analizę statyczną na C# kodu. Te interfejsy API umożliwia znajdowanie potencjalnych błędów lub rozwiązań, sugerowanie poprawki i nawet zaimplementować te poprawki.

## <a name="previous-versions"></a>Poprzednie wersje

Poniższa lista zawiera najważniejsze funkcje, które zostały wprowadzone w poprzednich wersjach C# języka i programu Visual Studio .NET.

* Visual Studio .NET 2013:
  - Ta wersja programu Visual Studio dołączony poprawki błędów, ulepszenia wydajności i technologii z podglądem platformie kompilatora .NET ("Roslyn"), który stał się [zestawu SDK platformy kompilatora .NET](../roslyn-sdk/index.md).
* C#5, visual Studio .NET 2012:
  - `Async` / `await`, a [informacje o wywołującym](../programming-guide/concepts/caller-information.md) atrybutów.
* C#4, visual Studio .NET 2010:
  - `Dynamic`, [argumenty nazwane](../programming-guide/classes-and-structs/named-and-optional-arguments.md), następujące parametry opcjonalne i ogólny [wariancji kowariancji i ma przeciwwskazań](../programming-guide/concepts/covariance-contravariance/index.md).
* C#3, visual Studio .NET 2008:
  - Inicjatory obiektów i kolekcji, wyrażeń lambda, metody rozszerzenia, typy anonimowe, właściwości automatycznych, lokalnego `var` wnioskowanie, typu i [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).
* C#2 programu visual Studio .NET 2005:
  - Metody anonimowe, ogólne, typy dopuszczające wartości null, Iteratory/yield `static` klasy i kowariancji i ma przeciwwskazań wariancji dla delegatów.
* C#1.1, visual Studio .NET 2003:
  - `#line` komentarze dokumentacji pragma i xml.
* C#1 programu visual Studio .NET 2002:
  - Pierwsza wersja [ C# ](../csharp.md).
